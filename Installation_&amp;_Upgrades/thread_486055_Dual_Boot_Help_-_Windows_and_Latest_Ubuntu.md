---
title: "Dual Boot Help - Windows and Latest Ubuntu"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by Lamez on 2007-06-27
I need help setting up a dual boot for my "box" aka computer. I am new to linux and I have some questions as well. This is how I want my partitons to be set up.

-----------------------
Windows - 130Gb
Linux - 130Gb
Swap - 4Gb
Fat - 36Gb - Shared?
-------------------------
HDD = 300Gb Maxator ATA
-------------------------

I do not know what to install first, windows or linux. After that how would I set up my swap, and my shared partition.

I also want to know what is swap, and I want to know how I can set up my Fat32 as a shared partiton.

Please someone guide me through this, I am not computer illiterate, I just have never messed with my partitions or setting up a dual boot.

-Thanks Guys,
          James Little ;)

---

### Post by merlinus on 2007-06-27
Install windows first.  Then this is an excellent guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You will not need more than 1.5G for /swap, and both os'es will be able to read and write to and from the FAT partition.

-merlin

---

### Post by Lamez on 2007-06-27
Looks great, but will it go ahead and setup swap, and my shared partition?

Thanks, this really helped!

---

### Post by merlinus on 2007-06-27
There will be options when you reach the partitioning menu.  Do not format your windows nor fat32 partitions, only the ubuntu one(s), as ext3.

swap will more or less take care of itself, once you select the size.

You may also wish to set up a /home partition, which will make saving most of your settings and configurations easy when upgrading to a new version.

-merlin

---

### Post by Lamez on 2007-06-27
when I get to the partition menu, I will select the first option. 

This will do everything for me right?

I am not good with partitions at all.

---

### Post by Irony on 2007-06-27
During your windows install (which you should do first, also put it in the first partition) you can very easily set up the partitions (it doesn't matter about them being non-linux).

Once they are set-up you can then install ubuntu.

---

### Post by maybeway36 on 2007-06-27
If you want a partitioning tool you can use GParted. Its probably best to make all the FAT32 partitions before you install Ubuntu; that way it will know they are there.

---

### Post by Lamez on 2007-06-28
Alright I did the first option (in Linux), and Linux was installed great, but when I try to boot into windows, I get a boot error ([COLOR="RoyalBlue"]The Blue Screen of Death[/COLOR]) I did have a great installation, and I even posted on the forums from windows, it all worked great untill I installed linux

Please help, I want to have both operating systems.

-Thanks,
     James Little

---

### Post by logos34 on 2007-06-28
boot from the windows install cd, hit 'r' for recovery console, then run 
chkdsk /r 

Hopefully that will fix any filesystem or partition table errors.

---

### Post by Lamez on 2007-06-28
ok I will give it a shot, but I have a off-topic quesion, do you have a WUSB54GC linux driver?

---

### Post by Lamez on 2007-06-28
Crap, that did not work, how would I manually partition the drive?

I just need to know how to mount them.

---

