---
title: "Intrepid Ibex on MacBook 4,1"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by beauman on 2008-10-25
Hi!

I have installed the release candidate of Ubuntu 8.10 
on my MacBook.

Hardware:
```

yo@LosBastardos:~$ sudo dmidecode -s system-product-name
MacBook4,1

```

It works fantastic!

A lot of problems I had with Ubuntu 8.04.1 are solved!

The Sound, the wireless-network, the normal network and compiz 
work out of the box. :guitar:

Some remarks on:
[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

-----------------------------------------------------------------------

The sections "Sound" and "Wireless" are obsolete. It works
out of the box. Ubuntu will ask to install a propriatary
driver for a broadcom device. The netwok manager has really
improved. It will display all wireless connections. There is no need 
for "wicd" anymore. 

-----------------------------------------------------------------------

Brightness control works out of the box over the function keys of the
MacBook.

-----------------------------------------------------------------------

I couldn't make the web cam work. I copied the isight firmware from
the Mac partition to /lib/firmware/$(uname -r), as described in
the URL above.

It seems, that the kernel is loading it:
```

yo@LosBastardos:~$ lsmod | grep sight
isight_firmware        11008  0 
usbcore               148848  10 btusb,appletouch,appleir,isight_firmware,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd

```

There is no lib called "libpt-plugins-v4l2". Instead I have installed
two libs called "libpt-1.10.10-plugins-v4l2" and "libpt-1.10.10-plugins-v4l". Ekiga will not find any video device.

-----------------------------------------------------------------------

The right click is mapped to "fn"+"F12"

-----------------------------------------------------------------------
Mic:
I couldn't record with 

```
gnome-sound-recorder
```
It will hang, if you press stop.

The section "Mic" in the URL above seems to be out of date.

-----------------------------------------------------------------------

DUALHEAD:

Its messy! I couldn't make it work.

I used three different xorg.conf, but none of them
lead to a real split screen configuration:


1.) The default xorg.conf after installation:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

If the external monitor is not plugged in,
the default conf will set the resolution to the native 
value "1280x800". 

If the external monitor is plugged in, it
will set the resolution to "1023x768" for both monitors
and clone the screen.

2.) The configuration from the "gnome-display-properties" tool:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

This works very buggy. The monitors have different resolution, but
its not possible to drag the mouse from one monitor to the other.
Also, the second monitor never gets a refresh, so all output
stays forever on the screen.

3.) I tried to write my own configuration:
```

Section "Device"
	Identifier	"Configured Video Device1"
        Screen 0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor1"
EndSection

Section "Screen"
	Identifier	"Default Screen1"
	Monitor		"Configured Monitor1"
	Device		"Configured Video Device1"
EndSection

Section "Device"
	Identifier	"Configured Video Device2"
        Screen 1
EndSection

Section "Monitor"
	Identifier	"Configured Monitor2"
EndSection

Section "Screen"
	Identifier	"Default Screen2"
	Monitor		"Configured Monitor2"
	Device		"Configured Video Device2"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
        # singlehead
        #screen "Default Screen1"
        # dualhead
        screen 0 "Default Screen1" 0 0
        screen 1 "Default Screen2" rightof "Default Screen1"
	#Option   "Xinerama" "On"
        Option "Clone" "Off"
EndSection

#Section "DRI"
#        Mode 0666
#EndSection
```

It didn't work with "screen 0" and "screen 1". It could only clone
the displays.


-----------------------------------------------------------------------
Analog USB Apple modem:
It still does not work.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/271004]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/271004")

-----------------------------------------------------------------------

A few remarks to the installation of ubuntu on a MacBook and
the section "Basic instructions" from the URL above.

To resize the Mac partition I opened a terminal under Mac OS and
used the command
```

diskutil resizeVolume disk2s2 75G

```

When you install rEFIt, run the install script in the rEFIt folder
in a terminal under Mac OS.

Make sure to install grub in the MBR of the linux root file system,
not to device hd0! You can tell that during the installation of 
Ubuntu in the last step (step 7) under "Advanced".

For MacBooks with a keyboard oher then english: Keep in 
mind, that "Y" and "Z" are switched. When rEFIt asks you
to sync the GPT with the MBR, press "Z"!

Everything else is straight forward :)

-----------------------------------------------------------------------

A few remarks to intrepid ibex:

It rocks! :guitar:

The network manager should integrate a setup for 56K analog modems.
If you can only get online over a 56K modem, its bad that you
have to download "gnome-ppp" on a different computer and then
install it by hand.

The location of the boot manager, that you can tell the ubuntu
installer during the seven steps before the installation would
be better placed under point 5 (partitions and stuff).


Its really cool, that GRUB finally accepts a UUID for the parameter "root"!
Which makes it independent from the physical partition of the device.



See my efforts on: (in german)
[http://forum.ubuntuusers.de/topic/grub-unabhaengig-von-physikalischer-position-/]("http://forum.ubuntuusers.de/topic/grub-unabhaengig-von-physikalischer-position-/")
-----------------------------------------------------------------------

All in all its a great release, with cool new features. It runs 
very good on the MacBook with excellent performance and look & feel.

Great work!!!

Regards,
beauman

---

### Post by beauman on 2008-10-26
I have been busy as a bee and reported all bugs on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289546](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289546)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289552)
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/271004](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/271004)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/289566](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/289566)

---

### Post by beauman on 2008-10-27
I got the iSight webcam working now.

I downloaded the isight-firmware-tools from here

[https://launchpad.net/ubuntu/intrepid/i386/isight-firmware-tools/1.2-2](https://launchpad.net/ubuntu/intrepid/i386/isight-firmware-tools/1.2-2)

and installed it with
sudo dpkg -i isight-firmware-tools_1.2-2_i386.deb

Then:
 - mount the hfs+ partition with nautilus
 - run :
             ift-extract -a /media/Macintosh\ HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
 - reboot

---

### Post by johnlocke2342 on 2008-10-28
I got Ubuntu installed on my MB 4.1, but it's still Hardy because I prefer waiting the final version to install it (I  bought my MacBook for working purpose, but I never really used it to work. I don't know how it's for Intrepid, but Hardy was such a pain to get working that I prefer just upgrading on friday. You said the wireless network works out of the box. Do you know if WPA works? 
However, I installed the RC on my desktop PC desktop and it's working like a charm.

---

### Post by beauman on 2008-10-28
Hi! I have been only online over the wireless once, at a friends place.
I'll ask him if he has wep or wpa. hang on.

---

### Post by johnlocke2342 on 2008-10-28
I booted my MacBook with the Intrepid RC live cd, it seems it doesn't recognize my networks.

---

### Post by Cifra on 2008-10-28
> **johnlocke2342 said:**
> I booted my MacBook with the Intrepid RC live cd, it seems it doesn't recognize my networks.

Yeah, I noticed it doesn't find WEP'd networks. Try WPA2, works for me most of the time.

---

### Post by johnlocke2342 on 2008-10-28
Err...
I never had any problems connecting to WEP networks, it's WPA that causes problems to most users.
Anyway, I meant it seems Intrepid doesn't recognize my wireless chip.

---

### Post by beauman on 2008-10-28
Please post

sudo dmidecode -s system-product-name

If you have 4,1 its likely that it works.
Did it ask you to install a propriatary driver?

---

### Post by johnlocke2342 on 2008-10-28
It says "MacBook 4,1".

It didn't ask me to install proprietary drivers, but I installed the Broadcom STA wireless one, but no more wifi connection.

---

### Post by beauman on 2008-10-28
Ok, you have the same hardware as I have. And you have the same
propriatary driver as I have.

If I run "ifconfig" I get:
eth0
ng
eth1
ng
lo

Maybe you have to reboot? Maybe a "sudo init 1" will do?
Maybe you should just install it. I have copied the 
intrepid ibex to a 16G USB stick and bootet it two different
PC and two different notebooks. One of the notebook is my
macbook the other a acer. wireless worked also out of the boxs.
Both PC no problems. Just install it. You get all the updates anyway.

*** My friend just called me. He says the wlan I used is WPA ***

---

### Post by johnlocke2342 on 2008-10-28
If you say WPA works out of the box, it should be OK.
I think it's a rebooting problem but if I reboot from the live cd, it's like if I did nothing.
I did a USB startup disk from my Intrepid installation on my desktop PC with the intrepid utility, and it boots well on it. I tried to boot my MacBook with it, but I can't.
sudo init 1 did nothing.
I couldn't resist anymore, I'm upgrading...:mrgreen:

---

### Post by beauman on 2008-10-28
> **johnlocke2342 said:**
> 
I did a USB startup disk from my Intrepid installation on my desktop PC with the intrepid utility, and it boots well on it. I tried to boot my MacBook with it, but I can't.


How did you do the USB startup disk?

I also used to have problems booting the USB-stick from
a boot-CD on the MAC. With "grub" it will say
"loading stage 2" and hang. I now use isolinux on the
boot cd, that works. Good luck with the installation!

---

