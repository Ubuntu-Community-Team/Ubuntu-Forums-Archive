---
title: "Failed"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by martintremblay on 2010-05-27
Good day folks,

I need to determine which package is causing every upgrade installation or removal of software to **fail**  ](*,) in Ubuntu 10.04
****
I have had a problem since allowing some non-supported upgrades (not certain what they were for) in 9.10 (FAIL!)

I hoped that upgrade to 10.04 would resolve the issue (I know FAIL again!) ](*,).

I am guessing I can;
a) Remove the offending package
b) Repair the missing/damaged 10.04 files
c) replace the 10.04 OS

any suggestions on the easiest path? 

I am running a dual boot one drive system with XP and Ubuntu each in their own partition and a 3rd partition where data resides

---

### Post by martintremblay on 2010-05-27
Here is an example of the error that occurs when I try to install 3D Chess from Ubuntu Software Center:


installArchives() failed: Selecting previously deselected package xaw3dg.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 195240 files and directories currently installed.)
Unpacking xaw3dg (from .../xaw3dg_1.5+E-17build1_i386.deb) ...
Selecting previously deselected package 3dchess.
Unpacking 3dchess (from .../3dchess_0.8.1-16_i386.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up memtest86+ (4.00-2ubuntu3) ...
/etc/default/grub: 9: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu6) ...
No apport report written because the error message indicates its a followup error from a previous failure.
/etc/default/grub: 9: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up xaw3dg (1.5+E-17build1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already

Setting up 3dchess (0.8.1-16) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-generic
 linux-generic
Setting up memtest86+ (4.00-2ubuntu3) ...
/etc/default/grub: 9: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu6) ...
/etc/default/grub: 9: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

---

### Post by martintremblay on 2010-06-04
Found the solution to this problem.

My Grub file contained incorrect quotation marks.

by removing the ” and replacing with " in the following line in GRUB: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
has corrected the error.

---

### Post by hansdown on 2010-06-04
Nice work martintremblay.

I just saw your thread.

---

### Post by Krantarin on 2010-06-09
I have had what seems to be the same problem, but being not half as adept as martintremblay, I have no idea how to fix it (even with the information in the above thread). I see lots of different files when I search "grub" and I can't even tell the difference between &#8221; and ".

Edit: I've realized my problem is very different from martin's, and it was a mistake of me to post here.

---

### Post by tropdoug on 2010-06-17
I also have had this problem, but when I followed your suggestion Martin and then did ```
sudo update-grub
``` I got ```
/etc/grub.d/10_linux: 121: done uname: not found
```any ideas as there doesn't seem to be anything on the net about this error

---

### Post by martintremblay on 2010-06-18
> **tropdoug said:**
> I also have had this problem, but when I followed your suggestion Martin and then did ```
sudo update-grub
``` I got ```
/etc/grub.d/10_linux: 121: done uname: not found
```any ideas as there doesn't seem to be anything on the net about this error


Hmmm
When you boot does GRUB initialize as expected?
If yes, you potentially have a package and/or file conflict.

These commands will completely uninstall and reinstall GRUB2.
Do this  while booted into Lucid:

```

     sudo mv /boot/grub /boot/grub_OLD 

``````

sudo mkdir /boot/grub 

``````

sudo apt-get --purge remove grub2 

``````
sudo apt-get --purge remove grub-pc 

``````

sudo apt-get --purge remove grub-common 

``````

sudo apt-get install grub-pc 

``````

sudo update-grub 

``````

sudo grub-install /dev/sda 

```Then reboot.

---

### Post by tropdoug on 2010-06-21
Martin your a genius

I did all as you posted, a lot of errors during the remove operations but I held my nerve and continued. The re install and configuring of grub went without a hitch and with bated breath I re booted, Bingo straight into the system and I immediately went to Synaptic and installed a program and this time no errors, All went as it's supposed to. 

Obviously you knew how to fix it, but if it's not too much trouble do you know what the cause of the errors were?

---

### Post by martintremblay on 2010-06-21
This issue was caused on my machine by a script that someone developed (It was from some online forum, but exactly where I am unsure) 

This script was supposed to improve the video graphics performance (video playback performance) of my laptop

Unfortunately it did not help my graphics performance, and through about 2 months of forum research I determined that this script caused software updates to fail. I tried to locate the original script to warn others of this script, but I have been unable to relocate.

I can't take all the credit for the GRUB repair, it was something I learned how to do from elsewhere in these forums! But basically you are un-installing any instance of GRUB and reinstalling GRUB2, which should repair pretty much any unresolvable issues with GRUB

---

### Post by Huzudra on 2010-07-17
> **martintremblay said:**
> Found the solution to this problem.

My Grub file contained incorrect quotation marks.

by removing the ” and replacing with " in the following line in GRUB: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
has corrected the error.

call me a moron, what exactly is the difference between *"* and "? I mean I can't make a *"* unless I press ctrl+I to make it Italics.  I don't mean 'whats the difference between italics and regular font' I mean in GRUB/Linux, whats the difference?

---

