---
title: "Installation problems (no video output)"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by thekaempfer on 2007-01-21
I've been attempting to install ubuntu for quite a while now, downloading new releases and seeing if they had the same problem. At first when I tried to install ubuntu something failed outright, and it wouldn't even start the installer. A few versions later (edgy) I was able to get to the installer, but once it started the monitor would cut off and put up a "no video signal" message.

My computer:
Intel Core 2 Duo (E6400)
ATI Radeon X1800 GTO
Corsair 2GB RAM (DDR800)
Samsung 250 GB HDD (2 partitions, 180 and 70)
Motherboard Gigabyte P965/G965 chipset Rev C1

I've tried installing from a CD twice and I've attempted using the new windows installer a few times.

---

### Post by montgoss on 2007-01-21
It sounds very similar to a problem I had, although with completely different hardware.  The similarity may be how new/powerful your video card is.  Do you have two monitors hooked up?  Mine would do the same thing if I had two monitors plugged in.

I think even with only one monitor hooked up, I stilled had the error.  The way I got around it was to hit F4 at the Ubuntu LiveCD boot menu.  F4 brings up a resolution list.  I picked 1024x768x32 and then selected the first boot menu option.  None of the other resolutions worked for me, not even the lower ones like 800x600x32.   Have you tried any of the F4 options?

---

### Post by thekaempfer on 2007-01-21
I'll try that and edit this post with my results...

The install failed. I booted from the CD, tried my resolution at 1024x768 (32), 1024x768 (16), and 640x400 (32). They all went to the.. beige loading screen with the ubuntu logo, then showed a blinking cursor in the top left corner on a black background. After that the video cuts off, but I can hear ubuntu's startup noise.

One extra detail: My monitor is a HANNS-G 19" **widescreen** LCD monitor using DVI. It's native resolution is 1440x900.

---

### Post by ice2257 on 2007-01-23
I am having the same problem. One monitor hooked to my PC. I have a NVIDIA GeForce 6600 LE video card and as soon as I hit install my monitor switches into No Video Mode. Any help would be greatly appreciated.

---

### Post by AAM on 2007-02-09
TheKeampfer,

I have been trying to install the Eft on a machine with 1440x900 monitor since it came out and NO GO! My graphics card is old (ATI Radeon 9600). I can install Dapper using the safe graphics option. Upgrading to 6.10 broke the system.

I have a couple of suggestions to make that I haven't tried so far. You will need a working LiveCD (?Mepis seems to do the trick for me!)

1. Install 6.06 with your present screen attached and configure to get hardware acceleration working.
2. Install 6.10 with another screen attached. then configure the xorg.conf file to match the settings and identifiers in Dapper once you have hardware acceleration working.
3. reboot and have the new screen attached.

Will it work? I don't know but nothing else has come close for me.

---

### Post by cieje on 2007-02-13
I have an x1800xl and a 1440x900 lcd and had a freaking hell of a time getting it working with 6.10 over the weekend. I couldn't for the life of me get the vesa driver; it simply would not work.

Off of a live cd/dvd disc I was able to change the parameters (f6 I believe) and take "quiet splash" out and put break=bottom in.

By doing this, before xserver started or anything I'd get a prompt so I could:

chroot /root nano /etc/X11/xorg.conf

that way I could edit the display etc. Of course, like I said I couldn't get it to work with vesa, radeon, or ati, so this eventually didn't work. However, it could for some people. Also, after doing that, and allowing install to continue it would halt eventually. At that point I was able to do ctrl + alt + f1 to get the console up, but I couldn't get much further myself.

-----------

What I did was get the "alternate" install cd, so I could do a text based install. I did that, and the video still didn't work, but I could boot into recovery/console mode (selecting it in GRUB) and do:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

and after, to configure:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

I also had to:

sudo nano /etc/X11/xorg.conf

and add/change the resolutions to add in 1440x900 for my desired color depth. 

I still don't have direct rendering working, but my 2d video is fine, so I'll fiddle with it tonight. I think I have to symblink the dri folder:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/

hopefully some of this info helped...

---

