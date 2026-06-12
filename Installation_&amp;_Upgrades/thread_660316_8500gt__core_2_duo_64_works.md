---
title: "8500gt  core 2 duo 64 works"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by modelmark on 2008-01-06
Finally got it working, with 64 bit blender installed and Yafray as renderer. No more running out of memory during the rendering of movies.
I had a lot of problems that I guess had to do with partitions not being healthy. (1 old disk that used to be bootable might have confused ubuntu)
So I split up a 200 G disk in a partition with some old windows stuff, followed by a 2G swap, a 20G root and the rest home partition (ext3). After this the installation was no problem (except for grub being on this disk also and I can't tell my bios to boot from this disk, so it goes straight into windows (this can be solved by leaving the live CD in, booting from CD and choosing first hard disk option)
I installed all the updates and then went on with the graphics card.

Don't install any kdm stuff yet
1. Download the driver to your desktop
2. Check that build-essentials are installed (if not you can install them with
sudo aptitude install build-essential
3. CTRL+ALT+F1 (to console)
4. sudo /etc/init.d/gdm stop (stop display manager)
5. cd Desktop (or where you have saved the driver)
6. sudo sh NVIDIA-Linux-x86-169.07.pkg1.run
(Now the NVIDIA installer asks to accept licence an other things you should accpet or say yes)
7. sudo gdm start (display manager again)

Now if you want twinview
sudo gedit /etc/X11/xorg.conf
go to the screen section and add

Option “TwinView”
Option “MetaModes” “1280×1024 1280×1024&#8243;

That should be it! Restart X with Ctrl+Alt+Backspace and you should have two screens. If the orientation of the screens is off, try this under the “Screen” heading…

Option “TwinViewOrientation” “LeftOf”

LeftOf can be LeftOf, RightOf, Below, Above, or Clone.

blender can simply be installed
sudo apt-get install blender
sudo apt-get install yafray
But you don't have the latest version of blender at the moment. I just downloaded the latest and copied it over the old files. That seemed to work.

Runs like a smile now

---

