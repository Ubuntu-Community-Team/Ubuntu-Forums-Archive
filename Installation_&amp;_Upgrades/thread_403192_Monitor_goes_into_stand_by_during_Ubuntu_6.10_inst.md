---
title: "Monitor goes into stand by during Ubuntu 6.10 installation."
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by DannyW on 2007-04-06
Hello, brand new to linux and certainly interested in giving it a go... I was hoping you could give me a hand on that.

Here goes... Downloaded Ubuntu 6.10 (Desktop Edition - amd64) today from the website. Cleared a small 10GB partition to try it out on untill I decide to get rid of Windows.

After booting from the CD I select 'Start or Install Ubuntu', then there is the black screen with a ubuntu logo and a loading bar and then after that my monitor stops receiving a signal and goes into standby mode.

I can hear a sound playing through the speakers however, so the system hasn't froze.

I've tried changing the resolution by pressing F4 before isntalling. I've tried starting in safe graphics mode. I've also tried this from the '[Bugs/AtiDriver]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")' help page. (I have ATI Radeon X800 with monitor: Dell 2407WFP)
> If you can't even boot the Desktop CD and/or install the system, see [bug #59618]("https://launchpad.net/bugs/59618") and [EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618") before anything else. You should be able to install using the "vesa" driver, and then go from there.

I then tried using 'radeon' instead of 'vesa'. No luck, the monitor still goes in to stand by. Any help would be greatly appreciated!

Please see my hardware summary below.
Thanks in advance!
Danny :)

**Belarc Advisor tells me:**
**Processor:**
2.20 gigahertz AMD Athlon 64
**Main Circuit Board:**
Board: ASUSTeK Computer Inc. A8V Deluxe Rev 1.xx
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. 1018.001 12/30/2005
**Memory Modules:**
3072 Megabytes Installed Memory
Slot 'DIMM0' has 512 MB (serial number SerNum0)
Slot 'DIMM1' has 512 MB
**Harddisks:**
Promise 1+0 Stripe/RAID0 SCSI Disk Device (300.08 GB) -- drive 3
Promise 1+0 Stripe/RAID0 SCSI Disk Device (203.92 GB) -- drive 2
ST3400620A ATA Device [Hard drive] (400.09 GB) -- drive 1
WDC WD800BB-00FRA0 ATA Device [Hard drive] (80.02 GB) -- drive 0
**Display:**
RADEON X800 Series [Display adapter]
RADEON X800 Series Secondary [Display adapter]
DELL 2407WFP [Monitor] (24.2"vis, s/n UY5456B138HS, October 2006)

---

### Post by DannyW on 2007-04-07
Update:

Burned Ubuntu Desktop 7.04 beta to disc and tried to install.

Monitor went straight into standby after hitting 'Start or Install Ubuntu'.

The only way to get it to start was to press F4 and change the mode to something else, for example 1600x1280/32 or 1024x768/32. Then I see the Ubuntu logo and the loading bar and Ubuntu then starts. The resolution once Ubuntu has started is 1024x768 and cannot be changed to the higher native resolution (or any other higher resolution for that matter, just 640x480, 800x600, 1024x768).

Now Ubuntu is installed and I can restart my computer to boot it up. After the OS selection menu (grub?) the monitor again goes into standby, until it loads up again when Ubuntu has started and is it the login screen.

If anyone could shed some light on this I would be very grateful!

Thanks again,
Danny

---

### Post by bulldog on 2007-04-07
Take a look into the BIOS if there are some modification to make for the standby,sleep mode and so on.

If you have installed ubuntu,it's a good idea to install drivers for the graphics,Im a nvidia user,so take a look in the multi media section of the forum for a guide to install your ATI driver.

[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by DannyW on 2007-04-07
Thanks for the speedy response!

I have tried to install the latest ATI drivers by following this article.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Now because I'm brand new to this I didn't know what this first step was asking me to do:
>  Enable "restricted" Repository

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work! 

I did the 'Disable Composite Extension' step, and then installed using method 1.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

Then 'Configured the driver':
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
...and rebooted the system.

Now I can use my native resolution, but I did get a pop-up on the task-bar saying something about a restricted driver.

However, at the verifying step of the article:
```
$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6400 (8.35.5)
```
I am asked to look at the output and check it has installed correctly, but when I type $fglrxinfo in the terminal there is no output.


Now in /etc/X11/xconf.org there are two Device sections:

```
Section "Device"
	Identifier  "ATI Technologies Inc R420 JK [Radeon X800]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

Is this normal?

Also, after the OS selection the monitor went into standby again for a good few minutes, then the Ubuntu login screen popped up. I noticed when pressing ctrl+alt+backspace or ctrl+alt+F1 my monitor went into standby. (Although I'm not sure what these shortcuts do, just seen them around the forums when I've been searching for solutions!).

Sorry for all the copying and pasting, just trying to give you as much info on what I've done.

Thanks!
Danny

---

### Post by DannyW on 2007-04-07
Ok, scrap the last post. The fglrx driver is installed.

I've added to the bootloader line vga=792 and I can see the splash screen (and if I take splash out of the bootloader line I see the status of the kernel loading).

After this is done I get a very distorted image for about 1 second which looks to have the colours of the login screen, then the monitor goes into standby mode.

After about 1 minute the monitor turns on and the login screen appears.

Now, all is fine, until I press ctrl+alt+F1. The monitor goes to standby, and so I press ctrl+alt+F7 to get back to the desktop. I see the distorted image (looks like horizontal distorted lines) and then the monitor goes off (but my TV (s-video out on my ati card) keeps this image in view). The computer has now froze, e.g. capslock doesn't toggle the capslock light on/off, so a restart is required using the button.

Any ideas?

Thanks
Danny

---

### Post by DannyW on 2007-04-07
Finally got there.

The default xorg.conf for some reason unknown to me was causing the monitor to go into standby when not viewing gnome desktop manager. I used the command given in the comments of xorg.conf:
sudo dpkg-reconfigure -phigh xserver-xorg

Now the system doesn't crash when I restart the X server with ctrl+alt+backspace and I can switch between ctrl+alt+f1-6. I had to select the ati driver, as fglrx caused the problem also. Not sure why this would be. I'll do some searching, but if anyone may know why this is the case, please let me know.

Thanks,
Danny

---

