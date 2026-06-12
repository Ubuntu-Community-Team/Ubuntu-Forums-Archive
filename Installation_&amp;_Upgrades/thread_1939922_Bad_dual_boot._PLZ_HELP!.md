---
title: "Bad dual boot. PLZ HELP!"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by caspertk on 2012-03-12
Hi,
I got a new comp yesterday that came with windows 7 and I set up the dual boot with 11.10 today. Upon doing so, there was no GRUB menu, it just booted straight into windows. So I searched around and found a thread containing something I could do, but it backfired. So here is what I did after dual booting:

> Please boot from the live cd/usb and select "try Ubuntu" and when the desktop loads open up a terminal and copy/paste these commands in one at a time pressing enter after each one
Code:
sudo mount /dev/sda5 /mnt  
sudo grub-install --boot-directory=/mnt /dev/sda
This should report "Finished. No errors".
If it does, reboot and you should go straight into Ubuntu. If Ubuntu loads please open a terminal again and run
Code:
sudo update-grub
and watch the screen as grub.cfg is run. The Windows Loader should be recognised. If it is reboot and you should then get a grub menu giving you the choice of which operating system to boot.

Except it didn't boot back into Ubuntu. Instead it boots into a black screen like:

>   GNU GRUB version 1.99-12ubuntu5

  Minimal bash line editing is supported

grub>

Can somebody please tell me what to do or point me in the right direction. I appreciate anything you guys can do to help. Thanks!

---

### Post by darkod on 2012-03-12
That is only a default, general fix. First of all, you need to know whether sda5 is your ubuntu root partition or not.

Also, the grub config files might not have been installed properly since you never saw grub after installing ubuntu.

To make sure what you have and what is missing, run the boot info script from the link in my signature. Post the results as explained there. You can do all that from live mode.

---

### Post by caspertk on 2012-03-12
Ok somehow an (much!) older version of grub was included in the live CD I had. Purged it and re-installed the latest version of Grub, and now I'm good.

---

