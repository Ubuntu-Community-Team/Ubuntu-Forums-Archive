---
title: "GDM doesn't love ATI driver (or fglrxconfig)"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by gibbolo on 2005-11-27
Hi everyone.
I installed latest ATI driver for my mobility radeon X600 and all seemed to work fine. Then I run fglrxconfig as suggested on the ATI website. Because I didn't know very well the meaning of all those parameters, I left default values for most of them, except for resolution sequence: I changed the values from ("1280x1024" "1024x768" "640x480") to ("1400x1050" "1280x1024" "1024x768").
After rebooting I see the known list of services started (kernel boot, hardware check, ..., network configuration, ..., GDM start,...) and then, instead of the login screen expected, I see a complete black screen without any prompt or written.

I suppose I have to substitute the xorg.conf but I don't know how because I have no terminal access!!

I tried Ctrl/Alt/Backspace and Ctrl/Alt/+ but nothing happened.
Please, help me!

---

### Post by bwog on 2005-11-27
In this thread [http://www.ubuntuforums.org/showthread.php?t=89370&highlight=vesa+drivers](http://www.ubuntuforums.org/showthread.php?t=89370&highlight=vesa+drivers)
I saw this

at grub hit Esc and boot recovery
sudo dpkg-reconfigure xserver-xorg
this will bring up a graphical wizard which helps change the settings

A little Knowledge is a dangerous thing, boy am I learning the hard way

In case that helps and you have a gui back (eg with the Vesa drivers); go to the Custimization section for a howto install ATI drivers (not to the ATI website).

---

### Post by gibbolo on 2005-11-28
ok... the problem is quite harder...
weeks ago I commented the lines with "boot recovery" from my menu.lst and now I can't see that option in my grub menu...

how can I modify the "standard boot" option, so that I can boot in recovery mode?

Thank you... I'm nervous because without my ubby!

---

### Post by bwog on 2005-11-29
It would somewhat like this 

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

with your root and root=/dev/? and your kernel.

---

### Post by gibbolo on 2005-11-30
YEAH!
That works!!
Now I try with the instructions dpkg-etc....

Thanks a lot for the moment

---

### Post by gibbolo on 2005-12-03
Yabbadabbadooo! I did it!

After I changed the comand line to boot in "recovery mode", I run dpkg-reconfig xserver-xorg; but something went wrong and my ubuntu can't start xserver correctly.
In /etc/X11 I found these three files ordered by decreasing date: xorg.conf, xorg.conf_20051130, xorg.conf_old

I supposed the first file was created by "dpkg-reconfig...", the second was created by ATI driver, and the third was created by first ubuntu installation.... And I was right! So i renamed xorg.conf in xorg.conf_notworking and also I renamed xorg.conf_old in xorg.conf.
Then I followed the Ati driver installation guide suggested by bwog, and now my X600 works properly.

Thank you Bwog!

---

