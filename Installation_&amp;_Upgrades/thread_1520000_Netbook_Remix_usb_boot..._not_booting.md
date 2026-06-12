---
title: "Netbook Remix usb boot... not booting"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Cytota on 2010-06-29
I've tried (several times now) to create a bootable USB stick with ubuntu to use on my netbook.  I've removed my HDD from the boot order, just to not worry about it, but my system refuses to boot from a stick.  A windows 7 bootable will run just fine, but Ubuntu will not.  I tried Ubuntu 10.04 before, and had a similar problem, posted here and no one responded.  Now I'm trying it with Netbook Edition and getting nowhere.  Could someone help me out? :(

---

### Post by Capslock118 on 2010-06-29
Is your issue similar to mine in that [the PC freezes at boot time]("http://ubuntuforums.org/showthread.php?p=9521060#post9521060")?

I have not been able to figure this out yet either but I can keep you posted if I make any progress.

---

### Post by Cytota on 2010-06-29
It's either the case that it skis the bootable entirely or stays with a flashing "_" until I decide to turn the system off.  I can't get a bootable to work on that system, or my laptop, which actually has ubuntu 10.04 running.

Evidently I'm doing something wrong.  I've tried 3 flash drives and these two different systems... followed all instructions from multiple guides to the letter.

---

### Post by Capslock118 on 2010-06-29
What netbook do you have? acer? asus? dell? etc?

I feel this might be a long shot and I cannot test until later tonight but I'll be updating my BIOS in hopes that I can try to boot off of an SD card instead to see if that works.

The internet is implying that I can boot off an SD card with an updated bios. We shall see.

---

### Post by C.S.Cameron on 2010-06-29
Have you checked the MD5SUM of the iso?

---

### Post by Cytota on 2010-06-30
The ISO is good, as it works just fine from an actual optical disk.

I'm using and Asus ee pc 105hab.

---

### Post by Capslock118 on 2010-06-30
Cytota,

I found that using the wubi installer worked just fine for me. If that fits your needs you may want to try that.

---

### Post by Cytota on 2010-07-03
yknow... wubi wouldn't actually install it... I forgot the reason why, but it had some error. I'll have to try it again.  I think it had a problem trying to install a boot file...

---

### Post by hobocaver on 2010-07-03
Hi     I have installed UNR Lucid on an Asus 1201n-mk, it came w/o an OS, but did have a minimal system for internet. I tore my few hairs out for 3 days before I found a msg in these forums. It suggested that the program I was using to create the USB, Unetbootin, has had problems; it does not install the MBR [master boot record] to the USB. I then found a link, again in these forums, with a command to move the MBR to the stick; voila, I have been up and running for a week now. The command is like this   dd if/pathtoiso of /dev/sdb     Please understand, this is only an approximation of the command I found, but it solved my problem. Good hunting, that is how i found it. Timeframe would be a week ago or more.

---

### Post by Capslock118 on 2010-07-07
hobocaver,

Could you provide the link to the thread or web article you are referring to that told you how to resolve the issue?

That may solve Cytotas problem and mine as well :)

---

