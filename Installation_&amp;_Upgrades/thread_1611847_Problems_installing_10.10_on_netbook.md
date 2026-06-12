---
title: "Problems installing 10.10 on netbook"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by luismgl on 2010-11-02
So I tried to install ubuntu 10.10 netbook edition an my toshiba nb200 and after the first reboot more or less something like this appeared

```

modprobe: FATAL: could not load /lib/module/2.6.35-22-generic/ modules dep: no such file or directory

modprobe: FATAL: could not load /lib/module/2.6.35-22-generic/ modules dep: no such file or directory

gave up on waiting for root directory. common problems:
-boot args (cat/proc/cmd line)
-check rootdealy=(did the system wait long enough?)
-check root=(did the system wait for the right device?)
-missing modules (cat/proc/modules, ls/dev)

ALERT! /dev/disk/by-uuid/f786c992-1803-4d1c-b35c-acd1057df7ab does not exist.

Dropping to a shell!

BusyBox v1.15.3(ubuntu 1.1.15.3-1ubuntu5)buil-in shell(ash)
Eneter 'Help' for a list of built-in commands)

(initramfs)_

```

since its a netbook, I installed via pendrive.
help!

---

### Post by Quackers on 2010-11-02
Were these messages received when you were trying to reboot with the pendrive plugged in or out?

---

### Post by luismgl on 2010-11-02
happened in both situations.

---

### Post by Abir Valg on 2010-11-02
luismgl, this may not be related to your case, I had a problem installing 10.10 for netbooks. I used Unetbootin as described on ubuntu.com site. I can't recall now exactly whether I was dropped to BusyBox like yourself or whether I had a kernel panic.
I my particular case, the was no initrd.gz image in the /boot folder. Whether Unetbootin is a culprit or Ubuntu installer, I don't know. One thing I know is that this error happened when the disk I was installing 10.10 to had other partitions. Once I wiped the disk clean and install 10.10 by default to the whole partition the predicament vanished.
Is the ramdisk initrd.img-2.6.35-22-generic in the /boot directory of the newly installed 10.10?

---

### Post by luismgl on 2010-11-02
its a fresh format and I'm using the full partition. to make my flash drive bootable I used Universal-USB-Installer-1.8.0.8 -> [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I've tried 3x formatting and 2 different pens. all with different outcomes (the other 2 formates it froze somewhere in the system install part)

---

### Post by luismgl on 2010-11-03
anyone knows what to do?

---

### Post by luismgl on 2010-11-03
@ Abir valg I've tried unetbootin once, I'm now giving it another try. If this doesn't work I dunno what I will do :/
I know that the other solution would be an external dvd drive, but I don't own one nor I plan to.

---

### Post by luismgl on 2010-11-03
Again failure. I'm going to try another linux distro in the morning, going for jolicloud, will report later then :)

---

### Post by ubanksy on 2010-11-03
I believe those first 2 messages you see:

```
modprobe: FATAL: could not load /lib/module/2.6.35-22-generic/ modules dep: no such file or directory

```

are not the problem and can be ignored - I have a working 10.10 machine that started printing that after 10.10 upgrade (but it runs fine).  Suspect this will disappear in a few kernel upgrades time (google it).

Last USB based install I did, I had installation / boot problems (not your one exactly) but my resolution was to use a different USB stick.  I still don't know why.

---

### Post by luismgl on 2010-11-04
thank you for your reply ubansky :)
I actually tried 2 different pen drives, and one of them was new, I also tried 2 different software's that are said to work and nothing. Today I tried jolicloud with their own software to make the pen drive bootable and it worked like a charm! In fact I was surprised on how fast the whole process was. So as for now I'm sticking with this one.

---

### Post by luismgl on 2010-11-04
tried again, although this time I tried to install in a partition instead of using the full disk, I downloaded again ubuntu netbook 10.10, bought another usb stick and downloaded the latest version of the Universal USB installer and followed the instructions on the ubuntu site and the outcome was the same being with or without the pen :/

---

### Post by Hashiru on 2010-11-04
A workaround that might work is:
1. Install Plop bootmanager on usb stick 1
2. Install Ubuntu on usb stick 2
3. boot with usb stick one inserted
4. insert usb stick 2
5. choose boot from usb
6. see what happens

I haven't tested it, but you might want to try it.

---

### Post by luismgl on 2010-11-07
no luck here :(
will I have to buy an external cd drive after all?

---

