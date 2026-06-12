---
title: "Trouble installing Ubuntu from USB - NVIDIA and no UEFI options"
date: 2020-12-08
forum: Installation &amp; Upgrades
---

### Post by peaflower on 2020-12-08
Hi, I've been trying and failing at installing a fresh Ubuntu OS on my lab desktop.

It allows me to "Try without installing" but freezes on the "partition" part of the installation, and no existing partitions show up.

My computer specs are:
- AMD Phenom II X4 820 Quad Core
- NVIDIA GeForce 9100 
- 8GB DDR3 ram
- 1 Terabyte HDD

The original installation came with Windows 7, but it's been wiped from the system. It also used to have an old version of Fedora, but it needed updating. However, any previous attempt at updating failed miserably (presumably due to trouble with the NVIDIA card drivers). Now there is nothing on the boot.

Attempted fixes:
1. I tried adding "nomodeset" and "acpi=off" to the boot options, but that didn't fix it.
2. I tried going into the Boot menu (the blue and grey screen) to enable UEFI mode, but no such option was available. 

Observations:
I tried to do a "boot-repair" from the "try without installing" mode (as per instructions here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), and this was the result [https://paste.ubuntu.com/p/TWDgKxfmfH/](https://paste.ubuntu.com/p/TWDgKxfmfH/) 
Maybe it gives some hints as to what's happening.

I'm a beginner with Ubuntu and don't have much of any experience troubleshooting these problems. I'll be really grateful for any help!

---

### Post by peaflower on 2020-12-08
Here's more information, result of 
sudo fdisk -l
df -h
[FONT=Courier New]
```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.98 GiB, 2103640064 bytes, 4108672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.55 GiB, 15610576896 bytes, 30489408 sectors
Disk model: DataTraveler 2.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x56f48570

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *          0  5439487  5439488  2.6G  0 Empt
/dev/sda2       5017392  5025327     7936  3.9M ef EFI 
/dev/sda3       5439488 30489407 25049920   12G 83 Linu
ubuntu@ubuntu:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.7G     0  3.7G   0% /dev
tmpfs                        771M  9.4M  762M   2% /run
/dev/sda1                    2.6G  2.6G     0 100% /cdrom
/dev/loop0                   2.0G  2.0G     0 100% /rofs
/cow                         3.8G  167M  3.7G   5% /
/dev/disk/by-label/writable   12G   50M   12G   1% /var/log
tmpfs                        3.8G   19M  3.8G   1% /dev/shm
tmpfs                        5.0M  8.0K  5.0M   1% /run/lock
tmpfs                        3.8G     0  3.8G   0% /sys/fs/cgroup
tmpfs                        3.8G  536K  3.8G   1% /tmp
/dev/loop1                    30M   30M     0 100% /snap/snapd/8542
/dev/loop2                    55M   55M     0 100% /snap/core18/1880
/dev/loop3                   256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop4                    63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop5                    50M   50M     0 100% /snap/snap-store/467
tmpfs                        771M   52K  771M   1% /run/user/999
```
[/FONT]

---

### Post by ubfan1 on 2020-12-08
sda appears to be your install media, and no other disks are seen.  Check the cables?  What disks are seen from the BIOS?

---

### Post by CelticWarrior on 2020-12-08
UEFI is firmware just like BIOS is firmware. If you have one you don't have the other.
"UEFI mode" refers to the proper mode the OS or OSes should be installed in UEFI hardware, oppose to the alternative Legacy/CSM/"BIOS" mode still allowed by some UEFIs for retro-compatibility.

Now, your hardware is old enough to be BIOS therefore it makes no sense to "enable UEFI mode" and your "[COLOR=#000000]1 Terabyte HDD" is not even detected. Is it at least recognized in BIOS? Probably not because very likely defective. [/COLOR]

---

### Post by peaflower on 2020-12-08
Thanks guys for the replies. So I can't see the HDD in the BIOS. Thing is, it was working find until I tried installing a new OS a while back, so I feel like I messed something up rather than the HD becoming defective at that exact point. I don't know what cables I should check, do I have to open the desktop case and look inside?

This is the initial startup screen
[IMG]https://lh3.googleusercontent.com/riBGrtQrxj_abS7xkuW5IkjgswgyLYRf9rPiBQm5_ZVBRhWtXyadtKrcDWoRMnQ-Pu9uumszFu6Q3tqHG0YwHBk_AdXRgUkUZKzh9Z4y5vkDCso19IZs0ivzi1WCOJk0l1Kr7ZLGD7AiEr3CH1VojaLHkQPpal55uHAAuGAiSlDYiYDgiigul54RTplxmrSj4WiwFrmpC-6g8wH2WmRmwfm4CncrXaso8fWFpHmOYa96a_d30iri5vHdzBDlNKhq38AH-muD1fmKQqGk6N_jqc2LUI4ygJELoiYM4FhjVRDiiXfP9V3OxRocwspERABf6fqJgZGq-kxQM1SDI1Wmw7EfwYqKXDjFqtLEDI0YKDcd4Zj8rUjb2qJPtHni1RQ8ldObUeIyyGQMpmLt7HBSu9uzqyk3bUppGed63QAed9LtMFpHhCwpHafOLdNjiQ1d7Ur7w7HREDbXHM1wifM7EvUIdUl-0He0xnmEUyDGxSGYj0zuaDu1iMF7nHhsns1wbNuCtgCTxD_-7p8g4mOPMgRFr8dLNgB4qq5h2qhI-7IZrACG7QjzMaJzF24W0IZrHObIn4q2TqFrNehP8ck2R5JdTaCbwHD7EojzHgBRdgKfk32FUVTRSAKmXXB0ldoSc0nWjOSiVdTR93iXk6voQnA2mAlWT82EDOLpYEMRVQnhFhfsxKZxztdjwSHCe78=w1170-h658-no?authuser=0[/IMG]

---

### Post by ubfan1 on 2020-12-08
Time to open it up, and check the cables (or that the disk is still present! Someone in the lab might have repurposed it ;^D).

---

### Post by CelticWarrior on 2020-12-08
The drive is old and already passes its best by date years ago. It was probably an "accident waiting to happen" precipitated by the installation attempt but not due to user error.

Yes, please check the cables as suggested above, just in case. Open the case, find the HDD and re-seat the cables, both data and power, and the data one on both extremities. Boot again and check if now it's detected.

---

### Post by peaflower on 2020-12-08
Ok so I opened it up, apart from being a bit dusty everything is there. :) I cleaned out a bit of the dust and unplugged the two hard drive cables and plugged them back in again.

When I turned it on, the HD still wasn't recognized, but a new error came saying "System Fan Has Failed. Service PC to prevent damage to the system" even though both fans are clearly running (and one is connected to the PCB where it says "system fan".
No idea what's going on.

Edit: Just unplugged the fan from the motherboard, blew on it and plugged it back in, and now the fan error is gone... I'll try doing the same thing to the hard drive cables.

---

### Post by peaflower on 2020-12-08
It doesn't look like its a problem with the hard drive, or the cables. I tried replacing the cables, and also tried with two other hard drives we had lying around. Every time it was still the same problem, no HD detected on the startup bios screen. Could it be a software/firmware issue, and would there be a way to check that from the bootable USB?

---

### Post by CelticWarrior on 2020-12-08
No, it's not a software issue. BIOS is before any software.

If other **known good** HDDs and cables produce the same result then it's likely the motherboard. Have you tried other SATA ports? Your screenshot suggests you have at least another 3...

---

### Post by peaflower on 2020-12-08
I can't 100% confirm that those other HDDs are good, but likely good (because the motherboard on the computer they came from is completely busted, so I thought the motherboard gave out and one of our lab members just took the Harddrives out for salvage). 
Yes I tried plugging the cables into the other SATA ports, and it also didn't work. 

It's really frustrating, I think for now I'm going to just try working on a different computer. If you have any other ideas I can try it still, though. I'd like to save the computer if at all possible.

---

### Post by ubfan1 on 2020-12-08
Having replaced the cables and hdds, looks like a motherboard problem.  I suppose you could try a reset to factory specs.  Don't know what problems other than the clock could be caused by a dead CMOS battery,but maybe check that tool.

---

