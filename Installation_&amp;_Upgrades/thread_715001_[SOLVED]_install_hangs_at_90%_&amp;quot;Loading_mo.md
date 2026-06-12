---
title: "[SOLVED] install hangs at 90% &amp;quot;Loading module 'usb-storage'&amp;quot;"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by alina.bolero on 2008-03-04
I have an HP Pavilion dv9700z that just won't install Ubuntu.
# uname -a
Linux ubuntu 2.6.24-8-generic #1 SMP Thu Feb 14 20:13:27 UTC 2008 x86_64 GNU/Linux

I've encountered this problem with both 7.10  and 8.04 Alpha 5.

It just hangs at "Detecting hardware, please wait ... 90%  Loading module 'usb-storage' for 'USB storage' ..."

My BIOS will not let me turn USB off.  Booting the liveCD with nousb did not help.

issuing an lsusb from the command line also just hangs.

nothing interesting in dmesg.

seems just like this:  [http://ubuntuforums.org/showthread.php?t=416424](http://ubuntuforums.org/showthread.php?t=416424)
and this kernel bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/132092](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/132092)

This notebook also hangs while booting the liveCDs while starting the bluetooth service.  However, I can kill -9 the init.d bluetooth service and it will continue booting.

If I could just get the damn thing installed I'd flush out the issues with USB later.

-Alina Bolero

---

### Post by jeffus_il on 2008-03-04
Any unnecessary usb devices plugged in?

---

### Post by alina.bolero on 2008-03-05
There is nothing USB plugged in at all.  If I could physically rip the USB controller out at this point I would!   lol

---

### Post by jeffus_il on 2008-03-05
An idea about the usb message, maybe the usb-storage modules succeeds, but what comes next hangs before displaying output. Can you do a lsmod to see if the usb-storage module is loaded. Can you try to disable bluetooth in the bios? Have you tried the alternate CD's text install?

---

### Post by alina.bolero on 2008-03-05
woohoo!  The alternate install worked without a single hickup!  I'm fully installed and up and running.

Thank you sooooooooo much!

:KS:KS:KS:KS:KS:KS

---

