---
title: "A little help with xine-ui (trying to play DVD)"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-18
I installed xine-ui by following the instructions given [Here](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29) but still cannot play DVDs. I figure it was due to not having the libdvdcss2 package, so I DLed it to desktop and installed it using the following command:

sudo -i *longpackagename.deb*

Still no joy. So, I figure I've screwed up somewhere. What need I do to get this working? Any help is more than appreciated.

(Oh, and please, don't suggest I try Automatix, as I want to learn to do these things myself, not have a program do it or me. Thanks)

---

### Post by coolclassic on 2006-02-18
Try using apt-get:

sudo apt-get install libdvdcss2

---

### Post by Coelocanth on 2006-02-19
That doesn't work, as it says it can't find te file (or something of that nature). Anyway, shouldn't it be already installed if I did it with the dpkg command?

BTW, that original command I posted was supposed to be sudo dpkg -i *filename.deb* (which is what I actually used, just in case anyone thought I made a mistake in the command.

---

### Post by gerbman on 2006-02-19
[QUOTE=Coelocanth]That doesn't work, as it says it can't find te file (or something of that nature)[/QUOTE]

Did you make sure to enable the extra repositories, as suggested in the guide?

---

### Post by Coelocanth on 2006-02-19
Okay, for anyone who might be able to help, here's what I've tried:

tried to install libdvdcss2 using the terminal: no luck
tried installing it by DLing the .deb package: seemed to work.
installed the w32codecs: seemed to work.

Still can't play DVDs with xine.

Went to the RestrictedFormats page of the Wiki and thought "What the hell, I'll install the recommended gstreamer packages (see [This Link](https://wiki.ubuntu.com/RestrictedFormats) ). Still no luck and xine now gave me a 'no mrl' error.

Tried running the dvd from the terminal with the xine dvd:// command. Got to the dvd this way, but I get the following error:

> 
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/sda3 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda3 with libdvdcss.
libdvdread: Can't open /dev/sda3 for reading
libdvdread: Device /dev/sda3 inaccessible, CSS authentication not available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0003b4ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0003b670
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0003b670)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003b6f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0003b72f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x0003b72f)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0005ffb4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003dcb0e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003ddb43
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003ddbab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003dff89
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0

So, can **anyone** out there help me on this? I'm stumped.

---

### Post by Coelocanth on 2006-02-19
[QUOTE=gerbman]Did you make sure to enable the extra repositories, as suggested in the guide?[/QUOTE]

No, I didn't so that, as I found the .deb package before trying to edit my sources list. So, shouldn't the dpkg command have installed it anyway (thus no need to edit the sources list and go through the apt-get install route)?

---

### Post by kingsidy on 2006-02-19
try to play the dvd using another player like totem for example, or vlc if you have it installed.

---

### Post by gerbman on 2006-02-19
[QUOTE=Coelocanth]No, I didn't so that, as I found the .deb package before trying to edit my sources list. So, shouldn't the dpkg command have installed it anyway (thus no need to edit the sources list and go through the apt-get install route)?[/QUOTE]

I'm not sure exactly what the difference would be, but generally the apt-get route will be more reliable in the future, as it takes care of dependencies, etc. Did you execute the script at ```
/usr/share/doc/libdvdread3/examples/install-css.sh

```with root permissions? Might give that a shot if another player doesn't work.

---

### Post by Coelocanth on 2006-02-19
[QUOTE=kingsidy]try to play the dvd using another player like totem for example, or vlc if you have it installed.[/QUOTE]

Just tried totem. Got this:

Error invoking "dvdnav_get_next_block": Error reading from DVD.

---

### Post by Coelocanth on 2006-02-19
[QUOTE=gerbman]I'm not sure exactly what the difference would be, but generally the apt-get route will be more reliable in the future, as it takes care of dependencies, etc. Did you execute the script at ```
/usr/share/doc/libdvdread3/examples/install-css.sh

```with root permissions? Might give that a shot if another player doesn't work.[/QUOTE]

Yep. Did that in terminal with sudo. No love.

---

### Post by kingsidy on 2006-02-19
try installing libdvdnav4, and libdvdread3. look at the attached picture. it is a pic of my synaptic with the dvd libraries installed. maybe it will help

---

### Post by Coelocanth on 2006-02-19
King: thanks for the screenie. I've got them all installed already.

---

### Post by kingsidy on 2006-02-19
any luck playing dvd at all?

---

### Post by Coelocanth on 2006-02-19
Hmmm, very odd. Now it's working! Thanks for the help!

---

### Post by kingsidy on 2006-02-19
glad to hear that

---

