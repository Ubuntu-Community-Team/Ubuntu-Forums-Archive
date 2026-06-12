---
title: "It will not boot!! ubuntu 9.10"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by rainingcats on 2009-11-14
hello,
 I am an absolute noobie with ubuntu and I recently installed ubuntu 9.10.
I turn on my computer, an acer aspire one, it goes to grub and I press enter on the ubuntu OS and it does nothing but take me to the blinking prompt and it stays there blinking to infinity! Windows XP svpk 3 works perfectly but i cannot even get into my ubuntu.
I would like to either remove the partition and reinstall it or be able to fix it now. I am concerned that if I delete the partition (if I can figure out how) that it will not boot windows xp because I have read that people have had these sort of problems.

---

### Post by aysiu on 2009-11-16
You need to use *fixmbr* to get the Windows boot loader back on:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

After that, I'd recommend using Wubi to set up a dual-boot with Windows:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by jimpr13 on 2009-11-16
maybe Wubi is to set a dual-boot but in that OS it's different and so i would recommend not deleting the partition because i had the same problem

---

### Post by audiomick on 2009-11-16
sounds like something is wrong with the X server. Maybe re-install ubuntu

---

### Post by sandwormblues on 2009-11-16
i've got a similar problem, and i've been using linux for a while.

I ran the full install, my machine reboots, and GRUB just sits there.  I hear no motion from my hard disk.  The install process installed the kernel, and installed GRUB, and grub can't find the kernel.  It says: "Grub loading.."  and does not boot.

I have a system76 gazv4 (AMI bios version I06201.004)

i'll boot from an alternate CD and check grub.CFG... *sigh*... because i have all the time in the world... sure wish i could afford a mac...

---

### Post by rainingcats on 2009-11-16
but I have already installed the partition for ubuntu how would I delete the partition and have all of my hard drive for windows to have both operating systems?

does fixmbr delete the other partitions?

---

### Post by rainingcats on 2009-11-25
Thank you for your help guys, but I am glad to say that ubuntu is now running on my laptop as it's own partition. I was lucky I accidentally fixed the problem by when grub loaded pressing the right arrow and ubuntu booted by chance but the mouse didn't work so I shut it down and rebooted ubuntu until it came up and worked. I plugged it into the internet modem and checked for updates. It downloaded them and my computer now works on ubuntu.

---

