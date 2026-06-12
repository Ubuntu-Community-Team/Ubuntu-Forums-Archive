---
title: "Installation on a Sony Vaio VGN-S5HP"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by reebomber on 2010-08-08
Hello all, this is the first time I have posted in the forums, but I now have a very weird problem, which makes no sense, and I don't even know where to start looking:

I have a [Sony Vaio VGN-S5HP]("http://www.shoppydoo.com.br/preco-notebooks-sony_vaio_s5hp_b.html"), which is a fairly unknown computer... 

I have already successfully installed Linux in this computer in various flavors: 

- installed Ubuntu 10.04 under windows, no problem
- installed Ubuntu 10.04 in separate partition (ext4 and swap), no problem.

So, since everything was running more or less ok, I decided to ditch windows and go full on for Ubuntu... big problem. 

I had 5 partitions on my disk:

sda1 NTFS with winXP

sda2 extented, with inside:
sda3 NTFS with data I want to keep
sda4 ext4, ubuntu as second OS
sda5 swap

I started installation of Ubuntu, splitting sda1 into two, one ext4, another swap. Then, I formatted sda4 and sda5, into one single partition, and was planning to migrate all the data from sda3 there, when the system was running.

Ubuntu took FOREVER to install, and eventually failed. I tried to install OpenSUSE, and eventually managed to install it only starting a LiveCD, and then installing from LiveCD. That also took FOREVER. 

When I tried my first boot, it started hanging up, and I managed to see that it was stopping when trying to read or mount sda6. I tried re-installing, this time WITHOUT an sda6. The same thing happened, hanging at mounting of a drive, this time sda1. 

This totally confuses me, since apparently the only thing I am doing wrong is NOT having Windows installed ?? 

in short, since I know this is quite confusing: 
my system has no problem if I install Ubuntu from inside Windows, or have it dualboot to win, with windows in the first partition. 
When I try to install Ubuntu or OpenSUSE in the first partition, the system will not boot, blaming it on different partitions. 

I am guessing, maybe the NTFS partition is the clue? I can't get the data off the computer easily, to completely format the drive, but if you guys tell me that makes sense, I will. 

I really want to get rid of windows, but apparently my computer is not of the same opinion :(

Thanks

---

### Post by walterav on 2010-08-08
> **reebomber said:**
> Hello all, this is the first time I have 
I had 5 partitions on my disk:

sda1 NTFS with winXP

sda2 extented, with inside:
sda3 NTFS with data I want to keep
sda4 ext4, ubuntu as second OS
sda5 swap

I am guessing, maybe the NTFS partition is the clue? I can't get the data off the computer easily, to completely format the drive, but if you guys tell me that makes sense, I will.
Thanks

Please backup your data from "sda 3 NTFS with data I want to keep" to an external drive. Its easier and better to start with a new partition layout, made with Ubuntu/Gparted than the thing you ended up with right now.

During the Ubuntu install, choose to setup the harddisk manually.
Make a new MBR which removes all partitions and DATA on the drive.
Add a primary system partition using ext4 and mountpoint /
Add a primary home partition using ext4 and mountpoint /home
Add a primary swap.

note: you can only have 4 primary partitions which may contain a bootable OS, or 3 primaries with one extended which can hold another 13 partitions if you really want to :p

---

### Post by reebomber on 2010-08-09
Hi Walter,

thanks for your reply :)

That was my guess, to do a fresh install, but I was a bit afraid of doing that, since in fact I already had an installation of Ubuntu, dualbooting with win, and that were more partitions than this setting now... the only thing changing here was that I was installing the single OS on the first partition of the drive.

I will try to do this as soon as I get all that data backed up. I really can't stand win anymore :)

Will post if that helped. 

Thanks

---

### Post by reebomber on 2010-08-10
Hello again,

this did not work. I transferred all my data to another computer, formatted the disk, repartitioned it, installed OpenSUSE (I lost my Ubuntu disk, and it was too late in the evening to DL again) on sda1 (12gb), created sda2 (50gb) as /home, and a 2.5 gb swap at the end of the disk. Everything installed, I rebooted, finished the installation, and when I rebooted again, it never passed boot, trying to access sda1... 

Exactly the same as had happened before... 

It seems that this is a hardware problem, but, again, I had Ubuntu installed and running on dual boot with win. The problem is when Linux (Ubuntu or SUSE) is installed as single OS. 

GRUB is installed on this installation, btw. 

I can see the error during boot, when it is trying to access sda1, but I dont know how to get a log or printscreen of that? Even if it is logging, I have no system to access the files... 

Help? I'm really puzzled with this, it makes no sense...

---

