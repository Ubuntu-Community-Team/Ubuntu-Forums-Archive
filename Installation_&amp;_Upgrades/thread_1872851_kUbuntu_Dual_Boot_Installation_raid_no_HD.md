---
title: "kUbuntu Dual Boot Installation raid no HD"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by chomp! on 2011-10-31
Howdy Folks,

I've been having a whale of a time trying to install ubuntu alonside Windows 7.  So far I've tried 11.04 (kUbuntu and Ubuntu) and 10.04.  The common problem to them all is that the installer thinks I have no hard drive space.  If I dig in a bit more, I think the problem is that it thinks I have no.. hard drive.  In first page of the installation preparation wizard the line: '4.1 Gb drive space' has a nice big X in front of it.

Currently I have windows 7 installed on a raid 5 (nvidia fakeraid) and I would like to install ubuntu alongside it. 

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 RAID bus controller: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (RAID mode) (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)

```

and... gparted says I have a partition outside the disk.  the gui pops up blank.
```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Can't have a partition outside the disk!

```

```

sudo fdisk -lu

```
returns nothing...

---

### Post by oldfred on 2011-10-31
I do not know RAID. But saved this info:

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

---

### Post by chomp! on 2011-11-03
Well the live cd literally doesn't recognize anything in my case.  Along with the above, after reading the posts you forwarded (I'd already read all of the 'offical' fake raid docs from ubuntu).  

Mapper is empty:
```
>ls /dev/mapper
control
```

Dmraid think/s that there is nothing to be done:
```
>sudo dmraid -tay
no block devices found

```

Just by the numbers, I find it difficult to believe that no one else has had similar issues.  Anyone have any ideas?

---

### Post by darkod on 2011-11-03
Did you try the alternate install CD? For Ubuntu with LVM and/or RAID you should use the alternate install cd, not the standard desktop.

It is still the standard desktop version, you end up with the same, but the installer is text based, not graphical. But it does include LVM and RAID support.

---

