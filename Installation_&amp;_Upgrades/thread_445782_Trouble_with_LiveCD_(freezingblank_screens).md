---
title: "Trouble with LiveCD (freezing/blank screens)"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by justin66 on 2007-05-16
Hey, I'm quite nooby with linux so please forgive me if I'm just doing something stupid here lol.
OK, I've been experimenting with a few different distributions and I currently have PCLinuxOS installed. I like Ubuntu because of its large community, ease of use and technical support. Either way I used to have Ubuntu 5 or something installed on my PC (no hiccups) so I decided I'd give the new version (7.04) a go. When I insert the LiveCD i select the first option to install/run. I get the loading screen for a few seconds, but when the bar is full the screen blanks out and the drive stops spinning. If I reboot the computer and try again it goes all the way and Ubuntu loads. However every time I try to actually install the OS from the desktop, the wizard freezes at one point or another. My disc has no errors (its my third one lol) and my PC should be fine, I've run several other distros including an older Ubuntu on it before. I'd appreciate any assistance with this problem, as I'd really love to have Ubuntu installed. Thanks in advance.

---

### Post by justin66 on 2007-05-16
Also if this helps i tried running Firefox in live cd to post here but the screen blanked out and lots of funny grey distortions ran across the screen.

---

### Post by gwoodard on 2007-05-16
How much memory do you have if you have less than 256mb then you need an alternate installer

---

### Post by justin66 on 2007-05-17
I got a gig of memory so I don't think thats the problem...

---

### Post by Topsiho on 2007-05-17
If you look around in this forum you'll find many people have trouble booting or installing from the LiveCD, which did not happen with those of the previous versions of Ubuntu.

You could try the alternate CD instead, which worked fine with me :), it has a different installer.

Topsiho

---

### Post by justin66 on 2007-05-17
I'll download and try the alternate cd then. I'll post back here if it works or not, or if I find another solution in the meantime. Thanks

---

### Post by justin66 on 2007-05-17
OK I downloaded the alternate CD, installed Ubuntu with no apparant problems. Rebooted, GRUB loaded followed by the Ubuntu bootsplash. The bar reached the end and my screen flickered with no input. When it came back on again there was just a black screen. None of the drives were spinning and I couldn't get any further. (Trust me to be awkward lol)

---

### Post by Blackforge on 2007-05-17
> **justin66 said:**
> OK I downloaded the alternate CD, installed Ubuntu with no apparant problems. Rebooted, GRUB loaded followed by the Ubuntu bootsplash. The bar reached the end and my screen flickered with no input. When it came back on again there was just a black screen. None of the drives were spinning and I couldn't get any further. (Trust me to be awkward lol)

What kind of graphics card do you have?  If its an nVidia or ATI, the drivers that Ubuntu comes with have been a pain for everyone...

---

### Post by Topsiho on 2007-05-18
I have got an nvidia graphics card, without trouble (with the nv driver).

But I think indeed that your graphics card is somehow not recognized with the correct settings, and so nothing is displayed and the screen is black.

Try and boot in rescue mode and see what your /etc/X11/xorg.conf file says. Mine says in the pertinent section:

Section "Device"
  identifier "Generic Video Card"
  boardname "RIVA TNT2"
  busid "PCI:0:6:0"
  driver "nvidia"
  screen 0
  vendorname "RIVA"
EndSection


in which you can see that I now use the driver from nvidia, which I installed afterwards, with no apparent benefit :)

Also the section about the monitor should be looked at, mine is:

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1024x768 @ 60 Hz"
  HorizSync 31.5-48.5
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsy
nc
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  gamma 1.0
EndSection

I am sorry I can not give you more advise on this, but maybe things are so obvious that you don't need it :)

Topsiho

---

### Post by justin66 on 2007-05-18
My graphics card is a somewhat dated ATi Radeon 9550 - the 256MB edition if that makes any difference - and I will try the rescue mode thingy shortly...

Just out of interest as well, I booted into the live CD again earlier without the blank screens etc this time. But when I got to the desktop it froze then sort of whited out, like an overexposed photo. I duno if that sheds any light on the subject...

---

### Post by Topsiho on 2007-05-19
Did you have a look at this:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Who knows you'll find the solution for your problem here :)

Topsiho

---

### Post by justin66 on 2007-05-19
Oooh... I use fglrx on all the other distros I tried... so it does not come with the Ubuntu CD?
By the way, total noob question here, how do I get to the command prompt to use apt-get when I can't boot into linux?

---

### Post by eapache on 2007-05-19
In the LiveCD boot menu press F6 to edit the boot options at the bottom. Remove quiet and splash, and add break=bottom. Halfway through boot this should bring up a cmd prompt.

---

### Post by justin66 on 2007-05-20
Okies, followed your instructions on the live CD
When I got to a prompt i got this:

/bin/sh: can't access tty: job control turned off
(initramfs):_

I tried to do apt-get but I was presented with:

error while loading shared libraries: libpam.so.0 cannot open shared object file: No such file or directory

Sorry for being such a pain lol

---

### Post by eapache on 2007-05-20
The infamous 'can't access tty, job control turned off' error. This has so many different causes that it's impossible to give fixed instructions for solving it. Search the forums for it and try various suggestions. Sorry I can't be of more help.

---

### Post by justin66 on 2007-05-20
I will, thanks. Ubuntu had better be good :P

---

### Post by eapache on 2007-05-20
It is :)

---

### Post by Topsiho on 2007-05-21
Ubuntu is really great. I use it from the first edition, Warty Warthog, 4.10, and fell in love with it, after having tried many other distributions, such as Red Hat, Fedora, Mandrake (now Mandriva) and Linspire/Freespire, and some other ones.

But alas, the installer on the live CD of the latest version, Feisty Fawn, 7.04 appears to have a bug which makes it impossible to use it on some PC's. How many (in percentage) I don't know, and I have read somewhere that it has something to do with that the developers have tried to make the boot process faster by having things done in parallel. Which means, I guess that timing problems may occur where a process expects the results of a previous process, which, however, is not there yet, as it is in an other thread ...

The Alternate CD has an other installer, and on my computer has done it's job perfectly, where the live CD gave the same results as you got with it.

The Alternate CD does not make it possible to first give Ubuntu a try before deciding to install, but you cannot get everything I guess :) Just install it, you won't regret.

Topsiho

---

