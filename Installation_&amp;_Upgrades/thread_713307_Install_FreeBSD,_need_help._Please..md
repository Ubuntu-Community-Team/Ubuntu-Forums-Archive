---
title: "Install FreeBSD, need help. Please."
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Thieflock on 2008-03-02
I had my entire HDDR dedicated to Ubuntu. Yesterday I allocated enough space to install FreeBSD to run along side Ubuntu. After the installation configuration the system requires a reboot to install FreeBSD. FreeBSD isn't going into the install process after reboot. Instead it is going to the Ubuntu boot manager. So I am pretty sure the Ubuntu boot manager is overriding the FreeBSD install process. Any ideas?

---

### Post by scottro on 2008-03-02
During the FreeBSD installation, there was an option to install the FreeBSD manager or not.  

However, it's easier to use Grub to boot FreeBSD.  
Did you give FreeBSD a primary partition?  

If it has one, and say it was /dev/sda3, for example, you can try adding this to grub

title FreeBSD
root (hd0,2,a)
kernel /boot/loader

(0 for the first hard drive, 2 for the third partition).

You're probably better off using Grub to boot FreeBSD than using the FreeBSD boot manager.

---

### Post by Thieflock on 2008-03-02
Yes I did give FreeBSD its own partition. So how do I add it to the grub?

---

### Post by scottro on 2008-03-02
Open /boot/grub/menu.lst with your favorite text editor and try adding the lines I gave above.   (Changing the 0 and 2 to represent your own layout.)

In grub, sda1 is hd0, sda2 is hd1, etc.  The first partition is 0, second partition 1, etc.  So, the example I gave above would work if BSD is on sda3.  

(If it was on sda4, then you'd use hd0,3,a)

The a stays the same in any case.  

This should work. On occasion it doesn't.  If not, then you can use--again, assuming it's on the 3rd partition

rootnoverify (hd0,2)
chainloader +1

That's chainloader, a space, the plus sign, no space and the numeral one.

---

### Post by Thieflock on 2008-03-02
Thank you Scottro.

---

### Post by scottro on 2008-03-02
Glad to help.  I tend to use mental shorthand, so I'm sorry that the first post wasn't clear. 

Like anything else, once you know how to do it, it's easy.  :)
Before you know how to do it, it seems difficult.

---

