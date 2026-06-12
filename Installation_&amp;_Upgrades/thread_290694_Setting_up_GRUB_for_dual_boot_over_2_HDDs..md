---
title: "Setting up GRUB for dual boot over 2 HDDs."
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Yorper on 2006-11-01
Ok heres my deal. I use Dapper which boots from my SATA HDD, after experiancing troubles with wine and some of my games i decided to throw a new HDD into my pc to load windows, having a dual boot system, windows for my few games and linux for everything else.

The HDD ive installed is a 20GB ATA. Now my problem is this, i cant for the life of me get GRUB to boot the windows xp installation from the ATA HDD.

I've added the following to to my menu.lst file....


title Windows XP Pro
root (hd1,0)
savedefault
makeactive
chainloader +1

but that throws up an error when i try to select it in my grub menu (something about unknown partition 0x7 if i remember corectly). I'll be honest with you, im not really sure what i was doing, ive searched the web and found a few instructions i tried, all of which failed miserably.

If anyone could tell me what i need to do to update grub booting from my SATA drive to add a working boot option for windows xp which is on my ATA drive, id be very grateful.

Oh i also modified my device.map so that hd1 was linked to /dev/hda, though i must repeat, im confussed about what i must do.

I hope ive been clear and thanks in advance for any help given.

---

### Post by BLTicklemonster on 2006-11-01
Okay, from what I keep hearing, you must have windows as your master drive, and ubuntu as the slave.

This would cause you some major rewrite problems in grub, but suffice it to say, windows would be on 

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

and ubuntu would be on 

title        Ubuntu, kernel 2.6.15-27-386
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/???? ro quiet splash
initrd        /boot/initrd.img- 2.6.15-27-386
savedefault
boot


Which is to say that you could either put windows in as master and reload ubuntu, or put windows in as master and try editing grub to reflect this change. 

I will not advise you to do either one, though, I'm just letting you know that usually, you will want to add ubuntu to a windows set up not vice versa. But I really don't see why editing grub won't work as well.

Good luck.

---

### Post by confused57 on 2006-11-01
> **Yorper said:**
> Ok heres my deal. I use Dapper which boots from my SATA HDD, after experiancing troubles with wine and some of my games i decided to throw a new HDD into my pc to load windows, having a dual boot system, windows for my few games and linux for everything else.

The HDD ive installed is a 20GB ATA. Now my problem is this, i cant for the life of me get GRUB to boot the windows xp installation from the ATA HDD.

I've added the following to to my menu.lst file....


title Windows XP Pro
root (hd1,0)
savedefault
makeactive
chainloader +1

but that throws up an error when i try to select it in my grub menu (something about unknown partition 0x7 if i remember corectly). I'll be honest with you, im not really sure what i was doing, ive searched the web and found a few instructions i tried, all of which failed miserably.

If anyone could tell me what i need to do to update grub booting from my SATA drive to add a working boot option for windows xp which is on my ATA drive, id be very grateful.

Oh i also modified my device.map so that hd1 was linked to /dev/hda, though i must repeat, im confussed about what i must do.

I hope ive been clear and thanks in advance for any help given.

You could try adding a mapping command to your Windows entry:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

If this doesn't work, open a terminal, and post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

---

### Post by Yorper on 2006-11-02
Thanks to both of you for a fast reply.

To BLTicklemonster, unfortunately your method didnt work for me, but thanks for the suggestion.:) 

To confused57, your method worked perfectly for me, so thankyou very much for the help. :D


Now i can play my games without the headaches cedega and wine gave me :cool: Once again thankyou to everyone for the help.

---

