---
title: "Problems finding partition for Install (Kubuntu)"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by PyroboyUK on 2010-12-19
Im rather new to Linux and learning every day as I go along. Currently my only real experience with Linux is on my Laptop where im using Ubuntu as the Primary OS. After getting to grips with the overall workings of Ubuntu I quite fancied extending Linux onto my Desktop Computer and after observing Kubuntu and its features I would like to go ahead with it.

Recently I upgraded my computer with an OCZ SSD (Approx 60GB) and I thought this would be the perfect time to go ahead with a Linux install. Like my laptop I was hoping to have a copy of Windows installed on the computer so that I can just boot into Windows and play around with office etc and have Linux as the OS for everything else. This works rather well on my Laptop as it seems to assume Ubuntu as the primary OS unless I tell it otherwise in an allotted time period. 

As the desktop computer stands it has a copy of Vista 64 on it, unfortunately at the time of install I had allotted all of the SSD to Windows, but according to (MiniTool Partition Wizard) I have successfully taken a partition away from Windows and formatted it into various different formats (Multiple attempts due to Linux install problems as I will explain).

So the problem.... I have created a Kubuntu Boot CD that seems to operate ok, I insert the CD and get to the stage where I can either run Kubuntu (That works ok but slow, im guessing due to it running from a CD drive) or choose to install. When I go to install I am always faced with the issue from one of the 3 main parameters it faces you with at the start. The installer can never see the required "More than 2.3GB Available". 
I have a partition taken away from Windows approx 12GB in size from the SSD and I have tried many formats (NTFS, EXT3, FAT 32 and also Un-formatted).

Can anyone point me in the right direction? I have tried various searches on the web but im not making much progress.

Thank You

---

### Post by ajgreeny on 2010-12-19
From the running live CD or from the install kubuntu choice at that menu just let the system go to the partitioning page of the install, and at that point choose the manual option.  I can't remember the exact words they use, but it will be obvious, and I think is the third option on that page.

A window should open up showing all the partitions on the disk(s) and will allow you to choose which partition to install the system to, or to edit that partition and make new partitions.  Don't forget you will need a swap partition, and a root partition at the very least.  A separate /home partition can be very useful, but if you run a dual boot system, a /data partition may be even more useful to you.

I think vista and ubuntu on a 60 GB disk may be a bit tight for space, as the last time I tried to shrink a vista partition on an unused vista OS, I could not get it to less than about 60 GB for vista alone, so maybe that is part of your problem.

---

### Post by Rebelli0us on 2010-12-19
Truth is Ubuntu installer sucks. It lacks the ability to let the user pick an existing partition to use. Manual partitioning can be done if you're a Linux geek but since you're a newbie I would practice on an unused 2nd disk or just install to a USB flash drive.

---

### Post by Pillars of Creation on 2010-12-19
From the kubuntu live CD have you tried running the GParted partitioning utility utility?

It it should be under system / administration.

I believe it&#8217;s much more straightforward to make your partitions from the live CD rather than trying to do the partitioning during the install process.

---

### Post by Rebelli0us on 2010-12-19
> **Pillars of Creation said:**
> From the kubuntu live CD have you try running the GParted partitioning utility utility?

It it should be under system / administration.

I believe it’s much more straightforward to make your partitions from the live CD rather than trying to do the partitioning during the install process.

You already have a partition ready, it doesn't need to be formatted. There's just no intuitive & straightforward way to point to an existing partition and tell Linux to install there! Practice but don't install unless you're absolutely certain where Ubuntu is going or you may trash Windows.

---

### Post by PyroboyUK on 2010-12-20
> **Rebelli0us said:**
> I would practice on an unused 2nd disk or just install to a USB flash drive.

I have tried installing this to a USB Stick as i thought it would be quicker to install from. The only problem after that was my computer not playing ball when it comes to booting from a USB Stick, it only lets me do (HDD, CD Rom & Floppy). Its an Asus P5Q Pro.

Im a bit confused what route to go down from here, thanks for your answers. Im just a little slow with Linux to start of with.

---

### Post by Pillars of Creation on 2010-12-20
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Rebelli0us on 2010-12-22
> **PyroboyUK said:**
> I have tried installing this to a USB Stick as i thought it would be quicker to install from. The only problem after that was my computer not playing ball when it comes to booting from a USB Stick, it only lets me do (HDD, CD Rom & Floppy). Its an Asus P5Q Pro.

Im a bit confused what route to go down from here, thanks for your answers. Im just a little slow with Linux to start of with.

How many yrs old is your pc? It should boot USB flash drive just fine, they are usually listed in the boot menu as HARD DISKS. Just make sure to install the boot loader to the USB drive, as I believe by default Ubu installs grub to the 1st hd.

The advantage is that your Linux will be portable, and will attempt to boot any PC that you insert it in.

---

