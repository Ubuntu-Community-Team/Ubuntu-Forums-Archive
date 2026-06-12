---
title: "Can't install Ubuntu 14.10 after GTX 970 installed"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by Hyper Tails on 2015-01-24
Hey guys.

I recently got a Nvidia Geforce GTX 970 SC, and after I installed it, it basically messed up my Ubuntu installation, for I couldn't get into the desktop and has a lower resolution. I tried to reinstall Ubuntu 14.10, but to add insult to injury, Sometimes I get stuck on a blank screen when trying to get into the live session, or installation. When I do get into the live desktop or installation, the installation always fails. When the live disc boots, I get a message saying "booting into insecure mode"

Any help will be thanks.

---

### Post by tokyobadger on 2015-01-24
You should boot the livecd with the "nomodeset" - when you first see the splash screen (purple with white keyboard and human symbols bottom centre) press F1 to get the advanced welcom screen. Press F6 then select nomodeset

Because your card is relatively new you will be better off installing the latest nvidia drivers from the xorg-edgers ppa. 

Try this first: After you have installed 14.10, boot into Ubuntu - the nouveau driver will be default and it may be displaying at the wrong resolution - if you can pull up the terminal enter the following:
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update 
sudo apt-get install nvidia-346
```

Try this next: You may have problems getting to a GUI environment, so you might need to edit the boot parameters in GRUB (temporarily - when GRUB menu shows, select the kernel you want to boot, press e and then remove the words "splash" and "quiet" and add "text". After booting to console, login as your user and then follow the step above to install nvidia-346

---

### Post by the3dman on 2015-01-25
Hopefully tokyobadger's info will work for you but if not.... Try a 14.04 Live CD/USB and see if you have the same issues. I recently had issues with my GTX 660ti and 14.10. After some recent updates I was not able to get to the desktop. I went back to 14.04 and the issues went away. I had some things going on at the time and did not look into what with 14.10 was causing it. When I have more time I will try 14.10 again...

---

### Post by Hyper Tails on 2015-01-25
I finally managed to get Ubuntu 14.10 installed with the drivers, but for some reason, when I go to login, after entering my password, the computer just freezes on the wallpaper with the "Ubuntu 14.10" logo on the bottom-left corner. Even pressing the reset button doesn't work, so I have to hold down the power button for a few seconds, or unplug it and plug it back in again. I do still manage to get into the Ubuntu Desktop, but this happens randomly, and I want it to be always.

---

### Post by efflandt on 2015-01-27
I have a GTX 750 Ti which also has a new Maxwell chip like the GTX 970. Using **nomodeset** boot parameter for a 64-bit 14.04.1 live/install iso somehow worked fine, even though I don't think nouveau supports it yet. But I could not get to a desktop on the installed system, and after I tried "apt-get install nvidia-current" from rescue boot, networking enabled, and root console, it was on old 304 version that does not support this card. So next boot I got as far a login, but could not get to a desktop. Once I purged nvidia-current and installed nvidia-331 I was finally able to boot normally.

So I would suggest using **nomodeset** boot parameter described by tokyobadger above when booting live/install iso (maybe for 14.04.1 for now). Then after install, boot to recovery selection in grub, enable networking from menu (just wait a while if it throws any errors for something it does not recognize), then select root terminal (or whatever it is called) from the menu and do this:```
apt-get update
apt-get install nvidia-331
```. Reboot and see if you can log into desktop. Then you can add the xorg-edgers ppa and install nvidia-346 as tokyobadger describes.

Once you have nvidia-346 installed if you want to try overclocking your card (which only works with 337 or newer drivers), boot into recovery to a root terminal and do:```
mount -o remount,rw /
nvidia-xconfig --cool-bits=12
```Then NVIDIA X Server Settings should have offsets for max gpu clock, and video RAM speed, and slider for optionally setting a specific fan speed (instead of automatic). This is easier for me to explain than stopping X to do nvidia-xconfig (since I forget how to do that exactly).

---

