---
title: "Installing onto an USB stick"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by Tinky Winky on 2012-02-29
[FONT=Verdana][SIZE=2]Folks,

I have been attempting to install Ubuntu 11.10 onto an USB stick rather than run a live version of it from the USB stick.  Previously I have successfully installed various distros and older versions of Ubuntu but recently when I tried to upgrade to 11.10, I have noticed that it and other distros no longer like being installed on USB sticks.[/SIZE][/FONT] 
    [FONT=Verdana][SIZE=2]I cannot imagine that all distros have the same problem so I very much suspect that I am the issue, but I cannot figure out what I may be doing wrong and I was wondering if anyone could shed some light on this please.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Kind regards[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Tinky
[/SIZE][/FONT]

---

### Post by efflandt on 2012-02-29
If you want help with a problem it would help to say what sort of problem you are having.

Do you have trouble during install or booting after install?

For example I have found that with the exact same nvidia driver version number, I have to use **nomodeset** to boot 11.10, but not 10.10, even though would both would use kernel mode setting by default, and the only difference I am aware of is the kernel version and how splash is handled during boot.  If I do not use **nomodeset** for 11.10 my display goes black with "No Signal" after the grub menu.

And although grub should use UUID's which should make the actual device you are booting from a non-issue, there have been some grub updates or configurations that seemed to use the actual device instead, and if the USB ends up as a different device than when installed, it might trip up trying to find the root (/) device.  Other times it boots fine whether it ends up as /dev/sdb or /dev/sdg.  So in rare cases you may need to edit /boot/grub/grub.cfg on the USB to boot the proper root device.

---

### Post by Tinky Winky on 2012-03-01
Efflandt,
 
Thanks for replying, basically the most recent version of Linux I can install onto a USB stick without incident is Mint 7.  
 
Unfortunately, on each occasion I attempt to install more recent versions of Linux, even after re-formating the USB stick, the install stops to tell me there is an issue with the 'root' partition.  Considering Mint 7 looks after formating issues, as do other older verisions, I cannot figure out why more recent versions are having issues.
 
Any help is greatly appreciated!
 
Regards
Tinky

---

### Post by oldfred on 2012-03-02
I have had several full installs on my 16GB USB flash drive. I use a 8GB / (root) partiiton, no swap and leave the other 8GB for data. I always partition in advance and use manual install to choose partitions and other than the nomodeset issue efflandt discusses have not had problems. Currently running 12.04 on my flash drive for testing.

Often the issue with / (root) is during install you have to select the partition, choose formating, and choose the partition as /. Then it works.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by Tinky Winky on 2012-03-02
Oldfred,
 
Thanks for the advice, it gave me insight into the problem and as I write, Ubuntu is installing on my USB stick!
 
I discovered that for Ubuntu the USB stick has to be formated in either FAT32 or NTFS then after opening the appropriate 'iso' file in WinRAR, stalling Ubuntu is reasonably straight forward.
 
Earlier this evening I installed Centos 6 on another USB stick using the same technique you discribed but a few messages popped indicating that the root was too small then another indicating that the absence of Swap would cause problems.  Once I formated the USB stick 50 % root, 50 % swap, Centos 6 installed with ease.
 
Thanks again for your advice. I will be dumping all things MS as soon as I get Ubuntu set up.
 
Kind regards
 
Tinky

---

### Post by efflandt on 2012-03-03
If you have enough RAM (like 2 GB or more), you do not necessarily need swap.  Swap is used to hibernate, in which case swap should be a little larger than RAM.

Suspend does not use swap.

I don't use swap for 64-bit Ubuntu on SD that I use on my 2 GB RAM tablet PC, nor for my 8 GB desktop (which cold boots faster from SSD than waking from suspend).

A bootable install iso on USB uses FAT32, but a regular install should not need that (ext2 is probably best for USB flash, to minimize write cycles).  However, it probably needs an MSDOS partition table if an iso was previously written directly to it without any partition(s).  I have had to use gparted to recreate the MSDOS partition table a number of times when I accidentally formated the entire USB stick (like sdb) instead of the partition on it (like sdb1).

---

### Post by gordintoronto on 2012-03-03
With Mint 12, I had no trouble making a LiveUSB, then installing onto an 8 GB flash drive, formatted as EXT4.

---

### Post by Tinky Winky on 2012-03-08
I have managed to resolve two different issues by downloading another version of Ubuntu and now I have Ubuntu operating on three different computers as well as one USB stick.

Thanks for all your help and advice.

Regards
Tinky

---

### Post by ScientificProp on 2012-03-08
I'm having a problem where my root partition is not being recognized during bootup, after installation onto a USB HDD. I partitioned the entire HDD which was formatted as ext2 for the root (/), a swap, and ext4 for the /home partition.
Do I need to have an FAT partition somewhere and would the absence of FAT explain the problem I've been having?

Thanks, ScientificProp

---

