---
title: "GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by CheeseAndToast on 2010-10-03
Hi all

I upgraded from 10.04 to 10.04.1 via the update manager.
Now i get a error message on startup everytime confused:

"Ubuntu is running in low graphics mode" error and had to reconfigure to default settings to get back into Ubuntu. 

When i do alt+ctrl+f7 i get following:
glib-warning getpwuid_r failed due to unknown user id 0
From googling the error - its a bug, but users are getting this intermittently, i can't even sign in.  :(

I have a HP compaq nx8220  - ATI MOBILITY RADEON X600 graphics controller 

What can i do to login?

---

### Post by mörgæs on 2010-10-04
One can not upgrade from 10.04.0 to 10.04.1. The .1-release is only meant to describe that a new CD is released, which includes all bug fixes as of the release day. This is always done for the long time releases.

If you have installed 10.04 from its birth, you will have applied the bug fixes gradually during the time, so it is not a 'step up'.

It is a difficult error message to deal with. There is no simple solution, as can be seen in
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

There are a number of recommendations in the thread which may work for you depending on your hardware. If everything else fails, go for 9.10.


LATER EDIT: As can be seen in post 168 in the thread, a bug fix has now been released.

---

### Post by CheeseAndToast on 2010-10-10
Help required!!! :confused:

> **mörgæs said:**
> 

There are a number of recommendations in the thread which may work for you depending on your hardware. If everything else fails, go for 9.10.

Thanks for the reply.  I've given up on fixing - i have very little knowledge and very little time :(

How do downgrade or reinstall without loosing data?

Thanks

---

### Post by mörgæs on 2010-10-10
It is all explained here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

You could also wait a few days and try 10.10.

---

### Post by owen_cook on 2010-10-10
well I just tried installing a unr 10.10 on a desktop from a usb stick.

It boots up, select language, the select either install or try and it hangs

Press Esc and the message is as per subject

I will try find a laptop to test, but my gut feeling after reading these threads is that it too will fail.

---

### Post by mörgæs on 2010-10-11
If the same error appears, please post in the other thread. Best is to have all discussions in the same place.

---

### Post by CheeseAndToast on 2010-10-12
Unfortunately i dont have any drives to back up my data!! :(

The Live Cd (10.10) works as did the old version (10.04)
What i tried was shrink the existing partition which freed up 30ish GB. I want to be able to mount my old prtition, take off what i need and then fresh install! I  Installed the new version on this 30GB parition and rebooted.......

BUT

Got the same error as before.  However it seems its booting from the orginal install.  How do i boot from the new installation?

Thanks

---

### Post by mörgæs on 2010-10-12
If you run ```
sudo update-grub
``` you should get a list of all kernels available.

---

### Post by CheeseAndToast on 2010-10-12
> **mörgæs said:**
> If you run ```
sudo update-grub
``` you should get a list of all kernels available.

Which mode do i do this in?

Edit - booted the live cd, CTRL+ALT+F1, mount /dev/sda6 /mnt, sudo chroot /
root@ubuntu:/ sudo grub-update

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by owen_cook on 2010-10-12
Well, trying 10.10 unr on an eeepc-701 - No problems
trying 10.10 unr on an eeepc-1005 - That Error message flashes up on screen and then it proceeds to normal operation

Next stage is to do an install.

Looks like unr and "high end" desktops weren't meant to mix.

Only user comment I have is that the side bar is maybe a retrograde step from the 10.04 version, which was the coolest desktop I have ever seen.

---

### Post by mörgæs on 2010-10-12
> **CheeseAndToast said:**
> Which mode do i do this in?

Edit - booted the live cd, CTRL+ALT+F1, mount /dev/sda6 /mnt, sudo chroot /
root@ubuntu:/ sudo grub-update

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Just do it in a normal boot, not in a live session.

---

### Post by CheeseAndToast on 2010-10-16
I've given up!! :(  Gonna wipe and reinstall 10.10.

How do i access my hard drive via live CD so that i can access my home folder?

I can access my hard drive via Live cd, but cant access my home folder, Error: you do noty have permissions necessary to view the contents of "HOMEFOLDER".

However i can access other users folders - any way round this?

I plan to copy all files to my PS3.  Need to find a way to connect my laptop via usb or network cable- is this possible?

Thanka

---

### Post by mörgæs on 2010-10-16
This is not a bad idea. A clean install solves a lot of problems. 

However, this particular error is hard to handle, and though a reinstall is the best you can do, it is not a guarantee that it will solve the problem completely. Let us know if there still are problems after the reinstall.

If you can not access files from the hard drive when booting from a CD, you can give yourself root powers with the command

```
 gksudo nautilus
``` 

Beware that you can make a lot of damage to a system being root, so take care!

---

### Post by CheeseAndToast on 2010-10-17
I tried ```
gksudo nautilus
```

it worked, but when i go to my home profile i only had two files in the folder:
Readme.txt and Access-your-private-data.desktop


When i double click Access-your-private-data.desktop i get the follow error message:

Untrusted Application launcher
The application launcher "Access-your-private-data.desktop" has not been marked as trusted.  If you do not know the source of this file, launching it may be unsafe.


When I open readme.txt:

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
"access your private data"

or

From the command line, run ecryptfs-mount-private

I run ecryptfs-mount-private and got the following error:
Error: Encrypted private directory is not setup properly

How can I access it?

---

### Post by mörgæs on 2010-10-17
Sorry, I don't know how to handle an encrypted /home.

---

### Post by CheeseAndToast on 2010-10-17
If i was to wipe it all, could I recover files?

---

### Post by Kinkke on 2010-10-18
Try USB stick and got the same problems.. it's frozen
my download unr 10.10 by torrents, specs: axioo netbook intel atom n270, ram 1 gb, hd 250 gb, usb flashdisk transcend 2 gb,.

---

### Post by mörgæs on 2010-10-18
Did the ISO check with the MD5 values? 

Did you create the USB stick using the latest Unetbootin?
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Does it work in 10.04?

---

### Post by w.reidlinger on 2010-10-18
installed ubuntu 10.10 with kde

when i reboot or suspend the notebook got the error and i have to switch of by killswitch.

*********************************************************************
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
*********************************************************************

found a workaround for this problem.
open a shell > sudo -s > to become root > set a passwort for the root user with > passwd root > reboot.

when i suspend now i got the message anyway but only for two seconds and the suspend really words. so when i wake up the book again i works well.


not a 100% solution but a workaround!
trie out and let me know if it works.

---

### Post by bjnueva8623 on 2010-12-31
> **w.reidlinger said:**
> installed ubuntu 10.10 with kde

when i reboot or suspend the notebook got the error and i have to switch of by killswitch.

*********************************************************************
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
*********************************************************************

found a workaround for this problem.
**open a shell > sudo -s > to become root > set a passwort for the root user with > passwd root > reboot.**

when i suspend now i got the message anyway but only for two seconds and the suspend really words. so when i wake up the book again i works well.


not a 100% solution but a workaround!
trie out and let me know if it works.


Hey w.riedlinger, can you instruct me how to do this?

---

### Post by mörgæs on 2011-01-01
It is not recommended to create a root user in Ubuntu.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Besides, there has been a bug fix released now.

---

### Post by flutte on 2011-04-13
Hi,

I started to get this error during the boot of an industry-PC from a USB-stick, when I was fiddling with the reboot= command-line to the kernel in Ubuntu 10.10.

It turned out, that the reboot= option actually affected the boot as well for some reason. In my case, the PC reports "00:02.0 VGA compatible controller: Intel Corporation 945GME Express Integrated Graphics Controller (rev 03)" and "00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)".

For me, booting without any reboot= option worked, as did reboot=pci, but not reboot=bios.

/Fredrik Lundström
Sr Software Designer, Prevas AB

---

