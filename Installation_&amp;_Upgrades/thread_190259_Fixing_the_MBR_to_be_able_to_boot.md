---
title: "Fixing the MBR to be able to boot?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-06
Well, I tried installing once, and it froze on the install for GRUB.  So, I started it again, and that time it got through perfectly.  Then, when I went to reboot, I got the dreaded "Error loading operating system" message.  How do I fix it?  It's a dual boot with Win XP and Ubuntu.  Please help!  I can't use my computer now.  :-(

---

### Post by linuchsan on 2006-06-06
this question has been answered many times. search the forum for mbr.

---

### Post by confused57 on 2006-06-06
If you have the Windows installation CD, you can boot up with it inserted in your CD drive...press "r" for recovery, then enter   fixmbr     , this will repair the Windows mbr, so you can boot into Windows, at least.

---

### Post by oliwally on 2006-06-06
> Well, I tried installing once, and it froze on the install for GRUB. So, I started it again, and that time it got through perfectly. Then, when I went to reboot, I got the dreaded "Error loading operating system" message. How do I fix it? It's a dual boot with Win XP and Ubuntu. Please help! I can't use my computer now.

I've had this problem once and was able to fix it, although the suggestion below doesn't always seem to work for some reason - I've had occasions when it failed. But give it a go.

In short I did this:

Chuck in your Windows install CD. Replacing the Windows MBR with the Windows CD is done after setup runs. There is a choice ("R") to enter the Recovery mode. When you get to the command prompt, it's >fixmbr.

I got this information from [this thread]("http://ubuntuforums.org/showthread.php?t=43528") at post 7.

Making a boot floppy as instructed in that thread is also good.

There are also some other suggestions there. Hope it helps.

---

