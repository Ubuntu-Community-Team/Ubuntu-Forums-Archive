---
title: "Version conflict ? linux-libc-dev and kernel version?"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2016-03-22
Hi, all:


I'm actually trying to compile openssl from scratch, but we met an issue (please refer to [https://github.com/openssl/openssl/issues/890]("https://github.com/openssl/openssl/issues/890") )

```

jiapei@jiapei-GT72-6QE:~/Downloads/networks/openssl$ uname -r
4.2.0-34-generic
jiapei@jiapei-GT72-6QE:~/Downloads/networks/openssl$ cat /usr/include/linux/version.h
#define LINUX_VERSION_CODE 199947
#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))

```

```

jiapei@jiapei-GT72-6QE:~/Downloads/networks/openssl$ apt-cache showpkg linux-headers
Package: linux-headers
Versions: 

Reverse Depends: 
  systemtap,linux-headers
  iscsitarget-dkms,linux-headers
  fwts-efi-runtime-dkms,linux-headers
  linux-headers-generic-lts-quantal,linux-headers
  sl-modem-dkms,linux-headers
  xtables-addons-dkms,linux-headers
  volatility-tools,linux-headers
  systemtap,linux-headers
  openswan-modules-source,linux-headers
  iscsitarget-dkms,linux-headers
  fwts-efi-runtime-dkms,linux-headers
  alsa-source,linux-headers
  linux-headers-generic-lts-quantal,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-4.4.0-13-lowlatency 4.4.0-13.29~14.04.1
linux-headers-4.4.0-13-generic 4.4.0-13.29~14.04.1
linux-headers-4.2.0-34-lowlatency 4.2.0-34.39~14.04.1
linux-headers-4.2.0-34-generic 4.2.0-34.39~14.04.1
linux-headers-4.2.0-30-lowlatency 4.2.0-30.36~14.04.1
linux-headers-4.2.0-30-generic 4.2.0-30.36~14.04.1
linux-headers-4.2.0-27-lowlatency 4.2.0-27.32~14.04.1
linux-headers-4.2.0-27-generic 4.2.0-27.32~14.04.1
linux-headers-4.2.0-25-lowlatency 4.2.0-25.30~14.04.1
linux-headers-4.2.0-25-generic 4.2.0-25.30~14.04.1
linux-headers-4.2.0-23-lowlatency 4.2.0-23.28~14.04.1
linux-headers-4.2.0-23-generic 4.2.0-23.28~14.04.1
linux-headers-4.2.0-22-lowlatency 4.2.0-22.27~14.04.1
linux-headers-4.2.0-22-generic 4.2.0-22.27~14.04.1
linux-headers-4.2.0-21-lowlatency 4.2.0-21.25~14.04.1
linux-headers-4.2.0-21-generic 4.2.0-21.25~14.04.1
linux-headers-4.2.0-19-lowlatency 4.2.0-19.23~14.04.1
linux-headers-4.2.0-19-generic 4.2.0-19.23~14.04.1
linux-headers-4.2.0-18-lowlatency 4.2.0-18.22~14.04.1
linux-headers-4.2.0-18-generic 4.2.0-18.22~14.04.1
linux-headers-3.19.0-56-lowlatency 3.19.0-56.62~14.04.1
linux-headers-3.19.0-56-generic 3.19.0-56.62~14.04.1
linux-headers-3.19.0-51-lowlatency 3.19.0-51.58~14.04.1
linux-headers-3.19.0-51-generic 3.19.0-51.58~14.04.1
linux-headers-3.19.0-49-lowlatency 3.19.0-49.55~14.04.1
linux-headers-3.19.0-49-generic 3.19.0-49.55~14.04.1
linux-headers-3.19.0-47-lowlatency 3.19.0-47.53~14.04.1
linux-headers-3.19.0-47-generic 3.19.0-47.53~14.04.1
linux-headers-3.19.0-43-lowlatency 3.19.0-43.49~14.04.1
linux-headers-3.19.0-43-generic 3.19.0-43.49~14.04.1
linux-headers-3.19.0-42-lowlatency 3.19.0-42.48~14.04.1
linux-headers-3.19.0-42-generic 3.19.0-42.48~14.04.1
linux-headers-3.19.0-41-lowlatency 3.19.0-41.46~14.04.2
linux-headers-3.19.0-41-generic 3.19.0-41.46~14.04.2
linux-headers-3.19.0-39-lowlatency 3.19.0-39.44~14.04.1
linux-headers-3.19.0-39-generic 3.19.0-39.44~14.04.1
linux-headers-3.19.0-37-lowlatency 3.19.0-37.42~14.04.1
linux-headers-3.19.0-37-generic 3.19.0-37.42~14.04.1
linux-headers-3.19.0-33-lowlatency 3.19.0-33.38~14.04.1
linux-headers-3.19.0-33-generic 3.19.0-33.38~14.04.1
linux-headers-3.19.0-32-lowlatency 3.19.0-32.37~14.04.1
linux-headers-3.19.0-32-generic 3.19.0-32.37~14.04.1
linux-headers-3.19.0-31-lowlatency 3.19.0-31.36~14.04.1
linux-headers-3.19.0-31-generic 3.19.0-31.36~14.04.1
linux-headers-3.19.0-30-lowlatency 3.19.0-30.34~14.04.1
linux-headers-3.19.0-30-generic 3.19.0-30.34~14.04.1
linux-headers-3.19.0-28-lowlatency 3.19.0-28.30~14.04.1
linux-headers-3.19.0-28-generic 3.19.0-28.30~14.04.1
linux-headers-3.19.0-26-lowlatency 3.19.0-26.28~14.04.1
linux-headers-3.19.0-26-generic 3.19.0-26.28~14.04.1
linux-headers-3.19.0-25-lowlatency 3.19.0-25.26~14.04.1
linux-headers-3.19.0-25-generic 3.19.0-25.26~14.04.1
linux-headers-3.19.0-23-lowlatency 3.19.0-23.24~14.04.1
linux-headers-3.19.0-23-generic 3.19.0-23.24~14.04.1
linux-headers-3.19.0-22-lowlatency 3.19.0-22.22~14.04.1
linux-headers-3.19.0-22-generic 3.19.0-22.22~14.04.1
linux-headers-3.19.0-21-lowlatency 3.19.0-21.21~14.04.1
linux-headers-3.19.0-21-generic 3.19.0-21.21~14.04.1
linux-headers-3.19.0-20-lowlatency 3.19.0-20.20~14.04.1
linux-headers-3.19.0-20-generic 3.19.0-20.20~14.04.1
linux-headers-3.19.0-18-lowlatency 3.19.0-18.18~14.04.1
linux-headers-3.19.0-18-generic 3.19.0-18.18~14.04.1
linux-headers-3.16.0-67-lowlatency 3.16.0-67.87~14.04.1
linux-headers-3.16.0-67-generic 3.16.0-67.87~14.04.1
linux-headers-3.16.0-62-lowlatency 3.16.0-62.83~14.04.1
linux-headers-3.16.0-62-generic 3.16.0-62.83~14.04.1
linux-headers-3.16.0-60-lowlatency 3.16.0-60.80~14.04.1
linux-headers-3.16.0-60-generic 3.16.0-60.80~14.04.1
linux-headers-3.16.0-59-lowlatency 3.16.0-59.79~14.04.1
linux-headers-3.16.0-59-generic 3.16.0-59.79~14.04.1
linux-headers-3.16.0-57-lowlatency 3.16.0-57.77~14.04.1
linux-headers-3.16.0-57-generic 3.16.0-57.77~14.04.1
linux-headers-3.16.0-56-lowlatency 3.16.0-56.75~14.04.1
linux-headers-3.16.0-56-generic 3.16.0-56.75~14.04.1
linux-headers-3.16.0-55-lowlatency 3.16.0-55.74~14.04.1
linux-headers-3.16.0-55-generic 3.16.0-55.74~14.04.1
linux-headers-3.16.0-53-lowlatency 3.16.0-53.72~14.04.1
linux-headers-3.16.0-53-generic 3.16.0-53.72~14.04.1
linux-headers-3.16.0-52-lowlatency 3.16.0-52.71~14.04.1
linux-headers-3.16.0-52-generic 3.16.0-52.71~14.04.1
linux-headers-3.16.0-51-lowlatency 3.16.0-51.69~14.04.1
linux-headers-3.16.0-51-generic 3.16.0-51.69~14.04.1
linux-headers-3.16.0-50-lowlatency 3.16.0-50.67~14.04.1
linux-headers-3.16.0-50-generic 3.16.0-50.67~14.04.1
linux-headers-3.16.0-49-lowlatency 3.16.0-49.65~14.04.1
linux-headers-3.16.0-49-generic 3.16.0-49.65~14.04.1
linux-headers-3.16.0-48-lowlatency 3.16.0-48.64~14.04.1
linux-headers-3.16.0-48-generic 3.16.0-48.64~14.04.1
linux-headers-3.16.0-46-lowlatency 3.16.0-46.62~14.04.1
linux-headers-3.16.0-46-generic 3.16.0-46.62~14.04.1
linux-headers-3.16.0-45-lowlatency 3.16.0-45.60~14.04.1
linux-headers-3.16.0-45-generic 3.16.0-45.60~14.04.1
linux-headers-3.16.0-44-lowlatency 3.16.0-44.59~14.04.1
linux-headers-3.16.0-44-generic 3.16.0-44.59~14.04.1
linux-headers-3.16.0-43-lowlatency 3.16.0-43.58~14.04.1
linux-headers-3.16.0-43-generic 3.16.0-43.58~14.04.1
linux-headers-3.16.0-41-lowlatency 3.16.0-41.57~14.04.1
linux-headers-3.16.0-41-generic 3.16.0-41.57~14.04.1
linux-headers-3.16.0-40-lowlatency 3.16.0-40.54~14.04.1
linux-headers-3.16.0-40-generic 3.16.0-40.54~14.04.1
linux-headers-3.16.0-39-lowlatency 3.16.0-39.53~14.04.1
linux-headers-3.16.0-39-generic 3.16.0-39.53~14.04.1
linux-headers-3.16.0-38-lowlatency 3.16.0-38.52~14.04.1
linux-headers-3.16.0-38-generic 3.16.0-38.52~14.04.1
linux-headers-3.16.0-37-lowlatency 3.16.0-37.51~14.04.1
linux-headers-3.16.0-37-generic 3.16.0-37.51~14.04.1
linux-headers-3.16.0-36-lowlatency 3.16.0-36.48~14.04.1
linux-headers-3.16.0-36-generic 3.16.0-36.48~14.04.1
linux-headers-3.16.0-34-lowlatency 3.16.0-34.47~14.04.1
linux-headers-3.16.0-34-generic 3.16.0-34.47~14.04.1
linux-headers-3.16.0-33-lowlatency 3.16.0-33.44~14.04.1
linux-headers-3.16.0-33-generic 3.16.0-33.44~14.04.1
linux-headers-3.16.0-31-lowlatency 3.16.0-31.43~14.04.1
linux-headers-3.16.0-31-generic 3.16.0-31.43~14.04.1
linux-headers-3.16.0-30-lowlatency 3.16.0-30.40~14.04.1
linux-headers-3.16.0-30-generic 3.16.0-30.40~14.04.1
linux-headers-3.16.0-29-lowlatency 3.16.0-29.39~14.04.1
linux-headers-3.16.0-29-generic 3.16.0-29.39~14.04.1
linux-headers-3.16.0-28-lowlatency 3.16.0-28.38~14.04.1
linux-headers-3.16.0-28-generic 3.16.0-28.38~14.04.1
linux-headers-3.16.0-26-lowlatency 3.16.0-26.35~14.04.1
linux-headers-3.16.0-26-generic 3.16.0-26.35~14.04.1
linux-headers-3.16.0-25-lowlatency 3.16.0-25.33~14.04.2
linux-headers-3.16.0-25-generic 3.16.0-25.33~14.04.2
linux-headers-3.13.0-83-lowlatency 3.13.0-83.127
linux-headers-3.13.0-83-generic 3.13.0-83.127
linux-headers-3.13.0-79-lowlatency 3.13.0-79.123
linux-headers-3.13.0-79-generic 3.13.0-79.123
linux-headers-3.13.0-77-lowlatency 3.13.0-77.121
linux-headers-3.13.0-77-generic 3.13.0-77.121
linux-headers-3.13.0-76-lowlatency 3.13.0-76.120
linux-headers-3.13.0-76-generic 3.13.0-76.120
linux-headers-3.13.0-74-lowlatency 3.13.0-74.118
linux-headers-3.13.0-74-generic 3.13.0-74.118
linux-headers-3.13.0-73-lowlatency 3.13.0-73.116
linux-headers-3.13.0-73-generic 3.13.0-73.116
linux-headers-3.13.0-71-lowlatency 3.13.0-71.114
linux-headers-3.13.0-71-generic 3.13.0-71.114
linux-headers-3.13.0-70-lowlatency 3.13.0-70.113
linux-headers-3.13.0-70-generic 3.13.0-70.113
linux-headers-3.13.0-68-lowlatency 3.13.0-68.111
linux-headers-3.13.0-68-generic 3.13.0-68.111
linux-headers-3.13.0-67-lowlatency 3.13.0-67.110
linux-headers-3.13.0-67-generic 3.13.0-67.110
linux-headers-3.13.0-66-lowlatency 3.13.0-66.108
linux-headers-3.13.0-66-generic 3.13.0-66.108
linux-headers-3.13.0-65-lowlatency 3.13.0-65.106
linux-headers-3.13.0-65-generic 3.13.0-65.106
linux-headers-3.13.0-63-lowlatency 3.13.0-63.103
linux-headers-3.13.0-63-generic 3.13.0-63.103
linux-headers-3.13.0-62-lowlatency 3.13.0-62.102
linux-headers-3.13.0-62-generic 3.13.0-62.102
linux-headers-3.13.0-61-lowlatency 3.13.0-61.100
linux-headers-3.13.0-61-generic 3.13.0-61.100
linux-headers-3.13.0-59-lowlatency 3.13.0-59.98
linux-headers-3.13.0-59-generic 3.13.0-59.98
linux-headers-3.13.0-58-lowlatency 3.13.0-58.97
linux-headers-3.13.0-58-generic 3.13.0-58.97
linux-headers-3.13.0-57-lowlatency 3.13.0-57.95
linux-headers-3.13.0-57-generic 3.13.0-57.95
linux-headers-3.13.0-55-lowlatency 3.13.0-55.94
linux-headers-3.13.0-55-generic 3.13.0-55.94
linux-headers-3.13.0-54-lowlatency 3.13.0-54.91
linux-headers-3.13.0-54-generic 3.13.0-54.91
linux-headers-3.13.0-53-lowlatency 3.13.0-53.89
linux-headers-3.13.0-53-generic 3.13.0-53.89
linux-headers-3.13.0-52-lowlatency 3.13.0-52.86
linux-headers-3.13.0-52-generic 3.13.0-52.86
linux-headers-3.13.0-51-lowlatency 3.13.0-51.84
linux-headers-3.13.0-51-generic 3.13.0-51.84
linux-headers-3.13.0-49-lowlatency 3.13.0-49.83
linux-headers-3.13.0-49-generic 3.13.0-49.83
linux-headers-3.13.0-48-lowlatency 3.13.0-48.80
linux-headers-3.13.0-48-generic 3.13.0-48.80
linux-headers-3.13.0-46-lowlatency 3.13.0-46.79
linux-headers-3.13.0-46-generic 3.13.0-46.79
linux-headers-3.13.0-45-lowlatency 3.13.0-45.74
linux-headers-3.13.0-45-generic 3.13.0-45.74
linux-headers-3.13.0-44-lowlatency 3.13.0-44.73
linux-headers-3.13.0-44-generic 3.13.0-44.73
linux-headers-3.13.0-43-lowlatency 3.13.0-43.72
linux-headers-3.13.0-43-generic 3.13.0-43.72
linux-headers-3.13.0-41-lowlatency 3.13.0-41.70
linux-headers-3.13.0-41-generic 3.13.0-41.70
linux-headers-3.13.0-40-lowlatency 3.13.0-40.69
linux-headers-3.13.0-40-generic 3.13.0-40.69
linux-headers-3.13.0-39-lowlatency 3.13.0-39.66
linux-headers-3.13.0-39-generic 3.13.0-39.66
linux-headers-3.13.0-37-lowlatency 3.13.0-37.64
linux-headers-3.13.0-37-generic 3.13.0-37.64
linux-headers-3.13.0-36-lowlatency 3.13.0-36.63
linux-headers-3.13.0-36-generic 3.13.0-36.63
linux-headers-3.13.0-35-lowlatency 3.13.0-35.62
linux-headers-3.13.0-35-generic 3.13.0-35.62
linux-headers-3.13.0-34-lowlatency 3.13.0-34.60
linux-headers-3.13.0-34-generic 3.13.0-34.60
linux-headers-3.13.0-33-lowlatency 3.13.0-33.58
linux-headers-3.13.0-33-generic 3.13.0-33.58
linux-headers-3.13.0-32-lowlatency 3.13.0-32.57
linux-headers-3.13.0-32-generic 3.13.0-32.57
linux-headers-3.13.0-30-lowlatency 3.13.0-30.55
linux-headers-3.13.0-30-generic 3.13.0-30.55
linux-headers-3.13.0-29-lowlatency 3.13.0-29.53
linux-headers-3.13.0-29-generic 3.13.0-29.53
linux-headers-3.13.0-27-lowlatency 3.13.0-27.50
linux-headers-3.13.0-27-generic 3.13.0-27.50
linux-headers-3.13.0-24-lowlatency 3.13.0-24.47
linux-headers-3.13.0-24-generic 3.13.0-24.47
linux-headers-3.13.0-24-lowlatency 3.13.0-24.46
linux-headers-3.13.0-24-generic 3.13.0-24.46

```


```

jiapei@jiapei-GT72-6QE:~/Downloads/networks/openssl$ apt-cache showpkg linux-libc-dev
Package: linux-libc-dev
Versions: 
3.13.0-83.127 (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: d5d143e6dffc891f04a85464446f9451
 Description Language: en
                 File: /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: d5d143e6dffc891f04a85464446f9451

3.13.0-24.46 (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: d5d143e6dffc891f04a85464446f9451
 Description Language: en
                 File: /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: d5d143e6dffc891f04a85464446f9451


Reverse Depends: 
  libdrm-dev:i386,linux-libc-dev 2.6.32-10
  libdrm-dev,linux-libc-dev 2.6.32-10
  linux-libc-dev:i386,linux-libc-dev 3.13.0-83.127
  linux-libc-dev:i386,linux-libc-dev 3.13.0-83.127
  libdrm-dev:i386,linux-libc-dev 2.6.32-10
  blktap-dkms,linux-libc-dev
  nvidia-352-updates,linux-libc-dev
  nvidia-352,linux-libc-dev
  nvidia-340-updates,linux-libc-dev
  nvidia-340,linux-libc-dev
  nvidia-304-updates,linux-libc-dev
  nvidia-304,linux-libc-dev
  fglrx-updates-core,linux-libc-dev
  fglrx-core,linux-libc-dev
  bcmwl-kernel-source,linux-libc-dev
  libdrm-dev,linux-libc-dev 2.6.32-10
  libc6-dev,linux-libc-dev
  linux-libc-dev:i386,linux-libc-dev 3.13.0-24.46
  linux-libc-dev:i386,linux-libc-dev 3.13.0-24.46
  libdrm-dev:i386,linux-libc-dev 2.6.32-10
  iptables-dev:i386,linux-libc-dev 3.5
  vdr-dev,linux-libc-dev 3.0
  librsbac-dev,linux-libc-dev
  blktap-dkms,linux-libc-dev
  nvidia-331-updates,linux-libc-dev
  nvidia-331,linux-libc-dev
  nvidia-304-updates,linux-libc-dev
  nvidia-304,linux-libc-dev
  nvidia-173,linux-libc-dev
  fglrx-updates,linux-libc-dev
  fglrx,linux-libc-dev
  bcmwl-kernel-source,linux-libc-dev
  libklibc-dev,linux-libc-dev
  libdrm-dev,linux-libc-dev 2.6.32-10
  libc6-dev,linux-libc-dev
  iptables-dev,linux-libc-dev 3.5
  gcc-multilib,linux-libc-dev 2.6.38-8.42
  gcc-multilib,linux-libc-dev 3.0.0-2
Dependencies: 
3.13.0-83.127 - amd64-libs-dev (1 1.1) amd64-libs-dev:i386 (1 1.1) dvb-dev (3 1.0.1-6) dvb-dev:i386 (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6-dev:i386 (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libc6.1-dev:i386 (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) linux-kernel-headers:i386 (0 (null)) dvb-dev (3 1.0.1-6) dvb-dev:i386 (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6-dev:i386 (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libc6.1-dev:i386 (3 2.3.2.ds1-6) libdrm-dev (0 (null)) libdrm-dev:i386 (0 (null)) linux-kernel-headers (0 (null)) linux-kernel-headers:i386 (0 (null)) linux-libc-dev:i386 (3 3.13.0-83.127) linux-libc-dev:i386 (6 3.13.0-83.127) 
3.13.0-24.46 - amd64-libs-dev (1 1.1) amd64-libs-dev:i386 (1 1.1) dvb-dev (3 1.0.1-6) dvb-dev:i386 (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6-dev:i386 (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libc6.1-dev:i386 (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) linux-kernel-headers:i386 (0 (null)) dvb-dev (3 1.0.1-6) dvb-dev:i386 (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6-dev:i386 (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libc6.1-dev:i386 (3 2.3.2.ds1-6) libdrm-dev (0 (null)) libdrm-dev:i386 (0 (null)) linux-kernel-headers (0 (null)) linux-kernel-headers:i386 (0 (null)) linux-libc-dev:i386 (3 3.13.0-24.46) linux-libc-dev:i386 (6 3.13.0-24.46) 
Provides: 
3.13.0-83.127 - linux-kernel-headers 
3.13.0-24.46 - linux-kernel-headers 
Reverse Provides: 

```


The above bash commands seem to tell 
1. I'm using a kernel **4.2.0-34-generic**
2. The newest linux-headers seems to be of a newer version **linux-headers-4.4.0-13-generic 4.4.0-13.29~14.04.1**
3. And linux-libc-dev seems to be based two older versions **3.13.0-83.127 and 3.13.0-24.46**

And, this seems to cause "code skipping by the Kernel Headers checking". 
warning: #warning "AFALG ENGINE requires Kernel Headers >= 4.1.0" [-Wcpp]
 # warning "AFALG ENGINE requires Kernel Headers >= 4.1.0"


In my point of view, whenever I update and upgrade my Ubuntu, the **Linux kernel**, as well as **Linux Headers**, and **linux-libc** should be all in consistency with each other ?
Any suggestions please?


Cheers
Pei

---

