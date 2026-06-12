---
title: "Missing dependencies for WoeUsb."
date: 2017-09-06
forum: Installation &amp; Upgrades
---

### Post by soulsprit on 2017-09-06
I got a Windows 10 computer that I require to reinstall.

The other only desktop available in the house which is the one I'm typing from is a Ubuntu Xenial Xerus (16.04) that is untouched from most forms of configuration and works fine for basic things which is what it is used for. But it is a little bit messy configuration wise. It's quite a mess and I'm sure to cleanup this machine when I got spare time.

For now I want my Windows 10 .iso image to be copied onto a 16gb flash drive.
It is mentioned on the interwebs that WoeUsb is the designated tool for this on Xenial Xerus.

Installing the .deb file through the dpkg command however gives missing dependencies, namely...

libwxbase2.8.0
libwxgtk-webview3.0-dev\
[I]libwxgtk2.8.0

[/I]Oh yeah, and software center is broken. I can't install squat with it.
I'm bit of a linux leek but wasn't there a alternative to software center? Maybe it installs woeusb and the dependencies through that alot easier.

Manually installing libwx(whatever specified package, I tried several) all give the following moronic error that leaves no clues whatsoever.


NOTE:I already have woeusb installed with the missing dependencies hence the error underneath.
[I]
ERROR:"_woeusb : Depends: libwxgtk2.8-0 (>= 2.8.12.1+dfsg2) but it is not going to be installed_"

When I use the same terminal command through apt-get for libwxbase but with [/I]**-F **to detect and install for missing dependencies I get this error.

ERROR2:[U][I]Note, selecting 'libwxbase2.8-0' for regex 'libwxbase2.8.0'
You might want to run 'apt-get -f install' to correct these: (that's what I did facepalm <<)
[/I]
[/U]Computer telling me to do what I already tried in first instance, which is quite unhelpfull.
So how do you smack those libwx packages onto xenial xerus and how do I make Woeusb work properly?

If you need more info you have to ask me.

---

### Post by vasa1 on 2017-09-06
Where did you get the .deb from? What is the exact link?

---

### Post by soulsprit on 2017-09-06
[URL="http://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu"]HERE

:)
[/URL]

---

### Post by sudodus on 2017-09-06
I suggest that you try mkusb according to the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb-dus can create a Windows USB install drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

---

