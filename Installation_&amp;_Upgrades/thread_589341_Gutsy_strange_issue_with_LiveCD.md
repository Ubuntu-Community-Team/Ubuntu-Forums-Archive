---
title: "Gutsy strange issue with LiveCD"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by diavolo22 on 2007-10-24
Hello,

I've encountered strange problem with Gutsy LiveCD (386 as well as x64).
It's bootting normaly up to log screen. Automatic logon is taking place and then..
Wallpaper is displayed, for 1sec I can see gnome toolbars, but right after toolbars disappear, mouse & keyboard are frozen and only thing I can see is empty desktop with standard wallpaper.

I'm trying to run it on standard hp pc dx2250
AMD 64
Ram 512MB
integrated ATI X200
SATA hdd

There was no issues with 7.04

Please help

Diavolo

---

### Post by Sef on 2007-10-24
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the disk for errors?

---

### Post by diavolo22 on 2007-10-24
Yes CD's fine I've checked it but also I've burn 32bit as well as 64 and both are behaving in the same manner :(

---

### Post by pannerrammer on 2007-11-05
I've got the same problem with hp dx2250 and 7.10.

With 7.04 the live cd boots ok, but when I run the install it doesn't appear to see the WinXP installation (so I stopped as friend still needs xp!)

---

### Post by bulldog on 2007-11-05
> **pannerrammer said:**
> I've got the same problem with hp dx2250 and 7.10.

With 7.04 the live cd boots ok, but when I run the install it doesn't appear to see the WinXP installation (so I stopped as friend still needs xp!)
You can add your windows to the menu.lst manually.
All you need to know on which partition windows is installed [should be the first primary partition]
Also you should install ubuntu and use manual partitioning,otherwise there's a fair change you blow your windows from the hdd.

---

### Post by pannerrammer on 2007-11-05
Thanks bulldog.

I tried the alternate 7.10 x86 cd distro as it skips the live cd step. Installation was just like old times!

Successful ubuntu installation and winxp still there.

However, the original problem persists (ie. when I logon I get the top bar and then it gives up and shows the logon screen again).

Started in Recovery mode, logged in and then did sudo gdm. Comes up with login screen, and problem is still there.

Any ideas?

---

### Post by bulldog on 2007-11-05
Looks like a problem with your graphics.
You didn't install any graphics driver I suppose?
Try in the console```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will make  a new xorg.conf file and backup the old one.
Just choose the right driver and resolution for your graphics,ie if you didn't install any driver you should choose nv for nvidia cards,not sure which one to choose for ATI though,think vesa or something like that.

---

### Post by pannerrammer on 2007-11-05
HP's website identifies the built-in graphics as ATI Radeon X300

The -phigh flag didn't work for me (it copied xorg.conf but didn't run the reconfigure part), so I used 
```
sudo dpkg-reconfigure xserver-xorg
```This got me running at low-res 640x480, but loads of fiddling about didn't yield improvement.

I'm pretty sure the issue is what's being discussed in thread 569654, but they're mainly upgrading, so presumably haven't had the live cd problem. It's to do with the **fglrx** driver.

Here's what made it all work properly for me:

Enable fgrlx driver. To do this install linux-restricted-modules and restricted-manager provided in the restricted repositories:
```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```When I rebooted the system locked me out completely (blank screen), so need to reboot and select the "recovery mode" option.

At the command prompt login then type                                   ```
sudo aticonfig --initial
```

Reboot and it started in 1280x1024 mode with all the effects. The only minor glitch was that the "aticonfig"  command reset the keyboard to US, but that's easy to fix!

My only remaining problem is after the "Grub 1.5 message I get a "monitor out of range" synch problem until the gdm starts properly - and the same during shutdown - Any ideas how to make the boot/shutdown occur at lower res or  vga?

---

### Post by pannerrammer on 2007-11-06
...and I've cracked the boot/shutdown issue - it's the 'splash' option in grub:
```
sudo gedit /boot/grub/menu.lst
```Near the end you'll see an uncommented line ending "ro quiet splash". Delete the "splash", save, reboot. Alright, not as pretty, but I'm up and running!

**Note: Don't do the above! See my later posting for a fuller solution to the boot/shutdown issue**

---

### Post by bulldog on 2007-11-06
> **pannerrammer said:**
> ...and I've cracked the boot/shutdown issue - it's the 'splash' option in grub:
```
sudo gedit /boot/grub/menu.lst
```
Near the end you'll see an uncommented line ending "ro quiet splash". Delete the "splash", save, reboot. Alright, not as pretty, but I'm up and running!

You've been busy:) glad you got most things working :lolflag:

---

### Post by pannerrammer on 2007-11-07
> **pannerrammer said:**
> ...and I've cracked the boot/shutdown issue - it's the 'splash' option in grub:
```
sudo gedit /boot/grub/menu.lst
```Near the end you'll see an uncommented line ending "ro quiet splash". Delete the "splash", save, reboot. Alright, not as pretty, but I'm up and running!

**Note: Don't do the above! See my later posting for a fuller solution to the boot/shutdown issue**

The problem with the faulty splash screen is dealt with more fully here. Worked for me!
[INDENT][http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)[/INDENT]

---

