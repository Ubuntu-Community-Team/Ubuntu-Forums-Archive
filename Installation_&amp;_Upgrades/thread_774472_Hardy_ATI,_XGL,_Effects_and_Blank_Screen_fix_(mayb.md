---
title: "Hardy ATI, XGL, Effects and Blank Screen fix (maybe)"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by roolark on 2008-04-29
Okay, so like nearly half the people posting in this topic, I suffered from the ati graphics driver problems. The symptoms I experienced were:
1) Blank screen on bootup in normal mode. Could only boot in "recovery mode"
2) Could not get the ATI restricted driver, fglrx, to load and stay loaded.
3) 3D effects were disgustingly slow.

Hardware: ATI Radeon XPress 1100, ACER 5102WLMi laptop, AMD 64x2 (2 core)
OS Version: Upgrade from Gutsy to Hardy Ubuntu (not clean install)
Was Using for 3D: Compiz, XGL, ATI restricted flgrx driver. This worked in Gutsy.

How I fixed the problems above:

1) Booted into recovery mode
2) used synaptic package manager to do a "Complete Removal" of xserver-xgl
3) rebooted PC to recovery mode 
4) Pressed the "reload" button in synaptic package manager.
5) did a re-installation of xorg-driver-fglrx
6) I also installed the following (though this may not have been necessary): fglrx-control; fglrx-amdcccle
7) Went to System > Administration > Hardware Drivers, and selected to use "ATI restricted"
8) Rebooted PC into Recovery Mode.
9) Went to System > Administration > Hardware Drivers, the ati driver said "in use" but was not checked. Checked it
10) rebooted, normal mode. This took about 1 minute 15 seconds.

At this point, login and desktop displayed fine. Even better, my 3D effects are smooth, fast, and flawless. No more blank screen on boot, etc.

---

### Post by zemoffm on 2008-05-02
Worked for me on Gateway ml3109.  Tried installing fglrx with envyng, which caused the blank screen on bootup.  After I copied back a backup of xorg.conf, went in and uninstalled driver through envyng, then followed his steps.

Somehow, magically, it worked.

Also, I don't know if this is something new in the fglrx driver or hardy, but suspend now works with my ATI card!

Now that ATI driver works, I can safely say that hardy is amazing, and now a permanent switch from windows.

---

### Post by muecker on 2008-07-09
I think I just discovered how to fix this.  I did the following:
[LIST=1]
[*]Boot using the ati driver (not fglrx)
[*]Rename /etc/ati to /etc/ati/backup
[*]Install the envy drivers (may also work to reinstall xserver-xorg-fglrx)
[*]Blacklist the fglxrx driver in /etc/default/linux-restricted-modules-common
[*]Reboot
[/LIST]

The good news is I now have fglrx in use.  The bad news is GLX is provided by mesa.  I'm still working on that part.

---

### Post by olifhar on 2008-07-10
Thanks, this thread helped a lot, even though it took me a while to find. Compiz worked wonderfully for me until (I think) I accidentally interrupted Adept in the middle of an important update: afterwards, the blank screen. Simply reinstalling the display driver did the trick for me.

I am much happier now: I basically use Compiz for the transparency capabilities and the Scale plugin, because they make me much more productive.

---

### Post by old farmer on 2008-07-17
I also have the same problem with an acer laptop
I didnt have xserver-xgl installed but got distracted and removed the xserver.... and now im in trouble :O
When I boot back with recevery option, Im in a terminal screen, start x returns
'/etc/x11/x is not executable
giving up
no such file or directory (errno2): unable to connect to x server
no such process (errno 3) server error error'

is there a way to initiate synaptic pachage manager so I can correct this little mistake

thanks

---

### Post by old farmer on 2008-07-17
just downloaded the current version 8.04.1, and can boot to live session
does this help? Can I update my instalation from the cd?
or do I have to reinstall.....
thanks

---

### Post by muecker on 2008-07-18
> **old farmer said:**
> just downloaded the current version 8.04.1, and can boot to live session
does this help? Can I update my instalation from the cd?
or do I have to reinstall.....
thanks

You shouldn't need to use the CD to install the new drivers.  Just boot into safe mode, tell it to fix your X Server, reboot and install.  Alternately you can modify /etc/X11/xorg.conf and use the "ati" driver instead of "fglrx".

---

### Post by nickgaydos on 2008-08-03
I also have a Gateway ML3109 and it worked! Someone on Yahoo Answers told me it was a RAM problem...but I did the RAM check and no problems at all. But, I followed your steps and it worked!

---

### Post by ultrabatman on 2008-08-17
I had this problem and was unable to resolve it using Roolark's procedure.  After much fiddling and FRUSTRATION, I finally got the ATI proprietary driver to work in Ubuntu 8.04 as follows:
* Get the latest proprietary ATI driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
* Make sure Xorg isn't running.  It's possible that this actually isn't necessary, but I moved to ctrl-alt-f1 and did:
sudo /etc/init.d/gdm stop
Xorg was still running afterward, so I did kill -2 (pid) to get rid of it.
* Remove beryl and all things compiz if installed.  I was formerly using compiz, and though awesome, its presence really hindered this procedure.  You may end up with a white screen of death after login if you don't get rid of it before installing the ATI driver (happened to me).
* In a terminal, as root, execute the ATI driver installation file that you downloaded in the first step w/ the --buildpkg option (you may need to first resolve missing dependency issues):
sudo ./ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/8.04
If all goes well, the installer should create five new .deb files in the current directory
* Not entirely sure whether this is necessary, but before installing the new packages, I removed the following packages just in case:
sudo apt-get remove fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx xorg-driver-fglrx-dev
* Install the .deb packages created by the installer.  Again, you may need to resolve dependency issues as they arise:
dpkg -i fglrx-kernel-source_8.512-0ubuntu1_i386.deb
dpkg -i xorg-driver-fglrx_8.512-0ubuntu1_i386.deb
dpkg -i xorg-driver-fglrx-dev_8.512-0ubuntu1_i386.deb
dpkg -i fglrx-modaliases_8.512-0ubuntu1_i386.deb
dpkg -i fglrx-amdcccle_8.512-0ubuntu1_i386.deb
* Reboot, and everything should be fine.  If not, then I wish you luck...  =^p

---

### Post by sjondoe on 2008-08-21
That's weird:confused: For me beeing a Newbie with Ubuntu,
All I did was activate the ATI driver,then go to the package manager and 'install the Catalyst Control Center'. Once installed,
I've got it to work. Well that is if I didn't leave my first 17" monitor to display @ 2600x?? res. After reboot, that screen gives me the message "out of sync". But I hope to correct that when I'm back home.

---

