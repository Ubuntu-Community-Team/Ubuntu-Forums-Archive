---
title: "Problems after upgrading to 16.04"
date: 2016-05-18
forum: Installation &amp; Upgrades
---

### Post by tchangu on 2016-05-18
Hi. I upgraded my installation from 15.10 to 16.04 yesterday and it has been nothing but pain. First when I got stuck, I was able to TTM (CTRL + ALT + F1) into terminal. Then from this forum "solved" instructions did the following
(1) [COLOR=#111111][FONT=Consolas]sudo apt-get purge nvidia-*
(2) [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:graphics-drivers/ppa
(3) [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo apt-get install nvidia-364

[/FONT][/COLOR]But 364 didn't work and so used 361 based on instructions from another forum. That worked but then now I have run into another debilitating issue. I CANT even get to my TTM. The screen is flashing and it feels like it is stuck in infinite loop. I fall into terminal using ctrl + alt + f1, and within seconds the screen refreshes and it is gone. The refresh is happens within couple of seconds.  I tried to update GRUB parameter by adding [COLOR=#111111][FONT=Consolas]nouveau.modeset=0 and nomodeset [/FONT][/COLOR]and nothing worked. Stuck in the infinite flashing loop.

Help please...

I have a LENOVO machine and didnt not think upgrading will land me in big trouble. I have about 6 months worth of work (unfortunately not backed up) sitting there behind the flashing screen.

---

### Post by grahammechanical on 2016-05-18
You could try opening the Advanced Option for Ubuntu sub-menu at the Grub boot menu. Then select a kernel with recovery mode. At the recovery menu select resume. That may get you to a working desktop using a fallback open source video driver. Then you can change video drivers at System Settings>Software & Updates>Additional Drivers tab.

The graphic-drivers PPA provides early access to the very latest Nvidia drivers. These are drivers that are not had sufficient testing to be available through Additional Drivers. Some times the very, very latest drivers may solve a problem, especially if we have the very, very latest video hardware. But those kind of video drivers can bring their own problems.

If you wish to purge that Nvidia driver, then you can do so from the recovery menu. Select Root shell prompt and run the purge nvidia command again. You may need to put the file system into read/write mode. You can do that by first running Network. That will establish an internet connection and put the file system into read/write mode at the same time.

To find out what drivers are recommended for your video hardware run

```
ubuntu-drivers devices
```

To install the current Nvidia driver for that hardware run

```
ubuntu-drivers autoinstall
```

Myself, I would get the OS loading & shutting down a few times with the open source video driver before experimenting further with proprietary video drivers. Your situation is one reason why I recommend reverting to the open source video driver before upgrading to a new version of Ubuntu.

Regards.

---

### Post by tchangu on 2016-05-18
Thanks for your response... I had tried that as well (i.e. pick recovery option, select resume) but the end result seems to be the same (I end up with flashing screen that doesnt allow me to even TTM and key in my user id/password...) I now think I will have to remove the nvidia drivers for sure and i seem to have no away to get to a terminal. When I pick the root option, I am asked for a password and I dont know if I ever set up a root password. So that seems to be a dead end too.

Can I install 15.10 brand new and not lose my data. Is there anyway i could log in using live USB and get access to the data? Help!

---

### Post by yancek on 2016-05-18
> When I pick the root option, I am asked for a password and I dont know if I ever set up a root password

You can't install Ubuntu without creating at least one user and that user (the first user created) has root access by default so use that user password.

If you want to recover data you can use a Live CD/flash drive.  Just boot it up, mount the partition(s) on which you have the data and copy it to another drive.

---

### Post by tchangu on 2016-05-18
Thank you for your response. There is only one user and the the password of that user doesn't work for the root user :( I am trying copying the data files over using live USB. If that works will try and reinstall Ubuntu all over. Wish I had known the upgrade is going to create so much headache and requires a PhD to solve... (lessons learned)...

---

### Post by EowynCarter on 2016-05-21
Let me try a guess. You bios is in UEFI with secure boot on ?

---

