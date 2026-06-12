---
title: "Request for advice: install 18.04"
date: 2021-01-05
forum: Installation &amp; Upgrades
---

### Post by mringer on 2021-01-05
Currently running L-Ub 16.04. First I tried the  mini  version, because I believe that later versions of Lubuntu are severely bloated. 
Copied the 18.04  .iso   to a USB stick. Started to install. There were 2 minor problems:

1: partitioning the disk. The instructions say that a partition marked  "K"  will be kept; and you can change mount
points. I could not find any way to do so. Also it offers to partition the USB stick that I am booted from.

2: Install process is very slow. Well over 3 hours. So there ought to be a method to resume a failed install where it left off & the 
user should be warned in advance and told how to do this.

Eventually Grub did not install. I dont know why, there was no error message. Retried, failed. Skipped this step, continued to the 
end. Booted off a rescue CD, installed  grub:  no error.

Removed the USB, tried to boot the new system. I got ~~1/2 a screen of error messages which look like the tail of a system log. 
I dont know how to read these. Only thing I can vaguely understand was

/sbin/init: exec format error

Booted off another disk. Looked in   /var/log ,  cant find anything that looks relevant. I would be happy to post the contents of
/var/log  , but I dont see how to post tarfiles in pastebin.   /sbin/init   is a link to   /lib/systemd/systemd   .  I copied a file of that
name from the bootable disk: this gave a different stream of errors

So I tried the regular  Lubuntu 18.04   live CD. I dont know how to handle the partition-disks stage.  I cannot now recall the exact
words, but the relevant menu says something like:

Lubuntu  16  detected.

1. over-write 16, all your files will be erased.
2. Install 18 alongside  16
3. Erase entire disk

I dont want to do 1, I only want to over-write the system & keep my personal files.  So I tried  2  .  The target disk has ~~90 G of free 
space and the  /home  partition is less than 1/2 full. If I were using  parted  it would be easy to either put a new partition in the free 
space or to shrink  /home  & put the partition there. But with the 18 live CD, I could not see any way to do either.  

I dont think I ever had these problems installing either 12 or 14 or 16. Please any advice? Thank you.

---

### Post by grahammechanical on 2021-01-05
There are big differences between the installation instructions for a minimal install and a standard install. I tried to access the Lubuntu site to get a link to the Lubuntu installation instructions but there is something wrong with the site. Here is a link to the Ubuntu install instructions. The Lubuntu instructions will be similar but with visual aids appropriate to Lubuntu.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

For more detailed help you will need to provide information about your motherboard - UEFI or BIOS? and the partitioning of your hard drive. What other operating systems are on the drive? Do you want to keep them?

The welcome window will give you the option of Try Lubuntu & Install Lubuntu. If you Try Lubuntu you will be able to load GParted and do all the changes to the partitions you require.

The Install Lubuntu option will ask you about the Installation Type. With 16.04 already on the drive you can select Install Alongside and let the installer take care of everything. If you want more personal control then you must select Something Else. Then you need to know about mount points for partitions and where to install the Grub bootloader and if you want /home on a separate partition. Do not try to use /home of 16.04.

With the minimal install we have to follow the instructions on the screen. Which means we need to know what we are doing and have the partitions all sorted about before hand. Keep in mind the minimal install ISO is itself very small. So, it has an entirely different installer with minimal instructions.

Regards

---

### Post by mringer on 2021-01-06
> **grahammechanical said:**
>   [CUT]  There are big differences between the installation instructions for a minimal install and a standard install. 

...

For more detailed help you will need to provide information about your motherboard - UEFI or BIOS? and the partitioning of your hard drive. What other operating systems are on the drive? Do you want to keep them?

...

With the minimal install we have to follow the instructions on the screen. 

 ...

Regards

thank you for your reply.

Please: are the instructions for minimal install published anywhere?

Motherboard: I am fairly sure that I am not running UEFI  now. [https://itsfoss.com/check-uefi-or-bios/#linux](https://itsfoss.com/check-uefi-or-bios/#linux)  said:

look for    /sys/firmware/efi

& it is not there. 

Partitions:

1:  ntfs   windows XP
free space 90G
2: swap
3: extended containing
5: root, LUB 16.04
6: /home 200G unused

I want to keep these but I think there is ample space for  minimal  either in the free space or by shrinking  /home
If I understood you correctly, I must create partition(s) before trying to install.

... follow the instructions on the screen....

That is what I was trying to do. 

I would rather install minimal than regular lubuntu.
Thank you, Mark

---

### Post by GhX6GZMB on 2021-01-06
I'd like to address your concerns that Lubuntu is "severely bloated":

I run Lubuntu 20.04 LTS in standard configuration.
The / partition takes around 8 GB.
RAM usage after boot is around 320 MB. Starting my web browser increases that to around 680 MB.

My laptop has 2 GB of RAM and runs very fast and reliably with 20.04. I've never had problems with space. My swap partition is practically inactive.

Just to give you a few numbers as opposed to beliefs.

Concerning mini-Lubuntu: AFAIK it doesn't exist any more.

---

### Post by mringer on 2021-01-09
> **ml9104 said:**
> 
[cut]...
Concerning mini-Lubuntu: AFAIK it doesn't exist any more.

The ISO that I tried to install came from

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

section "64 bit PC", file no 1: Ubuntu 18.04  MD5 8388 etc. 

I would be most grateful if somebody could tell me how to post the 
error messages that appear when I try to boot the system that I
installed from this ISO. 

I am hoping to reply to the rest of your message but I need to check
some facts. Also I must post a new thread as any reply would be off topic.

---

### Post by mringer on 2021-01-14
> **ml9104 said:**
> I'd like to address your concerns that Lubuntu is "severely bloated":

[CUT]



I have attempted to answer this in a new thread:

[https://ubuntuforums.org/showthread.php?t=2456573](https://ubuntuforums.org/showthread.php?t=2456573)

---

### Post by VMC on 2021-01-14
I'm unsure why you needed to start a new topic. This one you listed was fine.
 Please define **bloat**. Is it the size of the ISO, or the added new features.

---

### Post by TheFu on 2021-01-14
A fresh install is 9 - 15 minutes these days.

An upgrade install is 30 min to 3+ hours and the upgrade process is very clear about taking multiple hours.
I did an Lubuntu 16.04 --> 18.04-hwe upgrade today. Ran into a few issues because I'd removed and highly customized lots and lots of system things since it was first installed w/ 10.04 and has been migrated forward.  I started at 2pm and did the last reboot with the HWE kernel at 3:45pm. 

It wasn't completely smooth.  The problems were self-inflicted.
[LIST]
[*]The root LV became corrupted somehow. Had to boot from a *Try Ubuntu* flash drive to run fsck on all the LVs and partitions. No idea how this corruption happened.
[*]/boot/ ran out of space immediately after the first patches post-reboot. Fortunately, I saw it and was able to take steps so a minor problem didn't become a major issue. Happened because i allowed the default partition size for /boot 10 yrs ago and never fixed it.
[/LIST]

The non-standard network setup on that machine wasn't touched. Happiness.
All the major things on the machine "just worked" post-upgrade. It is mainly an NFS server, but it does calbre, plex, apt-cacher-ng, and runs a few VMs with nextcloud, wallabag, and an IRC bouncer.  All working.

1 box done. 15-ish more to go.  16.04 --> 18.04.x

---

