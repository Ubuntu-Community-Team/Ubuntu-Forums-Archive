---
title: "Install of AMD64 7.04 fails"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Gazimoff on 2007-05-16
Hello there,

Firstly, apologies if this query has been answered already. I did some searching around, but I couldn't find a solution to this problem. 

I've created an installation CD for Ubuntu 7.04 and booted from it. I get to the menu screen asking me to select an installation method. I selected the first option  (Start Install) and watch while the installer starts to load. I*t gets to a screen where there's the Ubuntu loco in the centre, with a progress bar underneath. For a while, a yellow rectangle moves back and forth. After a while, the progress bar empties and begins to fill from left to right. About 15% in, the installation process freezes. It never progresses to the Ubuntu desktop screen to allow me to install the OS.

I'm using the following hardware:

Intel Core 2 Duo 6600
2GB Crucial Ballistix Tracer DDR2
Gigabyte GA-965-DS3P Motherboard
Gainward NVidia 7900GS 256MB
Seagate 250GB SATA-II HDD
Netgear WG311 802.11b/g 

Any ideas on what's causing this and how to work around it? I'm not familiar with Linux installation processes myself (especially tinkering under the hood), so any help would be much appreciated. Please let me know if you need any further information from me, or if there are any tests you'd like me to carry out

Thanks in advance!

---

### Post by godd4242 on 2007-05-16
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

Do me a favor and dig through this thread, if you haven't already.

It's not the same error, but perhaps if you try one of the work arounds that worked for them, you might be able to complete the install?

---

### Post by Gazimoff on 2007-05-17
Thanks for the link, unfortunately I've not been able to make it work as yet.

By removing the quiet and splash settings, I could watch the installer loading. It seems to get furthest with no additional options set. When using acpi=off or noacpi the installation fails much earlier. When using the break=top setting and entering in modprobe piix, there doesn't seem to be any change.

Some further information: I have the 250GB SATA drive plugged into the jmicron sata port on my motherboard. I also have a 80GB IDE drive on Primary Master and a DVD drive containing the Live CD as Primary Slave

Hope this is of help.

---

### Post by RoboRat on 2007-05-19
I have the same board but I'm using one of the yellow Intel sata ports for my hard drive.  Everything works great with this setup.  Is there a reason why you're not using the Intel sata ports or you just like purple? :)

---

### Post by Gazimoff on 2007-05-19
Thanks for the tip, it helped!

I moved my drive from the JSATAII0 connection (purple) that used the jmicron chip to the SATAII0 connector (uses the Intel chip) and the installation progressed further. The only other thing I could think of that might have been causing problems is the Netgear WG311 card, which I disabled in Windows because it was caudsing problems at bootup. Removed the card, and Feisty boots without problems and I get the installation screen!

Now all I have to do is work out how to either resize my windows partition on the sata drive and we're home and dry. i'll have a dig around though - I think there are some topics on that :)

---

### Post by Gazimoff on 2007-05-19
Resolved!

Everything's working as intended. I now have a dual boot Ubuntu/WinXP system. The main plus is that Ubuntu's running in 64-bit dual core, which is more than I can say for XP. Monitor is running at 1440x900 as well, which is nice.

Thanks all for the help, now to see what this OS can really do :)

---

