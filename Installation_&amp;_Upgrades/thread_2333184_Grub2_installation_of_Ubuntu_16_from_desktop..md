---
title: "Grub2 installation of Ubuntu 16 from desktop."
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by dragon5611 on 2016-08-07
I have a major issue.My boot files are moved into a file named temp boot next to boot. However,  I do not know how to use grub in order to move and register them back to boot. Also I wanted to know what commands I can use in grub to boot instead off of a. Iso file on my desktop. I do not have a live CD or jump drive to work with. It all must be through grub command at start. I have seen it is possible.

---

### Post by dragon5611 on 2016-08-08
grub> ls (hd0,1)/ lost+found/ bin/ boot/ cdrom/ dev/ etc/ home/ lib/ media/ mnt/ opt/ proc/ root/ run/ sbin/ srv/ sys/ tmp/ usr/ var/ vmlinuz cdrom/ vmlinuz.old initrd.img initrd.img.old temp boot/     how do I make grub boot from temp boot/ (where all my boot files are) instead of boot/

---

### Post by dragon5611 on 2016-08-09
Very helpful,  I'm just going to make a repair usb.

---

### Post by yancek on 2016-08-09
> I have a major issue.My boot files are moved into a file named temp boot 

The problem with your 'temp boot' directory is that it has a space in it so it will be looking for a directory named temp.  If you look at the Grub Manual page below, you see a list of available commands.  Note that cp, mv and mount are not among them and you would need at least two of those.   Unless you are just experimenting on a test machine, it is not a good idea to move boot files.

Booting an iso directly from an installed system partition is not a problem with a number of different Linux systems.  The link below has an explanation and some examples of boot entries in grub.cfg.

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by dragon5611 on 2016-08-11
Appreciate that. Had a lot if headache trying to use a Google chrome book to download what I needed. However, none of it compiled correctly in Windows xp for the usb boot.

---

### Post by dragon5611 on 2016-08-15
Problem solved. I did a bit of Reading up on grub. When you have a file name with spaces you must use ("these")"temp boot" I just edit the boot menu and it worked. Appreciate the help.

---

