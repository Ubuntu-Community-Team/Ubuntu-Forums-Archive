---
title: "apt upgrade stuck during install (not during download)"
date: 2018-08-28
forum: Installation &amp; Upgrades
---

### Post by boonedoggle2 on 2018-08-28
I'm actually shocked I have never seen this before, but I'm wondering what the procedure should be to get it fixed. There were some pretty critical packages in this upgrade, so I'm a little concerned. After performing an upgrade, the install hung. I was unable to kill the process with ctrl-c, but the system functions. I'm just wondering what I can do at this point to minimize damage.

The system hung during the install at 97% while it was performing the following: ```
update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic
```

Here are the packages that were to be installed:

```

$ apt list --upgradable Listing... Done
fwupd/xenial-updates 0.8.3-0ubuntu4 amd64 [upgradable from: 0.8.3-0ubuntu3]
intel-microcode/xenial-updates,xenial-security 3.20180807a.0ubuntu0.16.04.1 amd64 [upgradable from: 3.20180425.1~ubuntu0.16.04.2]
libappstream-glib8/xenial-updates 0.5.13-1ubuntu6 amd64 [upgradable from: 0.5.13-1ubuntu5]
libdfu1/xenial-updates 0.8.3-0ubuntu4 amd64 [upgradable from: 0.8.3-0ubuntu3]
libfwupd1/xenial-updates 0.8.3-0ubuntu4 amd64 [upgradable from: 0.8.3-0ubuntu3]
libgd3/xenial-updates,xenial-security 2.1.1-4ubuntu0.16.04.10 amd64 [upgradable from: 2.1.1-4ubuntu0.16.04.8]

```

And here is what happened:
```

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  fwupd intel-microcode libappstream-glib8 libdfu1 libfwupd1 libgd3 libgd3:i386
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,832 kB of archives.
After this operation, 65.5 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libappstream-glib8 amd64 0.5.13-1ubuntu6 [101 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdfu1 amd64 0.8.3-0ubuntu4 [48.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfwupd1 amd64 0.8.3-0ubuntu4 [32.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 fwupd amd64 0.8.3-0ubuntu4 [120 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libgd3 i386 2.1.1-4ubuntu0.16.04.10 [129 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgd3 amd64 2.1.1-4ubuntu0.16.04.10 [126 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 intel-microcode amd64 3.20180807a.0ubuntu0.16.04.1 [1,275 kB]
Fetched 1,832 kB in 0s (6,389 kB/s)        
(Reading database ... 300303 files and directories currently installed.)
Preparing to unpack .../libappstream-glib8_0.5.13-1ubuntu6_amd64.deb ...
Unpacking libappstream-glib8:amd64 (0.5.13-1ubuntu6) over (0.5.13-1ubuntu5) ...
Preparing to unpack .../libdfu1_0.8.3-0ubuntu4_amd64.deb ...
Unpacking libdfu1:amd64 (0.8.3-0ubuntu4) over (0.8.3-0ubuntu3) ...
Preparing to unpack .../libfwupd1_0.8.3-0ubuntu4_amd64.deb ...
Unpacking libfwupd1:amd64 (0.8.3-0ubuntu4) over (0.8.3-0ubuntu3) ...
Preparing to unpack .../fwupd_0.8.3-0ubuntu4_amd64.deb ...
Unpacking fwupd (0.8.3-0ubuntu4) over (0.8.3-0ubuntu3) ...
Preparing to unpack .../libgd3_2.1.1-4ubuntu0.16.04.10_i386.deb ...
De-configuring libgd3:amd64 (2.1.1-4ubuntu0.16.04.8) ...
Unpacking libgd3:i386 (2.1.1-4ubuntu0.16.04.10) over (2.1.1-4ubuntu0.16.04.8) ...
Preparing to unpack .../libgd3_2.1.1-4ubuntu0.16.04.10_amd64.deb ...
Unpacking libgd3:amd64 (2.1.1-4ubuntu0.16.04.10) over (2.1.1-4ubuntu0.16.04.8) ...
Preparing to unpack .../intel-microcode_3.20180807a.0ubuntu0.16.04.1_amd64.deb ...
Unpacking intel-microcode (3.20180807a.0ubuntu0.16.04.1) over (3.20180425.1~ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Setting up libappstream-glib8:amd64 (0.5.13-1ubuntu6) ...
Setting up libdfu1:amd64 (0.8.3-0ubuntu4) ...
Setting up libfwupd1:amd64 (0.8.3-0ubuntu4) ...
Setting up fwupd (0.8.3-0ubuntu4) ...
Setting up libgd3:amd64 (2.1.1-4ubuntu0.16.04.10) ...
Setting up libgd3:i386 (2.1.1-4ubuntu0.16.04.10) ...
Setting up intel-microcode (3.20180807a.0ubuntu0.16.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic


Progress: [ 97%] [#####################################################################################..]

```

Update: The system will not boot now. I get the "Welcome to emergency mode!" screen

---

### Post by deadflowr on 2018-08-28
How long was it hanging?
And can you boot into an older kernel from the boot menu (selected from the Advanced Options menu)?

---

### Post by boonedoggle2 on 2018-08-28
Okay, so I got this fixed and I will post what I did here in case somebody else has the same problem.

When I booted the system, it went into Emergency Mode, to which I logged in. Then I:


1. enabled the networking with:
```
$ service networking start
```
2. determine your ethernet interface via
```
$ ip link show
```
3. turned on dhcp for your interface (mine was eth0)
```
$ dhclient eth0
```
4. Updated the repo
```
$ apt update
```
5. configured dpkg
```
$ dpkg --configure -a
```


I also had an issue where one of my drives got borked in the process somehow. So I went into /etc/fstab and commented out all drives that were not /


Then I was able to sucessfully boot the system. I then repaired the drives via:
```
$ sudo fsck -f /dev/sdxy
```


I hope that helps somebody.

---

### Post by boonedoggle2 on 2018-08-28
It was hanging for about 30 minutes before I killed it. I probably could have booted into an older kernel, but I didn't try. See my other reply for the solution.

---

### Post by wildmanne39 on 2018-08-28
Glad you got it working and thanks for posting the solution!

---

