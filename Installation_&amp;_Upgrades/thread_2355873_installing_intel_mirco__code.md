---
title: "installing intel mirco  code"
date: 2017-03-17
forum: Installation &amp; Upgrades
---

### Post by rev-matthewagilmore on 2017-03-17
i installed it using the  repo but got  a missing firmware

```
matt@matt-Inspiron-11-3168:~$ sudo apt-get install microcode.ctl intel-microcodeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  iucode-tool
The following NEW packages will be installed:
  intel-microcode iucode-tool microcode.ctl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 503 kB of archives.
After this operation, 699 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 iucode-tool amd64 1.5.1-1ubuntu0.1 [33.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/restricted amd64 intel-microcode amd64 3.20151106.1 [464 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 microcode.ctl amd64 1.18~0+nmu2 [4,840 B]
Fetched 503 kB in 0s (782 kB/s)     
Selecting previously unselected package iucode-tool.
(Reading database ... 207708 files and directories currently installed.)
Preparing to unpack .../iucode-tool_1.5.1-1ubuntu0.1_amd64.deb ...
Unpacking iucode-tool (1.5.1-1ubuntu0.1) ...
Selecting previously unselected package intel-microcode.
Preparing to unpack .../intel-microcode_3.20151106.1_amd64.deb ...
Unpacking intel-microcode (3.20151106.1) ...
Selecting previously unselected package microcode.ctl.
Preparing to unpack .../microcode.ctl_1.18~0+nmu2_amd64.deb ...
Unpacking microcode.ctl (1.18~0+nmu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up iucode-tool (1.5.1-1ubuntu0.1) ...
Setting up intel-microcode (3.20151106.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up microcode.ctl (1.18~0+nmu2) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-41-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
matt@matt-Inspiron-11-3168:~$ dmesg | grep microcode
[    1.945294] microcode: sig=0x406c4, pf=0x1, revision=0x40a
[    1.945590] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

```

---

### Post by Doug S on 2017-03-18
You only need to worry about Kaby Lake missing firmware warnings if you actually have a Kaby Lake processor.
Otherwise, see [here]("http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs/811487#811487") for where to get the firmware.

---

