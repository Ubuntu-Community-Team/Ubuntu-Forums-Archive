---
title: "Installing Ubuntu 6.10 on Dell Latitude 131L"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by jjalocha on 2007-02-22
This guide shows how to install Ubuntu 6.10 Edgy Eft on a Dell Latitude 131L notebook. Together with the Inspiron 1501, this is Dell's first notebook with an AMD processor. This is the first report I know of a Linux installation on this model.

This method has been tested both with Ubuntu and Xubuntu (should work also with Kubuntu) on the following hardware configuration:

[LIST]
[*]Processor: Mobile AMD Sempron 3500+ (1.80GHz 512K)
[*]Memory: 512MB, Double Data Rate 2-533 SDRAM, 1 Dimm
[*]Hard Drive: 60GB, 9.5MM, 5400RPM
[*]Optical Drive: 24X fixed CDRW/DVD with Cyberlink Power DVD
[*]Keyboard: Internal English
[*]Monitor: 15.4 inch Wide Screen WXGA LCD (1280x800)
[*]Graphics Card: Integrated ATI Radeon X1100 (ATI RS482, Radeon Xpress 200M)
[*]Sound Card: SigmaTel STAC92xx, HDA ATI SB 4383
[*]WiFi: Dell Wireless 1390 WLAN (802.11g,54Mbps) Mini Card (Broadcom Corporation BCM4311)
[*]Ethernet: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
[*]Memory Reader: SD/SDIO/MMC/MS/MSPro, Class 0805: Ricoh Co Ltd R5C822 (rev 19)
[/LIST]

Graphics Driver (without composite), WiFi, Sound, and SD Card working. Suspend/Hibernate not tested yet.


[COLOR="DarkRed"]**_Hard Drive_**[/COLOR]

If you're trying to install Linux on your computer, but the installer fails to recognize your hard drive, then you need to do the following. After booting your installation disk, press F6. You will be prompted for entering extra kernel arguments. Append the following characters, and continue normally with your installation.

```

pci=nomsi

```

Strangely enough, after this, my hard drive gets detected as device 'sda'.


[COLOR="DarkRed"]**_Graphics Driver_**[/COLOR]

This part is based mainly on  [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

By default, the open source driver (xserver-xorg-video-ati) is installed. If DRI is not working, but you need hardware OpenGL acceleration, then the propietary driver (xorg-driver-fglrx) must be installed instead. Be warned, though, that composite will not work.

Check if DRI is working. If you get "No" in your output, then you will have to install the propietary driver:

```

$ glxinfo | grep rendering
> direct rendering: No

```

Check the chipset of your card, and look for the line with your graphics controller:

```

$ lspci
[...]
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
[...]

```

The fglrx driver is known to support this chipset. But since it doesn't support composite with DRI, it must be disabled. Append the following lines to the [FONT="Fixedsys"]/etc/X11/xorg.conf[/FONT] file:

```

Section "Extensions"
   Option "Composite" "Disable"
EndSection

Section "ServerFlags"
   Option "AIGLX" "off"
EndSection

```

Now we can install it, generate a new set of kernel module dependencies, and configure the new driver:

```

$ sudo aptitude update
$ sudo aptitude install linux-restricted-modules-`uname -r`
$ sudo aptitude install xorg-driver-fglrx
$ sudo depmod -a
$ sudo aticonfig --initial
$ sudo aticonfig --overlay-type=Xv

```

Save and restart xorg with Ctrl+Alt+Backsp. If this doesn't work, just restart your computer.

Check if everything went well. With fglrxinfo you should see the following line:

```

$ fglrxinfo
[...]
OpenGL vendor string: ATI Technologies Inc.
[...]

```

And DRI should work now:

```

$ glxinfo | grep rendering
direct rendering: Yes

```

[COLOR="DarkRed"]**_Wi-Fi_**[/COLOR]

The default wifi driver installed (bcm43xx) does not work. The following procedure using ndiswrapper and the original windows driver is based on [this tutorial]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29"). This procedure works only with a clean install, and will probably fail, if you have attempted any previous setups.

First, let's find out what hardware you have. In my case, it's a BCM4311, but many other Broadcom Corporation cards shipped with Dell notebooks work with ndiswrapper, too.

```

$ lspci | grep Network
05:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

```

Chances are high, that your card is not working with a Ubuntu default installation, as seen by a lot of "invalid"s, "off"s and "0"s in iwconfig's output:

```

$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Curiously, in this case the ethernet adapter is recognized as eth1, while wifi is recognized as eth0.

Check the contents of the [FONT="Fixedsys"]/etc/iftab[/FONT] file and make sure to remove all devices that have the eth0 or wlan0 driver names reserved for them. If there are any lines assigning the names eth0 or wlan0 to a MAC identifier then delete them, comment them out with the "#" character:

```

#eth0 mac 00:19:7d:35:a6:d5 arp 1
eth1 mac 00:15:c5:ca:8c:c2 arp 1

```

In order to use ndiswrapper you must put the bcm43xx in the black list file, so that the blacklisted module will not be loaded on reboot from now on. Put the following line at the end of the [FONT="Fixedsys"]/etc/modprobe.d/blacklist[/FONT] file:

```

blacklist bcm43xx

```

And remove the module from the kernel:

```

$ sudo modprobe -r bcm43xx

```

You will need ndiswrapper version at least 1.28. Since the ndiswrapper package in the Ubuntu repositories are probably too old, you will have to compile your own.

First of all, you need to prepare the Linux build environment:

```

$ sudo aptitude update
$ sudo aptitude install build-essential
$ sudo aptitude install linux-headers-`uname -r` 

```

Get the latest (stable) version of the ndiswrapper driver from [sourceforge]("http://sourceforge.net/projects/ndiswrapper"), or get it directly with the command line. Extract the compressed tarball, and make the driver:

```

$ wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.38.tar.gz
$ tar -xzvf ndiswrapper-1.38.tar.gz
$ cd ndiswrapper-1.38
$ make distclean
$ make
$ sudo make install

```

If you want, you can now check the ndiswrapper to see that it is installed correctly. You should see something similar to:

```

$ ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.11

```

Now, get the driver package, extract the relevant files, and install it:

```

$ wget http://ftp.us.dell.com/network/R140747.EXE
$ unzip -a R140747.EXE
$ cd DRIVER
$ sudo ndiswrapper -i bcmwl5.inf

```

You can test the driver now. It should be installed, together with the correct hardware.

```

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

At the last installation step, you should be told something about a wlan0 alias being added, and the wifi light should turn on:

```

$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
$ sudo modprobe ndiswrapper

```

If you test with iwconfig, you should get some meaningful output for wlan0 now:

```

$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And [FONT="Fixedsys"]sudo iwlist scanning[/FONT] will work now, too.

To make sure your module gets properly loaded at boot time, add the following line at the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

ndiswrapper

```


[COLOR="DarkRed"]**_CD/DVD Drive_**[/COLOR]

My CD-RW/DVD-ROM is installed correctly out of the box. Be warned, though, that the Xubuntu Edgy Eft version of xfburn is broken. You will have to use another program for burning CDs, or you will have to downgrade xfburn to the Dapper Drake version:

```

$ wget http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb
$ sudo aptitude remove xfburn
$ sudo dpgk -i xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb

```

This will uninstall your xfce-desktop package, but since this is only a metapackage it's OK.



[COLOR="DarkRed"]**_Sound Driver_**[/COLOR]

I have the following soundcard:

```

$ lspci
[...]
00:14.2 Audio device: ATI Technologies Inc Unknown device 4383
[...]

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Sound playback works OK out of the box, but it gets temperamental with the microphone jack input, specially with Skype. You might try to tweak it with 'alsamixer' from the command line, which didn't do it for me. Or you can try the following hack with the command line version:

```

$ amixer set "Input Source" Line
$ amixer set "Input Source" Mic

```

For some reason, switching those in that order solves the problem. If this works for you, then you can add the fix permanently to your [FONT="Fixedsys"]/etc/rc.local[/FONT] file. Just add the following lines before [FONT="Fixedsys"]exit 0[/FONT].

```

/usr/bin/amixer set "Input Source" Line
/usr/bin/amixer set "Input Source" Mic

```


[COLOR="DarkRed"]**_SD Card Reader_**[/COLOR]

In order to get your internal SD Card Reader/Writer working, you will have to add the 'tifm_sd' module to your kernel. Just add the following line to the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

tifm_sd

```

If you are using Ubuntu or Kubuntu, the device should be mounted automatically. If you are using Xubuntu, you will have to mount the device manually:

```

$ sudo mkdir /media/mmc
$ sudo mount /dev/mmcblk0p1 /media/mmc

```

and unmount it with:

```

$ sudo umount /media/mmc

```


[COLOR="DarkRed"]**_Hibernate and Suspend_**[/COLOR]

I've never tested these, since i don't really know what they should do, or how they work.


[2007-03-04 EDIT: Extended introduction, tested on Ubuntu, CODE tags corrected.]
[2007-03-07 EDIT: Fixed microphone problem.]
[2007-03-21 EDIT: Added ndiswrapper at boot time fix.]
[2007-03-30 EDIT: Added SD Card, and minor information extended.]
[2007-04-03 EDIT: Solved SD Card.]
[2007-04-08 EDIT: Added sound card specs. Replaced 'apt-get' by 'aptitude'.]

---

### Post by jjalocha on 2007-02-22
Hello, everybody. This was my first post on this forum, so i'm still learning. Somehow, the verbatim text got disconfigured, and i lost the whitespaces... I'll try to get them right later.

As i told you on my first post, the microphone is still not working. I tried the following fix without success:

> The fix is to add
   options snd-hda-intel model=ref
to /etc/modprobe.d/alsa-base
Reboot for changes to take effect.

I also tried to set the MIC to Capture in alsamixer, but that's impossible, since there's not even a volume bar for MIC. Mic is labeled as "Input So".

There's a lot of threads on this topic, so i'm still reading, if i can find a solution.

---

### Post by jjalocha on 2007-03-07
Finally i solved the problem. The microphone jack was working right from the beginning, but Skype didn't recognize it. And then eventually it did. Sometimes. But usually not.

If you want consistent microphone input, add the following to your /etc/rc.local file, just before the exit 0.

```


/usr/bin/amixer set "Input Source" Line
/usr/bin/amixer set "Input Source" Mic


```

---

### Post by jjalocha on 2007-03-21
I hadn't been using wifi for weeks, and suddenly I realized that the device had disappeared, probably some time ago, after an upgrade. [FONT="Fixedsys"]sudo iwlist scanning[/FONT] simply showed no entry for [FONT="Fixedsys"]wlan0[/FONT].

It was possible to enable it temporarly with:

```

$ sudo modprobe ndiswrapper

```

but after rebooting it was gone again. I finally got help in [this thread]("http://ubuntuforums.org/showthread.php?t=389880"). I just had to add the following at the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

ndiswrapper

```

This makes sure, the module gets loaded at boot time.

---

### Post by n_dimos on 2007-03-23
I have the same laptop as you.

I would like to confirm that the VGA is working properly, i even have beryl installed. And wireless connection is up and running too.

Thanks for the guide.

---

### Post by jjalocha on 2007-03-30
I just came back from a trip and found your message. I'm really glad, this guide was useful to you.

I just bought a camera, and am trying now to use the SD Card reader. Have you tested it? I really don't know how to make it work. After plugging-in the card nothing happens, and I don't know what device I should mount. I asked for help on [this thread]("http://ubuntuforums.org/showthread.php?t=267749").

I suppose you are using Beryl without composite. Do you know about a workaround for this?

---

### Post by jjalocha on 2007-04-03
I finally know how to get the SD-Card reader/writer working. According to [this tutorial]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working"), the 'tifm_sd' module must be loaded into the kernel, adding the following line to the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

tifm_sd

```

When a card is inserted, it should be detected as [FONT="Fixedsys"]/dev/mmcblk0p1[/FONT], and mounted automatically by Ubuntu-Gnome. (Haven't tested that.)

But [if you are using Xubuntu]("http://ubuntuforums.org/showthread.php?t=398889"), automatic detection doesn't work ([Xfce Bug 2652]("http://bugzilla.xfce.org/show_bug.cgi?id=2652")), and you will have to mount it manually:

```

$ sudo mount /dev/mmcblk0p1 /media/mmc

```

and uninstall it with:

```

$ sudo umount /media/mmc

```

Maybe someone can come up with an elegant script to solve this...

---

### Post by jjalocha on 2007-04-08
Since 'aptitude' is meant to be a front-end for the APT package management system, it has some features that make it [preferable over 'apt-get']("http://ubuntuforums.org/showthread.php?t=350350"). So I replaced 'apt-get' by 'aptitude' in the guide.

---

### Post by hugo.archila on 2007-09-22
this is how i manage lcd brightness...

Adjust LCD Brightness!

sudo gedit /proc/acpi/video/VGA/LCD/brightness

cat /proc/acpi/video/VGA/LCD/brightness

levels:  100 37 12 25 37 50 62 75 87 100

echo 20 > /proc/acpi/video/VGA/LCD/brightness

---

### Post by ktaylor555 on 2008-04-28
I am having the mic problem with the Latitude 131L but don't know where to change the code to show the mic before the line can somebody please help me out.

Kathy

---

### Post by jjalocha on 2008-04-29
Sadly, I didn't understand your question very well...
but if you want to try the alsamixer fix, then you have to type the following lines (finished each one with ENTER) in a terminal (which I think is found in Applications > Accessories).

```

$ amixer set "Input Source" Line
$ amixer set "Input Source" Mic

```

If you are completely new to Linux, you might be better off asking questions at the [Absolute Begginer Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum. In my experience, there they know better how to help you start. There's also a sticky thread with some useful guides and howto's.

Good luck!

---

