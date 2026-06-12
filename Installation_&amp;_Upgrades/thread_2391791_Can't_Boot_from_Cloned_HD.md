---
title: "Can't Boot from Cloned HD"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by MaccyDG on 2018-05-13
Hello,

I'd be grateful for any help on an issue I'm having.

**In Brief**
I use Ubuntu 16.04 64 bit on a 5,400 rpm HD and am trying to upgrade it to a solid state device. I have cloned the disk, which appears to have worked, but the new SSD won't boot.

**More Info**
I've had a look at the sticky relating to the problem I'm having, but as the problem doesn't occur on the original disk that the clone was made from, I'm not sure what route to go down from here. I'm quite au fait with hardware stuff, but not that knowledgeable about the software side of things, so please don't assume too much knowledge! Ideally I want to keep my clone and not format/reinstall the OS afresh, as I have an old Win XP partition on there that I boot into once in a blue moon.
I can sometimes reach the Grub menu and sometimes not (seems quite random as to whether I do or not). When I do reach it, selecting my Ubuntu 16.04 (or Win XP) installation results in a black screen.

System: Acer Aspire 5100, 2x 2 GHz AMD Turion 64 bit, 4 GB RAM, RS482M [Mobility Radeon Xpress 200], 120 GB Samsung mSATA solid state with mSATA to IDE bridge controller.

GParted shows the same partitions on the cloned drive as on the original, and that they have the same amount of data written to them. So whilst it's possible that the cloning went wrong, it's probably not where I want to start?

Separately, I have made a bootable USB of Ubuntu 16.04. When this is inserted either with no HD/SSD present, or with only the original HD present, it boots. When I try to boot it when the new mSATA drive is present, it shows a black screen, same as booting off the mSATA device. This seems odd to me, and might be key to solving the issue. In all cases, the USB key is at the top of the boot list. When I boot from the USB key, I get a message telling me that it's using generic retpoline because LFENCE hasn't been serialised, which I don't see when booting from the original drive.

**Things I have Tried**
[LIST]
[*]Reinstalling GRUB on the new disk 
[*]Using the boot option "--verbose text" in GRUB (it shows a load of text telling me what it's doing, then the screen turns blank again, as before) 
[*]Using boot option "radeon.modeset=0" (it says "[drm:radeon_init[radeon]] *ERROR* No UMS support in radeon module" 
[/LIST]

Just to be really explicit, **the original hard drive that this one was cloned from works perfectly**.

Any help appreciated!

Cheers,

Liam

---

### Post by rsrocha on 2018-05-13
How did you cloned it? Are you booting with UEFI?

---

### Post by MaccyDG on 2018-05-13
I cloned it using Redo Backup Live CD.

I'm not sure how to tell if I am booting it with UEFI, and I can't find the answer on DuckDuckGo. Booting off my old hard drive, I typed this in the terminal:
```
#!/bin/bash

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
... as per this question: [https://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios](https://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios)

It returns the text "BIOS". So I think that means my old hard drive is booting in BIOS mode. But I guess this doesn't mean my new one is. How would I find out?

Thank you!

Liam

---

### Post by oldfred on 2018-05-13
You cannot have duplicate UUIDs, so HDD must be disconnected once you start booting with SSD. You can change UUIDs on one system or the other, but to have it boot then must edit UUIDs in fstab and reinstall grub.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by MaccyDG on 2018-05-14
I have been swapping my HDD and SSD into/out of a single drive bay, so they are never plugged in at the same time. Should I still run Boot Repair? I ran it yesterday, to re-install GRUB, and it gave me this link:
[http://paste.ubuntu.com/p/pkXX8N98p7](http://paste.ubuntu.com/p/pkXX8N98p7)

---

### Post by oldfred on 2018-05-14
Is your BIOS set for AHCI, not IDE nor RAID?
And if so old not to have that setting, it may not work.

I first purchased  small SSD for my old BIOS desktop. My XP only booted with IDE and SSD only booted with AHCI. And installing AHCI drivers in XP essentially required a new install. So I retired XP. :)

---

### Post by MaccyDG on 2018-05-14
OK, thanks. No, there are no settings to choose AHCI or any other mode :(. I've already flashed the most up-to-date BIOS (from 2009!).

OK, so are you saying that if I get rid of the XP partition I might have a chance? I could do a vanilla install of Ubuntu on the drive?

---

### Post by oldfred on 2018-05-14
Unless you have AHCI, I do not think you can boot from SSD? System is just too old.
You may be able to configure boot from a flash drive, and have rest of install on SSD?
Not sure if just grub install to MBR of flash drive or full /boot on flash drive would be required. And either may not work.

---

### Post by MaccyDG on 2018-05-14
OK oldfred, thank you so much for your help. I think I'll just buy the fastest IDE drive I can get. Not the end of the world - the laptop is still surprisingly fast for its age (2006), so hopefully has a few more years in it yet :D.

---

### Post by oldfred on 2018-05-14
I have an old 2006 laptop. It had 12.04, but I built new desktop with UEFI & SSD. 
I, just to see if it worked, did install 16.04 to it and it seemed to be better than 12.04 was. But compared to my new UEFI/SSD boot systems still pretty slow.

---

### Post by MaccyDG on 2018-05-16
Same here - when I upgraded to 16.04, my computer was faster, even though I was using Unity in 2D mode in 12.04.

---

### Post by Bashing-om on 2018-05-16
MaccyDG; Hello -

I too run on old old hardware - 2007- and when I installed an SSD in this old box I too discovered that AHCI enabled in bios is required.
But AHCI was not known in 2007; after a lot of struggling I did find that in my Phoenix Award bios one can enable raid for the system and disable raid for all drives and whalla ! AHCI is set .  
Running now 2 SSDs:
> 
sysop@x1804mini:~$ sudo parted -l
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  149GB  149GB   primary   ext4            boot
 2      149GB   165GB  15.7GB  extended
 5      149GB   154GB  4719MB  logical   linux-swap(v1)


Model: ATA PNY CS900 120GB (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  8390MB  8389MB  primary   ext4         boot
 2      8390MB  18.9GB  10.5GB  primary   ext4
 3      18.9GB  25.2GB  6291MB  primary   ext4
 4      25.2GB  88.1GB  62.9GB  extended
 5      25.2GB  56.6GB  31.5GB  logical   ext4
 6      56.6GB  67.1GB  10.5GB  logical   ext4
 7      67.1GB  77.6GB  10.5GB  logical   ext4


sysop@x1804mini:~$ 


[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

