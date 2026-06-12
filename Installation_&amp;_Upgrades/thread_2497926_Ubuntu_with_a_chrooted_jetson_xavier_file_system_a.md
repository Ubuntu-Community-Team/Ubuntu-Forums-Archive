---
title: "Ubuntu with a chrooted jetson xavier file system and qemu : apt-get in"
date: 2024-05-23
forum: Installation &amp; Upgrades
---

### Post by adamssas on 2024-05-23
Hello,
I am using a chrooted jetson xavier file system with qemu. (Ubuntu 20.04) (qemu-aarch64 4.2.1)
Here is the output with the command when I try to apt-get :




```

sudo apt-get install -y build-essential
Unknown host QEMU_IFLA type: 54
Unknown host QEMU_IFLA type: 56
Unknown host QEMU_IFLA type: 57
Unknown host QEMU_IFLA type: 54
Unknown host QEMU_IFLA type: 56
Unknown host QEMU_IFLA type: 57
Unknown host QEMU_IFLA type: 54
Unknown host QEMU_IFLA type: 32820
Unknown host QEMU_IFLA type: 56
Unknown host QEMU_IFLA type: 57
Unknown host QEMU_IFLA type: 54
Unknown host QEMU_IFLA type: 32820
Unknown host QEMU_IFLA type: 56
Unknown host QEMU_IFLA type: 57
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb bogl-bterm busybox-static cryptsetup-bin dctrl-tools dpkg-repack gir1.2-timezonemap-1.0 gir1.2-xkl-1.0
  grub-common libdebian-installer4 libtimezonemap-data libtimezonemap1 ncurses-term openssh-sftp-server os-prober python3-icu python3-pam
  rdate tasksel tasksel-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dpkg-dev fakeroot g++ g++-9 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++-9-dev
Suggested packages:
  debian-keyring gcc-9-doc libstdc++-9-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-9 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++-9-dev
0 upgraded, 9 newly installed, 0 to remove and 5 not upgraded.
Need to get 9347 kB of archives.
After this operation, 42,1 MB of additional disk space will be used.
Get:1 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libstdc++-9-dev arm64 9.4.0-1ubuntu1~20.04.2 [1687 kB]
Get:2 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 g++-9 arm64 9.4.0-1ubuntu1~20.04.2 [6843 kB]
Get:3 http://ports.ubuntu.com/ubuntu-ports focal/main arm64 g++ arm64 4:9.3.0-1ubuntu2 [1592 B]
Get:4 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 dpkg-dev all 1.19.7ubuntu3.2 [679 kB]
Get:5 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 build-essential arm64 12.8ubuntu1.1 [4664 B]
Get:6 http://ports.ubuntu.com/ubuntu-ports focal/main arm64 fakeroot arm64 1.24-1 [61,9 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports focal/main arm64 libalgorithm-diff-perl all 1.19.03-2 [46,6 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports focal/main arm64 libalgorithm-diff-xs-perl arm64 0.04-6 [11,1 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports focal/main arm64 libalgorithm-merge-perl all 0.08-3 [12,0 kB]
Fetched 9347 kB in 9s (1029 kB/s)

```


I am stuck after this message, the command is still running I can see it in top from the host system (outside chroot).




Does anyone face the same issue or know how to solve it ?


Thanks




I also fixed the broken packages but none were.


I can ping :


```

ping -c 2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=112 time=73.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=112 time=70.4 ms


--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 70.351/71.656/72.962/1.305 ms

```

---

