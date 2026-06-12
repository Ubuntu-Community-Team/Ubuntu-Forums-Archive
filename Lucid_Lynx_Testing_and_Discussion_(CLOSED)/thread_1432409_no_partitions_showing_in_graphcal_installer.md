---
title: "no partitions showing in graphcal installer"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gregh on 2010-03-17
When I try to do a graphical install the partitioner does not show any existing partitions and all the buttons are greyed out so I cannot create new ones.

The alternate install show the partitions just fine

Anyone seen this? I searched the forums and found errors with the partitions during installation but node where they did not show at all.

-G

---

### Post by VMC on 2010-03-17
Which ISO, todays, yesterdays. Are you using LiveCd, USB?

I just installed from todays Mar17th, daily-live and ubiquity works fine.

---

### Post by gregh on 2010-03-17
Sorry, it i sthe March 17th one.
It boots in live desktop and works fine, just the install/partition thing

---

### Post by cariboo on 2010-03-17
I've had the problem on my system since Lucid testing started. I'm currently running Lucid on an external USB drive, I have Karmic on my main drive. The system is a pure Sata, both hard drive and DVD R/W.

I haven't bothered with it yet as every once in a while, I've had to fall back to Karmic when a problem came up in Lucid.

I have a similar system, same motherboard, different cpu and ram, with an IDE Hard drive and DVD R/W and a Sata drive. I recently reinstalled using last Friday's daily build, the partitions on both drives were detected with no problem.

---

### Post by ronacc on 2010-03-17
the partitioner for lucid has been fouled up from the start , I have a mixed ide/sata system , the partitions are detected ok but it absolutely refuses to install grub anywhere except the MBR of HDA , I bugged that back on nov 21 09 .

---

### Post by VMC on 2010-03-17
Yes, I only use one HD and it is SATA or IDE never both. My BIOS doesn't know what to do with it, and I haven't taken the time to research it. 

there's been a few topics on problems using mixed technologies.
I don't even fill up the one HD I have installed.

---

### Post by ronacc on 2010-03-17
I had some problems with a mixed system back during edgy testing but that was a kernel issue not a bios one . dapper didn't have the problem neither did fiesty or other distro's unless they also used that kernel .I haven't had that kind of a problem since , the current problem I am having with the installer did not exist in karmic .

---

### Post by gregh on 2010-03-18
My setup is one large disk (SATA) with 3 partitions, so not too unusual
I seem to remember that 9.04 also did this and I needed to install from the alternative disk

---

### Post by VMC on 2010-03-18
> **gregh said:**
> My setup is one large disk (SATA) with 3 partitions, so not too unusual
I seem to remember that 9.04 also did this and I needed to install from the alternative disk

That is very strange. Never had that happen to me.

Here's what you can do. Boot up using the Try first, then open a terminal or Alt+F2, and put in '*ubiquity -d*' then the installer will start. 

When you get to the part that is grayed out open nautilus and view '*/var/log/installer/debug*' go to the bottom and check for any messages that may shed some light on this.

If that doesn't reveal anything of interest, then check '*/var/log/syslog*' and see if it has any tel tail signs.

---

### Post by executorvs on 2010-03-18
I encountered it with this morning's 64bit live disc image on my thumb-drive while re-OSing my Acer timeline 5810T

---

### Post by gregh on 2010-03-18
I have collected the install.log (attached) and a screenshot of the blank ubiquity applet

I will also open a bug report

-G

---

### Post by VMC on 2010-03-18
> **gregh said:**
> I have collected the install.log (attached) and a screenshot of the blank ubiquity applet

I will also open a bug report

-G
I noticed that partman has a lot of doesn't exist outputs in your install.log.

Also try booting the Livecd and after you get a desktop, see if "Places" shows any partitions.

---

### Post by gregh on 2010-03-18
Booting with live cd shows all partitions, I can even browse the files on the partitions easily. 
It's only ubiquity that has the error

---

