# Yocto-core-image-image-minimal
this is a practical guide for beginner to describe them how could they customized first image on yocto project using poky refrence distro

<div>
<img align="left" src="https://github.com/waleedelfieky/yocto-vsomeip-project/assets/126036494/158df6f5-4402-406b-bfde-e41f1efe758c" alt="STL Notes Logo" width="350">

# *Yocto Simple PROJECT: A Summary Guide for beignners for generating core-image-minimal*

[![GitHub stars](https://img.shields.io/github/stars/waleedelfieky/Yocto-core-image-image-minimal?style=social)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/stargazers) 
[![GitHub forks](https://img.shields.io/github/forks/waleedelfieky/Yocto-core-image-image-minimal?style=social)](https://github.com/waleedelfieky/yocto-Yocto-core-image-image-minimal/network/members) 
[![GitHub watchers](https://img.shields.io/github/watchers/waleedelfieky/Yocto-core-image-image-minimal?style=social)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/watchers)

[![GitHub repo size](https://img.shields.io/github/repo-size/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal) 
[![License](https://img.shields.io/github/license/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/blob/main/LICENSE) 

![GitHub search hit counter](https://img.shields.io/github/search/waleedelfieky/Yocto-core-image-image-minimal/goto?style=flat-square)
[![Contributors](https://img.shields.io/github/contributors/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/graphs/contributors)

[![GitHub commit activity](https://img.shields.io/github/commit-activity/m/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/commits/main) 
[![Last commit](https://img.shields.io/github/last-commit/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/commits/main) 

[![GitHub pull requests](https://img.shields.io/github/issues-pr/waleedelfieky/Yocto-core-image-image-minimal)](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/pulls)
![GitHub merged PRs](https://img.shields.io/github/issues-pr-closed/waleedelfieky/Yocto-core-image-image-minimal?style=flat-square)
</div>


## A collection of markdown notes on Yocto simple project for beginners

yocto project: it enables developers to create custom Linux-based systems for embedded devices. It offers tools for building Linux distributions.
  
## Table of Contents:

- [overview-of-system](#overview-of-system)
- [prepare-host](#prepare-host)
- [choose-poky-branch ](#choose-poky-branch)
- [download-poky](#download-poky)
- [source-the-varibales-and-utilites-needed](#source-the-varibales-and-utilites-needed)
- [choose-machine](#choose-machine)
- [choose-image-recipe](#choose-image-recipe)
- [build-image](#build-image)
- [Test-on-qemu](#Test-on-qemu)
- [Contact Information](#contact-information)

## overview-of-system:

![first-image](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/f0421e8e-2b76-4110-8df6-0d543829231a)


## prepare-host:
- At least 90 Gbytes of free disk space, though much more will help to run multiple builds and increase performance by reusing build artifacts.
- At least 8 Gbytes of RAM, though a modern modern build host with as much RAM and as many CPU cores as possible is strongly recommended to maximize build performance.
- Runs a supported Linux distribution (i.e. recent releases of Fedora, openSUSE, CentOS, Debian, or Ubuntu). For a list of Linux distributions that support the Yocto Project, see the [Supported Linux Distributions](https://docs.yoctoproject.org/ref-manual/system-requirements.html#supported-linux-distributions) section in the Yocto Project Reference Manual. For detailed information on preparing your build host, see the [Preparing the Build Host](https://docs.yoctoproject.org/dev-manual/start.html#preparing-the-build-host) section in the Yocto Project Development Tasks Manual.
	- Git 1.8.3.1 or greater
	- tar 1.28 or greater
	- Python 3.8.0 or greater.
	- gcc 8.0 or greater.
	- GNU make 4.0 or greater
### Build Host Packages
```
$ sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev python3-subunit mesa-common-dev zstd liblz4-tool file locales libacl1

$ sudo locale-gen en_US.UTF-8
```
![Pasted image 20231223014636](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/200079e7-4dfc-4a27-8e85-bcbe0da8a6f3)
![Pasted image 20231223014706](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/be18e753-2e74-49f7-8040-6eb7ff053cda)


## choose-poky-branch:
- we would work by mickeldore branch
![Pasted image 20231223014724](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/ef9157a0-3fe1-444e-b836-bc4895b1e7f4)

## download-poky:
```
$ git clone -b mickeldore https://github.com/yoctoproject/poky
```
![Pasted image 20231223014846](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/d8eb5a59-d0cc-49a5-af9a-cf2a171cfd77)

## source-the-varibales-and-utilites-needed:
inside poky directory run
```
$ source oe-init-build-env
```
## choose-machine:
how to choose it ?
- inside build/conf/local.conf
	- you would find machine varibale change it to any of supported images 
	- we would choose qemux86-64
![Pasted image 20231223015608](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/7f625bb2-3363-46c1-9f59-d38f59b2f494)

 
## choose-image-recipe:

- there is a ready to use image inside meta layer in directories called *images
- we would use core-minimal-image 

## build-image:
in poky/build directory run
```
$ bitbake core-image-minimal
```
## Test-on-qemu:
on build directory run
```
$ runqemu
```
![Pasted image 20231223015908](https://github.com/waleedelfieky/Yocto-core-image-image-minimal/assets/126036494/4c13d6c7-1075-44b6-9be0-df82a5aa9231)


## Contact Information:

If you have any questions, suggestions, or feedback regarding these this project, please feel free to contact me at waleedelfieky@gmail.com


