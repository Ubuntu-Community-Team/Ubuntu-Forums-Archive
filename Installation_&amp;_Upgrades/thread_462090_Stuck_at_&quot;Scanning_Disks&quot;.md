---
title: "Stuck at &quot;Scanning Disks&quot;"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by krendar on 2007-06-02
Hi,

I tried to install Ubuntu 7.04 on my PC, but it got stuck at exactly 46% done. I first thought it was the few scratches I saw on the disk.

But now I am trying the same with a Kubuntu 7.04 disk and it get stuck at exactly same location (46%).

I wonder if anybody got any idea how I could pinpoint the problem and its solution?

Hardware:
Core2 Duo E6420
Asus P5B Deluxe Motherboard
SATA Disk Hitachi H7K250 (or something similar, think thats the name)

---

### Post by Gagle on 2007-06-02
Well, are you considering a dual boot setup ?  If so, before installing Feisty, log in your Windows account and Defrag the disk.  Once that is done, open a terminal/command prompt and issue this command 
```
chkdsk -f 
```

The -f option is very important.  It means it will fix errors on the drive. If the command detects error, you will be asked if it is OK to run the command at startup, before the drive is mounted, to fix the errors.  
Respond positively...

I advice you to run the chkdsk -f command twice.

From there try again and let us know what happens .  ;)

hope it helps,

gagle

---

### Post by krendar on 2007-06-02
> **Gagle said:**
> 
I advice you to run the chkdsk -f command twice.

From there try again and let us know what happens .  ;)


I don't currently have windows installed, this will be a fresh linux install without dual-boot.

I tried "fsck" but was not sure if it needed any parameters. Here is the result I got:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: clean, 11/30539776 files, 973477/61049000 blocks

---

### Post by Gagle on 2007-06-02
I doubt your hardware is to blame.  Try buning the Feisty Fawn DVD using slower speed.  If that doesn't work, try the alternate CD or the text install.

Hope it help,

Gagle

---

### Post by krendar on 2007-06-02
Solved!

I had to look at the Debian forum to find a solution. It turned out that it got stuck because my iPod was connected to its USB cable and this confuses the installer (both on Debian and (K)Ubuntu apparently)

---

