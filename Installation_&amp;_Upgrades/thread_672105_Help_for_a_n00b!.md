---
title: "Help for a n00b!"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by darkman738 on 2008-01-19
Hi, so here is my problem.  I have a laptop using a SATA drive.  I am running Windows a one partition and attempting to install Ubuntu 7.10 on another.  I boot from the CD and walk through the install and it stops at the end stating that GRUB could not be installed, this is a fatal error, and install goes away :confused:.  Ubuntu has been installed to the partition and added to NTBootLoader as an option, when I choose to boot to it however I only get the terminal and am unable to launch th GUI [-X.  I am assuming this is because there is further installation that needs to be done after boot that the install isn't preping since it crashes.  I have also noticed that the option in the install is attempting to install GRUB to (hda).  This is not my HDD, sda is.  I have attempted to change this and failed.  I have attempted to manually install GRUB from the terminal 
{
> grub
root (sda#,#)  (here I have tried every combo of numbers I can think of)
setup (sda#, #) (again combo'd numbers)
} [-X

I have tried to install without GRUB with the same results (no error/crash about not installing, but dose not load GUI on boot, but does appear to finalize some installation.)  

I've notices that lots of people as for the disk config so:
ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4673    37535841    7  HPFS/NTFS
/dev/sda2            4674        6044    11012557+  83  Linux
/dev/sda3            6045        7166     9012465   1c  Hidden W95 FAT32 (LBA)
/dev/sda4            7167        7297     1052257+  d7  Unknown
 
sda3 is the recovery partition that came with my computer that I would not like to loose.
sda4 is some mystery partition, again came with the computer so I figure its important.

Any help would be appreciated.  I have set the install partition on a Primary partition and I have not setup a swap partition.
I'm not a novice computer user, and am quite proficient in Windows, however in an attempt to further my knowledge of OS's this is my 2nd or 3rd attempt in several years to use a Linux Disto and as of yet have been unable to install on any computer I have ever tried for various reasons  ](*,) (lack of important drivers such as Vid card, ect.)


Thanks in advance

---

### Post by darkman738 on 2008-01-22
/bump

Anyone have any ideas?

As an update I have gotten it to work with another laptop, but this one still is giving me trouble.

---

### Post by Saponsky09 on 2008-01-22
Well... I'm guessing here 'cus I'm a little confused about your partition's scheme.  I think you said... /dev/sda1 ->Windows
                /dev/sda2 ->(maybe Linux)
                /dev/sda3 -> Windows recovery
                /dev/sda4 -> Unknown ...
  well, all I can think of is that maybe Grub is loading the wrong partition so try these...
when you see the boot options, highlight Ubuntu and press 'e'... you should see something like this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b2102a9-6137-4f3e-825a-5f257c6d1665 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
check if yours say something different in: root     (hd0,0), if so, try changing it to (hd0,0) and then press 'b' to see if Ubuntu boots.

---

### Post by Partyboi2 on 2008-01-22
Your ubuntu partition I think  is hd0,1 for grub purposes. I see you don't have a swap partition. Did you manually create the partitions or let the ubuntu installer do them?

---

