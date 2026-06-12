---
title: "Install not detecting XP when installing 7.10"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Jimes on 2008-02-03
The title pretty much says it all. When I install Ubuntu 7.10, the installation process doesn't recognize my Windows XP install, and doesn't install Grub for me >.<

I've installed Ubuntu about a dozen different times, on different computers, both as primary OS and dual booting with XP, but this is the first time I'm doing it with a SATA HDD.  I'm wondering if that's the problem.

I don't have anything setup as RAID or anything, since I dunno what that is.  Although everytime I boot up my motherboard it seems to want to make one.

---

### Post by taurus on 2008-02-03
Let's see if windows is even still on your machine.  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Jimes on 2008-02-03
Um, sorry I just got up, I should clarify my last message.

Windows boots fine, I can't get into Gutsy.

Installation of Gutsy through the live-disc goes fine, and it recognizes my windows accounts when the account import part comes by.  It doesn't give me anything saying it recognizes Windows is there past that, and doesn't mention Grub at all.

I popped the live-disc back in, and all my files seem to be on the 20GB partition, including Grub, and I checked menu.lst and it seems normal, to the best of my recollection.

---

### Post by froy02 on 2008-02-03
If Window$ is booting fine it means grub is not installed on the MBR of your your boot drive.  You say your menu.lst is fine.  Does that mean that you have an entry there that look something like this?

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
Also when you installed Gutsy was the order of boot drives the same in the bios as now?
Anyway if the installation went okay, here's a thread on how to install grub using a live CD. 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Make sure your Window$ drive is the first drive in the BIOS boot order.  While you're in the  BIOS section make sure RAID is disabled.

---

