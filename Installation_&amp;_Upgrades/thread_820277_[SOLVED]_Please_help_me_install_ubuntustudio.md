---
title: "[SOLVED] Please help me install ubuntustudio"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by blattengel on 2008-06-06
Brief: I'm installing ubuntustudio, and had problems installing timidity and ubuntustudio-audio.  Running ubuntu using a live cd right now.  Version 7.10.

I've been following this guide to install ubuntu:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Except I'm not installing ubuntu-desktop, I am installing ubuntustudio as outlined here (minus the upgrade part):
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29)
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

I get stuck on that step with the following output from the terminal (I've done this a couple times already):
```
root@ubuntu:/# apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntustudio-desktop is already the newest version.
ubuntustudio-audio is already the newest version.
ubuntustudio-audio-plugins is already the newest version.
ubuntustudio-graphics is already the newest version.
ubuntustudio-video is already the newest version.
linux-rt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                                      * Starting TiMidity++ ALSA midi emulation...                                            ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                  [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```

I'm pretty sure it isn't a problem with FakeRaid:
```
ubuntu@ubuntu:/target/cdrom$ sudo dmraid -r
/dev/sdb: nvidia, "nvidia_ijcaifjh", stripe, ok, 625142446 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_ijcaifjh", stripe, ok, 625142446 sectors, data@ 0
ubuntu@ubuntu:/target/cdrom$ sudo fdisk -l /dev/mapper/nvidia_ijcaifjh

Disk /dev/mapper/nvidia_ijcaifjh: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_ijcaifjh1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/mapper/nvidia_ijcaifjh2            5223       44385   314576797+   5  Extended
/dev/mapper/nvidia_ijcaifjh5            5223        5744     4192933+  82  Linux swap / Solaris
/dev/mapper/nvidia_ijcaifjh6            5745        7311    12586896   83  Linux
/dev/mapper/nvidia_ijcaifjh7            7312       44385   297796873+  83  Linux
ubuntu@ubuntu:/target/cdrom$ 
```
1 is XP
5 is swap
6 is /
7 will be home

For a little history (nothing to do with the problems from what I can tell), I've set up Ubuntu 7.10 and XP on this system before.  I made the mistake of using XP's "Computer Management" to create a partition on unallocated space.  It could see all the partitions just fine, so I assumed the utility would not touch them.  It unfortunately did :(  It somehow merged my 4 GiB swap partition, and 12 GiB / partition into a 16 GiB partition, and made my home partition become unallocated.  Pretty bizarre... It did however succeed in creating the partition I wanted in the unallocated space after the extended partition.  I messed around with gparted and other utilities for a while in hopes of learning how to get my partitions back, files intact.  After some tinkering, I found testdisk.  That utility couldn't find the old partitions, so I gave up, and decided to reinstall Ubuntu.

I've been working on this for a good part of today, and need sleep.  I'm posting this in hope of getting help.

---

### Post by blattengel on 2008-06-06
Alright, this is resolved.  I decided to come back to it later, as I don't think those two packages were necessary for my system to boot.  I tried it after doing some other stuff from the FakeRaidHowto guide, and it worked great, no errors.  I think I got the error initially because I missed a line earlier in the guide.  I noticed the /target/dev/mapper directory was missing, then figured out I didn't follow the guide in doing:
sudo mount --bind /dev /target/dev

I think that is what fixed the cause of the errors.

---

