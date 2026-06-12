---
title: "gstreamer1.0-libav package install is broken on iMX8(ARM) platform"
date: 2021-07-08
forum: Installation &amp; Upgrades
---

### Post by gilmotta1 on 2021-07-08
gstreamer1.0-libav package install is broken on iMX8(ARM) platform

Weeks ago, I used to be able to install libav on my iMX8 (ARM) platform running Ubuntu 18.04.3 LTS
However today when I tried sudo apt-get install gstreamer1.0- libav
I typed sudo apt-get update before updating libav
I got the following error:


```
$ sudo apt-get install gstreamer1.0- libav
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer req uired:
linux-boundary-17b-headers-4.14.98-12
linux-boundary-17b-headers-4.14.98-8
linux-headers-4.14.98-12-boundary-17b
linux-headers-4.14.98-8-boundary-17b
linux-image-4.14.98-12-boundary-17b
linux-image-4.14.98-8-boundary-17b
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
libavfilter6 libavformat57 libavresample3 libbluray2 libmysofa0
libnorm1 libpgm-5.2-0 libpostproc54 librubberband2 libssh-gcrypt-4
libswscale4 libzmq5
Suggested packages:
libbluray-bdj
Recommended packages:
libaacs0
The following NEW packages will be installed:
gstreamer1.0-libav libavfilter6 libavformat57 libavresample3
libbluray2 libmysofa0 libnorm1 libpgm-5.2-0 libpostproc54
librubberband2 libssh-gcrypt-4 libswscale4 libzmq5
0 upgraded, 13 newly installed, 0 to remove and 37 not upgraded.
Need to get 1,942 kB/2,911 kB of archives.
After this operation, 8,519 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://ports.ubuntu.com/ubuntu-ports bionic-updates/main arm64 libs sh-gcrypt-4 arm64 0.8.0~20170825.94fa1e38-1ubuntu0.2
404 Not Found [IP: 91.189.91.39 80]
Err:2 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libavformat57 arm64 7:3.4.6-0ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
Err:3 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libavresample3 arm64 7:3.4.6-0ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
Err:4 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libmysofa0 arm64 0.6~dfsg0-2ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
Err:5 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libpostproc54 arm64 7:3.4.6-0ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
Err:6 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libswscale4 arm64 7:3.4.6-0ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
Err:7 http://ports.ubuntu.com/ubuntu-ports bionic-updates/universe arm64 libavfilter6 arm64 7:3.4.6-0ubuntu0.18.04.1
404 Not Found [IP: 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libs/li bssh/libssh-gcrypt-4_0.8.0~20170825.94fa1e38-1ubuntu0.2_arm64.deb 404 N ot Found [IP: 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/f/f fmpeg/libavformat57_3.4.6-0ubuntu0.18.04.1_arm64.deb 404 Not Found [IP: 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/f/f fmpeg/libavresample3_3.4.6-0ubuntu0.18.04.1_arm64.deb 404 Not Found [IP : 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/lib m/libmysofa/libmysofa0_0.6~dfsg0-2ubuntu0.18.04.1_arm64.deb 404 Not Fou nd [IP: 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/f/f fmpeg/libpostproc54_3.4.6-0ubuntu0.18.04.1_arm64.deb 404 Not Found [IP: 91.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/f/f fmpeg/libswscale4_3.4.6-0ubuntu0.18.04.1_arm64.deb 404 Not Found [IP: 9 1.189.91.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/f/f fmpeg/libavfilter6_3.4.6-0ubuntu0.18.04.1_arm64.deb 404 Not Found [IP: 91.189.91.39 80]
E: Unable to fetch some archives, maybe run apt-get update or try with -- fix-missing?
```

Can anyone shed some light please?

Thank you!

---

### Post by grahammechanical on 2021-07-08
You could have added this information to your earlier post on this subject.

Those failed to fetch messages are an indication that each of those software repositories cannot be found. Assuming that the internet connection is working, the problem might be caused by those IP. addresses some how becoming incorrect. Or, the particular server you are attempting to download from is off line for some reason. Ubuntu 18.04 (Bionic) is supported until April 2023. So, the OS reaching End of Life and the repositories being moved is not the cause of this problem.

I am not helping much am I? Sorry.

Regards

---

