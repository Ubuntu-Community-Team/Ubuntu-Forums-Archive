---
title: "ati hd 4330: how to install fglrx driver?"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by giorsat on 2010-04-22
Hi . I have a packard bell easynote with a ati hd 4330 video card . I installed lucid 64 bit and the open source driver seems unstable. It changes resolution at each reboot. So I tried the fglrx driver. But at reboot all I get is a black screen even if I ggive the nomodeset at boot. Any idea how to make the closed source driver work?

---

### Post by clhsharky on 2010-04-22
HI

The OSS driver is more stable than fglrx.

What cat driver exacting, and how did you try to install it?

The only fglrx driver that works in Lucid is in the repos.

Sharky

This should help.

Ubuntu Gets Another ATI Catalyst Driver Handout 
[http://ubuntuforums.org/showthread.php?t=1434064](http://ubuntuforums.org/showthread.php?t=1434064)

> Originally Posted by jngrim  
i couldn't get it to work either for HD3200 so did the following:

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics, ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

---

### Post by giorsat on 2010-04-22
I used the hardware driver section in administration.... then it says to reboot but it doesn't work

---

### Post by BrokeMahPC on 2010-04-22
Before you reboot try:
```
sudo aticonfig --initial -f
```
works for me - have had to use it after driver updates too.
It will back up the original xorg and write a new one.

---

