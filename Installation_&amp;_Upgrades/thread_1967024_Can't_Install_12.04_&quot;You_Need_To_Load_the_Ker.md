---
title: "Can't Install 12.04: &quot;You Need To Load the Kernel First...&quot;"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-04-27
12.04 64-bit is failing to install here off a CD.  I am getting the same "You need to load the kernel first" error that I reported here:[http://ubuntuforums.org/showthread.php?t=1964065](http://ubuntuforums.org/showthread.php?t=1964065) about Beta2.

Here's what happens: I insert the CD newly burned on a Mac, and hit reset. It boots into the CD and I see the "Try or Install" menu.  Selecting either option, the drive spins up for about 15 seconds, goes quiet, and then I see this:

"error: couldn't read file"
 "You need to load the kernel first...Press a key to continue" 

If I press a key, it returns to the original "Try or Install" menu.  If I don't, it returns by itself. At that point, pressing F-10 to boot, or any other key, has no effect. The machine appears to be locked up.

I have tried editing the Grub options.  Nothing has an impact. 

I have verified, on  multiple CD's, that the iso burned correctly and that the kernels are, in fact, where grub thinks they are.

The install routines on CD's of other distributions work.  Only Ubuntu 12.04 does this. Repeatedly.

Has anyone else seen this?  Is there a fix?  I followed through the beta cycle and now, when I want to do a clean install, it's frustrating to get this error over and over.

---

### Post by buzzingrobot on 2012-04-27
Well, the USB stick seems to be working. I partitioned my drives manually and I noticed the USB showed up in the list. Took me a second to realize what the 8004 mb drive was.

Anyway, thanks for the reminder about the usb.

---

### Post by fbreve on 2012-05-22
I have the same problem here. So I wonder if you already got a solution.

---

### Post by buzzingrobot on 2012-05-22
> **fbreve said:**
> I have the same problem here. So I wonder if you already got a solution.

I used a USB stick.  Someone suggested the iso image is too big for a CD.  That's true, and I hadn't noticed.  While it's just under 700 megs on Ubuntu's server, it's more than 730 megs here once downloaded.  Still, I burned it on a DVD and got the same result.

---

### Post by fbreve on 2012-05-22
Thank you.

I've also tried both a CD and a DVD with the same problem.

I'll try with an USB stick.

---

