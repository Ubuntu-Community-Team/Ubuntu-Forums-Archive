---
title: "Upgrade to Natty via USB stick - dual boot now error with grub"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by The Wagster on 2011-11-01
Hi everyone,

I finally got around to upgrading from Karmic to Natty on my dual boot (with XP) computer.  I have 2 hard drives; one for windows and one for Ubuntu.  I formatted the ubuntu hard drive and installed Natty from clean using the USB stick installer method.  Now when I reboot I get an error and the boot stops before grub loads and so I can't boot into windows or ubuntu.

The error message appears as:

> Grub Loading Stage1.5.


Grub Loading, please wait
Error 15

How can I fix this?  I do not know if I was using grub 1 or grub 2 or how I could tell!

Thanks for your help.

Wagster

---

### Post by Grenage on 2011-11-01
I'm going to assume that the PC is still booting from same drive (probably Windows drive), and that Grub is there but can no longer find the Ubuntu installation.  When you reformatted and reinstalled Ubuntu on the second drive, you probably installed a new copy of Grub there.

If you change your BIOS boot order so that it boots from the *second* drive, what happens?

---

### Post by ashickur.noor on 2011-11-01
Try to restore the grub using live cd.

---

### Post by The Wagster on 2011-11-01
Thanks for the swift replies.

Unfortunately my BIOS only has one option for Hard Drive so I can't tell it to boot from the other drive!

How would I go about restoring grub?  I've searched but only found guides for after reinstalling windows, not Ubuntu!  And there's different methods for grub 1 and grub 2.

---

### Post by ashickur.noor on 2011-11-01
There are plenty of ways to restore grub. See [here]("http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+restore+grub+of+Ubuntu+11.04&ie=utf-8&oe=utf-8") all are for live cd. You are using Ubuntu 11.04 and it contains grub 2.

---

### Post by The Wagster on 2011-11-01
Thanks everyone.  I've got it working now!:D

---

