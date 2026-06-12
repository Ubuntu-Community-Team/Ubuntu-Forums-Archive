---
title: "Graphics card stops working after upgrade from Dapper to Edgy"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by Purple Sheep on 2007-09-03
Hi,

I wanted to upgrade from Dapper Drake to Fiesty Fawn, so I (foolishly) did a Google search rather than checking the official Ubuntu documentation, or these forums. It brought me to [this page](http://urbanpuddle.com/articles/2007/05/23/upgrade-from-ubuntu-dapper-or-edgy-to-feisty-fawn), and I followed the instructions, which were, for the first stage:
```
apt-get update
apt-get dist-upgrade
sed -e 's/\dapper/ edgy/g' -i /etc/apt/sources.list
apt-get update
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
reboot
apt-get dist-upgrade
reboot
```
So presumably my system is now Edgy rather than Dapper. However, after the second reboot, the X-server failed to start. I got a message saying:
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? Yes/No
And when Ubuntu starts up, it fails to load graphics card drivers, giving this message:
> /etc/rcS.d/STOudev: line 64: /sbin/udevplug: No such file or directory

I'm guessing the problem must be due to the fact that I recently replaced my old Radeon 7000 with a Radeon 9550. Ubuntu still functioned as it always had done without me having to do anything, so I assumed the new graphics card was set up correctly and that Ubuntu had automatically downloaded the right drivers or something. However, it seems now that the system still thinks I have a Radeon 7000 (that's what it says in xorg.conf, anyway).

Can anyone please tell me how to set up X to work with a Radeon 9550, from bash? Or solve my problem in any other way, if I've got it all wrong.

(I'm posting this from a completely different computer.)

---

### Post by Pumalite on 2007-09-03
At the command line: (or Ctrl+Alt+F1):
sudo dpkg-reconfigure xserver-xorg. Accept most defaults, choose 'vesa' as you driver. Then: startx

---

### Post by Purple Sheep on 2007-09-03
The screen flickers and then I get the following:
> Fatal server error: failed to initialize core devices
XIO: fatal error 104 (Connection reset by peer) on X server "0.0" after 0 requests (0 known processed) with 0 events remaining.
Having the driver as "ati" which is selected by default doesn't work either.

---

### Post by Pumalite on 2007-09-03
If you have an xserver problem, what are those errors doing there? Looks like you have a connection problem Did you choose 'vesa'. Finishing re-configuration should have brought you back to command line. Can you give more details of what you did?

---

### Post by Purple Sheep on 2007-09-03
Finishing the configuration did go back to the command line, but then I typed "startx" as you said.

I've just tried again, doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```
Autodetect video hardware: yes
Graphics card driver: vesa
Graphics card identifier: ATI Technologies, Inc. RV350 AS Radeon 9600 (the card is actually 9550 but that's what it said by default)
Kernel framebuffer device interface: yes
X.Org server modules to be run by default: bitmap, ddc, dri, extmod, freetype, glx, int10, type1, vbe
Monitor: Studioworks 57i
Video modes used: 1280x1024
Monitor size: Up to 14 inches
Write monitor sync ranges to a configuration file: yes
Colour depth: 24 bit
```
startx
```

The screen flickers for a bit and then I get a load of error messages finishing with the one I gave you.

---

### Post by Pumalite on 2007-09-03
Say 'no' to kernelbuffer

---

### Post by Purple Sheep on 2007-09-03
It makes no difference.

---

### Post by Pumalite on 2007-09-03
I'm stumped then. Someone that knows better will chime in. Patience.

---

### Post by Purple Sheep on 2007-09-03
Well, thanks for trying. I've just seen [this thread](http://ubuntuforums.org/showthread.php?t=187177) and tried it with the driver as "vga", but still no luck.

Edit: OK, I've got it to work - I just did "dpkg --configure -a" and I am now on Firefox in Gnome with 640x480 resolution. I guess it was all because I didn't do the update properly.

Now I have a new problem: when I click the software updates icon, I get the following message:
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
When I run "sudo apt-get install -f" I get the following:
> Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.17-12-386_2.6.17.1-12.40_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix this, and how do I now get my graphics card working properly?

Edit 2: OK, after reading various other threads and documentation pages I think I've solved everything now.

---

### Post by Pumalite on 2007-09-03
Good for you. You are ahead of the crowd!

---

### Post by ContextualFabric on 2008-05-27
My solution was to go to /etc/X11 and find out that the original xorg.conf was replace by a new one. The original was renamed xorg.conf.6003627282 (some number). I renamed the xorg.conf to xorg.conf.bk and renamed the xorg.conf.6003627282 to xorg.conf (sudo mv xorg.cong xorg.conf.bk, sudo mv xorg.cong.6* xorg.conf)
Then I did startx and all was well.
Apparently the update installed a new xorg.conf, but fortunately created a backup of the original one.

---

