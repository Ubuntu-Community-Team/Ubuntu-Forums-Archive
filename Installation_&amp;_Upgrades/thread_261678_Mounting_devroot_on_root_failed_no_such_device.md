---
title: "Mounting /dev/root on /root failed: no such device"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by kauf on 2006-09-20
I had some problems earlier and due help from various memebers I have gotten around them... however now I have some new issues that prevent me from using Ubuntu.

I have two harddrives: a 80 GB with windows installed (currently MIA due to LiveCD GRUB install messing up the MBR [will fix later]) and a 40 GB which I'm trying to run linux off.

I installed off the alternate CD and it completed without a hitch, I used LILO as opposed to GRUB this time... and I placed the boot record on the 40 GB.  I don't mind going into the BIOS to choose which OS to boot.

So, the BIOS is set to boot from the 40 GB, and LILO starts to boot Ubuntu parts of it load fast so I can't tell if there are more errors but I believe these to be the only ones (as follows)

mount: Mounting /dev/root on /root failed: no such device
mount: Mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on /root/sys failed: no such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

Those failed mounts all occur at the end, after which this comes up:

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for ------------ (unimportant - didn't write down):
/bin/sh: Can't access tty; job control turned off

I can enter commands, so hopefully there are some I can enter which will fix the mounting issues.  I don't want to go crawling back to Windows without Ubuntu up and running - please help me.

---

### Post by kauf on 2006-09-21
Come on someone, I'm stuck using the Live CD unless I make some windows recovery floppies off someone else's machine.

Maybe I should abandon dapper and wait for edgie to be released (not just through beta though).

---

### Post by kauf on 2006-09-22
I fixed it [not that anyone seems to care]!  Lol, I feel like such an idiot, but I had reasons for my choices.

So, when installing off the live CD GRUB messed up, or the whole thing did... whatever it didn't work.  So when I installed off the alternate CD I used LILO, I had also read someone state that it was better.

After all this time trying to figure out what to do, all I had to do was install with the alt. CD and GRUB.  Now everything is fine, windows is recognized yet I haven't tested it.  See no reason too, I GOT UBUNTU!

---

### Post by robio376 on 2006-09-22
I'm have the exact same problem your had earlier with the 
/root not found, no such device blah blah blah...

How did you fix it?

---

### Post by kauf on 2006-10-04
All I did to fix it was try to install the GRUB bootloader on my Windows (Master) HDD, using the Alternate CD (Install CD).  

I had tried a GRUB install (on windows/master HDD - and corrupted the boot process [leaving me only with the Live CD for my working OS]) with the Live CD but it messed up, most likely because the Live CD install doesn't really work for most users.  When I got the Alternate CD I first tried to use the LILO boot loader running off my Linux HDD, that didn't work though I did set the BIOS to boot off the slave HDD (to prevent the corrupted GRUB from interfering).  Then I as I started this post, I installed GRUB on the master and it work fine.  Can boot to either OS, it's sweet.

---

