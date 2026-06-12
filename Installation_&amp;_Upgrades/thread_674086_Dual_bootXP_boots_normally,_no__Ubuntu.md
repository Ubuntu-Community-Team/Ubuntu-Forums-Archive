---
title: "Dual boot:XP boots normally, no  Ubuntu"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by spzed on 2008-01-21
HI 
I can't find a thread exactly the same as this ,hence the new one.

I loaded up Ubuntu on the same hard drive as XP, except that XP starts as normal. I don't get any error messages. No invitation to choose OSs.

Background:
I've got two hard drives: the 80gb master is boot dead(ie stopped booting windows- that's why I want Ubuntu!) but can be viewed from XP on the other drive. Ubuntu on the my live cd will view the files too.
The drive with XP and Ubuntu  is 160gb reduced to 100gb partition for XP.50gb for Ubuntu. This is the slave drive , but set to boot .

I may have done something bonkers when partitioning as it had to be manual: it wouldn't let me be guided. Think I used ext3 .

I tried making a supergrub disc to boot from but nothing happened. Then again I was confronted by a huge list of supergrub versions and hadn't a clue which one to use.Tried sgd_0.9654.iso

XP ran disc checker(I think) on restart.No problems.

Motherboard:Asus K8V-xSE /AMD X86 2002mhz

You've probably guessed I'm a newbie: well I am! I do want escape windows. Any offers?

---

### Post by torgrot on 2008-01-21
Well that dead drive is the problem.  Ubuntu installed grub to its MBR in all probablity.  What is the boot order in your BIOS?  Try changing the boot order to boot off the dead drive.  If it isn't to badly hosed it probably will start grub and give you the option to boot any of the OS's installed.

torgrot

---

### Post by spzed on 2008-01-21
Thanks torgrot I'm now replying from my Ubuntu installation!!

One question though. How can I get rid of my dead drive? Or *is* it dead? Perhaps just got corrupted.
It didn't give me much of a chance to choose OSs . Is this normal? Then it loaded Ubuntu .

Anyway , result!!

spzed

---

### Post by torgrot on 2008-01-21
You can edit /boot/grub/menu.lst and change the timeout.  I have mine set to 10 seconds.  Type this in a terminal window ```

gksu gedit /boot/grub/menu.lst

```
It will prompt you for your password, type it in and find the this line:
# (normally the first entry defined).
timeout		10
The number after timeout is the delay in seconds before it boots the default operating system.  Change it to however long you want to wait.

torgrot

---

