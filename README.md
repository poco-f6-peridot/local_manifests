## 1. xiaomi-peridot (poco f6) specific forks ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### 1.1 Installing dependencies and Repo ###

Several packages are needed in order to build
```
sudo apt install -y -qq git-core gnupg flex bc bison build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 x11proto-core-dev libx11-dev jq lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig imagemagick python3 python3-pip python3-dev python-is-python3 schedtool ccache lzop tmux libssl-dev neofetch patchelf dos2unix git-lfs default-jdk libxml-simple-perl ripgrep rclone
```

Install Repo tool

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/.bin
$ PATH=~/.bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

# Make Repo executable
$ chmod a+x ~/.bin/repo
```
### 1.2 Initializing Repo ###

```bash
# Create a directory for the source files
# You can name this directory however you want, just remember to replace
# WORKSPACE with your directory for the rest of this guide.
# This can be located anywhere (as long as the fs is case-sensitive)
$ mkdir WORKSPACE
$ cd WORKSPACE

# Install Repo in the created directory

```
```bash
repo init -u https://github.com/poco-f6-peridot/local_manifests.git -b peridot-15 --git-lfs

```
or,
```bash

git clone https://github.com/poco-f6-peridot/local_manifests -b peridot-15 .repo/local_manifests

```

### 1.3 Downloading the source tree ###

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
#
# The -j# option specifies the number of concurrent download threads to run.
# 8 threads is a good number for most internet connections.
# You may need to adjust this value if you have a particularly slow connection.
$ repo sync --no-tags --no-clone-bundle --current-branch -j8
```
### 1.4 Downloading other hals ###

vendor_qcom_opensource_power

```bash
rm -rf vendor/qcom/opensource/power/ && git clone https://github.com/poco-f6-peridot/vendor_qcom_opensource_power vendor/qcom/opensource/power/
```
hardware_qcom-caf_common
```bash
rm -rf hardware/qcom-caf/common/ && git clone https://github.com/peridot-dev/android_hardware_qcom-caf_common.git hardware/qcom-caf/common/
```
vendor_qcom_opensource_vibrator
```bash
rm -rf hardware/qcom-caf/common/ && git clone https://github.com/peridot-dev/android_hardware_qcom-caf_common.git hardware/qcom-caf/common/
```
