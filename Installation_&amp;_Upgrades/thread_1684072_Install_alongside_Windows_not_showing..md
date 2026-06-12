---
title: "Install alongside Windows not showing."
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by Gyrth on 2011-02-08
Hello, 

I'm not very experienced in working with Ubuntu. I did try it using Wubi to install and that I liked very much. But now with the latest version (10.10) the wubi installer isn't showing every option. How do I get the old interface where you can install it alongside Windows?

The first attachment is what I get when opening wubi.exe and the second one is what I would like. That is a 10.04 version.

Thanks in advance.

---

### Post by bcbc on 2011-02-08
Did you download an iso that doesn't support wubi e.g. edubuntu or the alternate iso etc?

See the [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) for info on installing wubi.

---

### Post by Frogs Hair on 2011-02-08
The current version of Wubi offers 10.04 . To get Wubi for 10.10 installation You can download the 10.10 ISO , burn a cd , and run Wubi from the disk.

Another option is to use the link and scroll to the bottom of the page and download Wubi .exe. [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

---

### Post by bcbc on 2011-02-08
@Frogs Hair, I checked a few days ago and they've updated the [main download]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") to 10.10 now.

---

### Post by Frogs Hair on 2011-02-08
> **bcbc said:**
> @Frogs Hair, I checked a few days ago and they've updated the [main download]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") to 10.10 now.


Thanks! the last time I installed Wubi with a friend it was 10.04 and we used the index page to get 10.10.

---

### Post by Gyrth on 2011-02-11
I'm just using the normal Ubuntu distro. After using the Universal USB Installer to get the Netbook version of Ubuntu on my 2Gb flash drive, all the wubi.exe's I try to install are "Ubuntu Netbook-menu". I try's deleting all the wubi's iso's and my temp files using Ccleaner but every time I start up a freshly downloaded Wubi.exe the Netbook version is shown. Like seen on the first attachment. I downloaded the wubi from here, which is clearly the desktop version. [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

---

### Post by Gyrth on 2011-02-11
This is very weird. I just unplugged the usb flash drive and the next wubi I downloaded was the right one. I this some kind of software malfunction?

---

### Post by bcbc on 2011-02-11
> **Gyrth said:**
> This is very weird. I just unplugged the usb flash drive and the next wubi I downloaded was the right one. I this some kind of software malfunction?

There is no 'netbook' version of wubi.exe. Wubi.exe is supposed to check where it is running and restrict the choices accordingly - there's no point e.g. in offering Kubuntu if you are running wubi from an Ubuntu CD.

Wubi also looks all over to find installation media - so it scans optical drives etc. So - I guess - even if you are running Wubi from a folder (not the USB) but the USB is plugged in - it finds it and decides to restrict the choice.

Note wubi often cannot install from USB if it's > 900MB. This is because Wubi has a very simple check to prevent installation from DVD images - it won't allow an image > 900MB. And many USBs are bigger than that. So wubi fails them and tries to download from the net instead.

---

### Post by Gyrth on 2011-02-11
> **bcbc said:**
> There is no 'netbook' version of wubi.exe. Wubi.exe is supposed to check where it is running and restrict the choices accordingly - there's no point e.g. in offering Kubuntu if you are running wubi from an Ubuntu CD.

Wubi also looks all over to find installation media - so it scans optical drives etc. So - I guess - even if you are running Wubi from a folder (not the USB) but the USB is plugged in - it finds it and decides to restrict the choice.

Note wubi often cannot install from USB if it's > 900MB. This is because Wubi has a very simple check to prevent installation from DVD images - it won't allow an image > 900MB. And many USBs are bigger than that. So wubi fails them and tries to download from the net instead.

But why does the wubi on the netbook iso I put on my usb drive not show the install inside windows option? I mean not downloading the whole iso all over again and just use the files that are on the drive to install it inside windows.

---

### Post by bcbc on 2011-02-11
> **Gyrth said:**
> But why does the wubi on the netbook iso I put on my usb drive not show the install inside windows option? I mean not downloading the whole iso all over again and just use the files that are on the drive to install it inside windows.

Yeah that's a good question. I haven't tried out wubi on USB so can't offer any opinion.

---

