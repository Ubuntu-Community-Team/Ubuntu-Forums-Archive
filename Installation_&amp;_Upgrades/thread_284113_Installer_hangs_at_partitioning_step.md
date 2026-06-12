---
title: "Installer hangs at partitioning step"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by pattymnaish on 2006-10-25
I have successfully partitioned my 80GB hard drive with the Linux System Rescue CD. I am currently running XP SP2 on my Dell Dimension 2400, which I wanted to dual boot with Ubuntu. I have 256MB of RAM, and a 2.8Ghz Pentium 4 processor.
 However, during the Ubuntu (6.06) install process, it suddenly freezes, and stops reading from my hard drive, and my CD drive. I then have to force-shutdown my PC.
 What I am wondering is, is there a compatibility issue with my PC or OS, or do I simply need more RAM? :-?

---

### Post by pattymnaish on 2006-10-25
Hmm. I'm going to try the alternate install cd.

---

### Post by pattymnaish on 2006-10-26
Whilst installing the "optional modules" in the text-mode installer, it suddenly switches to a black screen, with two white dots. On attempting to boot into Ubuntu, after force-shutting it down, it displays a white cursor on a black background. That's it.
 I have now done this twice, re-formatting the linux partition on my hard-drive inbetween. I have yet to check my CD for defects. Could this be the problem?

---

### Post by dvader on 2006-10-26
Installer hangs at partitioning step, It comes up with an error message saying there is no root. and will not install This has happened with the RC 1 as well   It should work as I am installing it over 6.06.1 which has / , home, and swap partitions 

any suggestions , this the master HD 'C" the slave has XP and 6.06 in a dual boot mode 

Dvader

---

### Post by oncemore on 2006-10-26
that's happening to me too :(

---

### Post by nick122147 on 2006-10-26
Happening to me too. The installer opens op a blank window from gparted, looking like it's trying to send a message, but the window is blank. Then I chose a swap and a root partition, but it doesn't let me go on, it's just saying no root partition selected, even thought I have marked sda1 as root /. I'm downloading the alternate cd now, hope tha one works better. 

The installer not working could really be a turn off for new ubuntu users..

Steinar

---

### Post by pattymnaish on 2006-10-27
My problem with the blank screen was referring to the alternate cd. I'm going to try re-burning the ISO at 24X rather than 48X.

---

### Post by pattymnaish on 2006-10-27
No joy. I still have the same issue. Anyone have any ideas?

---

### Post by PillowFightin on 2006-11-12
I'm having the same problem here--I'm trying to install 6.10 as dual-boot with the LiveCD on a Sony laptop, a PCG-GR370. I'm a newbie and have no clue what I'm supposed to do now.

---

### Post by marties on 2006-11-13
try alternate cd

---

### Post by cotcot on 2006-11-13
Install an older version (Breezy 5.10) and upgrade.

---

### Post by johnhenry on 2006-11-13
I found the same problem of "No root system" at first, but I find that this seems to happen when one has pre-created the partitions. If one allows Ubuntu to delete and then recreate the partition for the root / all seems to go according to plan thereafter. It does for me anyway;) 

Hope this helps

JohnHenry

---

### Post by johnhenry on 2006-11-13
I had the same problem at first. I had a partition ready and the system insisted there was no root system - in spite of the / in the box. I find the only way to overcome this is to let the Ubuntu installation process DELETE the prepared partition and recreate it. Then the system allows itself to put the root / in and accept it. It has worked has worked like that for me in 3 separate installations on 3 separate machines.

Hope this helps

johnhenry

---

### Post by johnhenry on 2006-11-13
Sorry about the duplication above. It seemed at first not to have accepted my first attempt. I am new to this forum.

jh

---

### Post by pattymnaish on 2006-11-13
Sorry, I forgot to say this was resolved. PillowFightin, try this guide: [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")

---

