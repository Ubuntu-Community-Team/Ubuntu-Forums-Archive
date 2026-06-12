---
title: "I want to upgrade the browser of Ubuntu 15.10 without replacing the OS."
date: 2023-02-26
forum: Installation &amp; Upgrades
---

### Post by sebastianbenito on 2023-02-26
I have a 32 bits PC in which I use Ubuntu 15.10 operating system (this is a 2015 release). Unfortunately, Ubuntu 15.10 went unsupported by 2016, and, therefore, the browser included in that release of Ubuntu cannot be updated. Given this, I thought that the solution could be a portable stand-alone new browser that can run along with that version of Ubuntu. Then: Is there any portable stand-alone updated browser that can be run in a USB flash-drive under Ubuntu 15.10 in a 32 bits machine?

---

### Post by QIII on 2023-02-26
Is there a particular reason  you are not using a supported release?

---

### Post by guiverc on 2023-02-26
I still use 32-bit hardware (*though rarely*) being devices from 2003 & 2004.  You can use a *supported* release of Ubuntu on *i386* devices such as I do with my old IBM Thinkpads (eg. 18.04 is still currently *supported* even though later 18.10 & 19.04 which had *i386* support are now EOL).  Though note 18.04 reaches EOSS in a few months, and if I recall correctly, *i386* does not get ESM support.

If using an *unsupported* release like 15.10, I'll suggest you're better offline, for security purposes alone.

EOL Notice - [https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/](https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/)

---

### Post by QIII on 2023-02-27
D'oh!  I didn't notice the 32-bit hardware ...

---

### Post by ajgreeny on 2023-02-27
You may have to move to Debian, the OS on which Ubuntu is based; that does still have 32bit systems still available and still supported.

---

### Post by sebastianbenito on 2023-02-28
> **QIII said:**
> Is there a particular reason  you are not using a supported release?

Yes there is! Otherwise I would be upgrading the OS; and, on the other hand: What difference does it make? That is: Are you going to answer what I posed or what? Under my circumstances, **I NEED to upgrade the browser I have, but without having to replace the OS.**

---

### Post by guiverc on 2023-02-28
***Your release is [I]u*nsupported[/I]**, yet you still want support?

From the link I provided earlier ( [https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/](https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/) )

> This is a follow-up to the End of Life warning sent earlier this month  to confirm that **as of today (July 28, 2016), Ubuntu 15.10 is no longer  supported**.  No more package updates will be accepted to 15.10, and it  will be archived to old-releases.ubuntu.com in the coming weeks.

---

### Post by ajgreeny on 2023-02-28
> **sebastianbenito said:**
> Yes there is! Otherwise I would be upgrading the OS; and, on the other hand: What difference does it make? That is: Are you going to answer what I posed or what? Under my circumstances, **I NEED to upgrade the browser I have, but without having to replace the OS.**
You might "**need to upgrade the browser"**, and I note that you haven't actually told us which browser you need, but in spite of this need you are going to have to accept that it will be just about impossible to do.

The repositories for 15.10 no longer exist where they were and even if they were accessible easily, the packages would be the versions you already probably have, assuming that you updated regularly while 15.10 was still supported, ie, in July 2016. So a system upgrade to a fully supported version is your only sensible option no matter how annoying you find that situation.

---

### Post by BBQdave on 2023-02-28
> **ajgreeny said:**
> You may have to move to Debian, the OS on which Ubuntu is based; that does still have 32bit systems still available and still supported.

+1 For Debian!

You would be able to have an up to date and secure OS and an up to date browser :)

---

### Post by guiverc on 2023-02-28
I'm also another +1 for Debian..

Most of my *i386* or 32-bit x86 hardware now runs Debian...  (*i still have one running 18.04 LTS that I've felt no need to move; that reaches EOSS for 'main' packages in April 2023 so it'll soon move too I bet*).

I QA-tested Debian releases on the same hardware I used to QA-test *i386* on releases up to 19.04 or *disco* of Ubuntu (esp. Lubuntu, Xubuntu which had ISOs into the *disco* cycle; with most stopping at 18.04 LTS), and of those 12+ old *i386 *devices, only one didn't perform equally well on Debian as a *lighter* Ubuntu *flavor* (*it preferred Lubuntu over Debian*).  That one device was just so *resource limited *it was no fun to use & thus I gave up trying to work out why...

I did note some devices performed better (*esp. related to graphics*) on* old-old-stable* of Debian, but I'd not pay for extended-LTS support for that release, and use a *supported* release of Debian as *browser* use is not the purpose of the extended-LTS support (*the concentration being server usage*).

---

### Post by MAFoElffen on 2023-02-28
Another +1 for Debian 32bit. 

I still have one laptop that I started my early Ubuntu journey with, that is 32bit, which is now running Debian.

---

### Post by mIk3_08 on 2023-03-02
> **sebastianbenito said:**
> I have a 32 bits PC in which I use Ubuntu 15.10 operating system (this is a 2015 release). Unfortunately, Ubuntu 15.10 went unsupported by 2016, and, therefore, the browser included in that release of Ubuntu cannot be updated. Given this, I thought that the solution could be a portable stand-alone new browser that can run along with that version of Ubuntu. Then: Is there any portable stand-alone updated browser that can be run in a USB flash-drive under Ubuntu 15.10 in a 32 bits machine? I think you can still use the tar.bz firefox. Maybe you can download the latest one. Regards and cheers.

---

### Post by grahammechanical on 2023-03-02
> Is there any portable stand-alone updated browser that can be run in a USB flash-drive under Ubuntu 15.10 in a 32 bits machine? 				

Getting back to your question. Tricky. The nearest thing that I know of in Linux to a portable application is Appimage.

[https://en.wikipedia.org/wiki/AppImage](https://en.wikipedia.org/wiki/AppImage)

[https://appimage.org/](https://appimage.org/)

[https://appimage.github.io/Firefox/](https://appimage.github.io/Firefox/)

It might be possible for a 64 bit version of a web browser as an Appimage to run on a 32 bit Linux OS. I wonder if anybody has tried it. You could be the first to experiment. Let us know the results. There might be other web browser Appimages available that may not use as much resources as Firefox. 

I found this through a internet search.

> Where are AppImages saved?


Where do I store my AppImages? &#61633; An important point about the AppImage format is that you can store AppImage files **wherever you want**.  This includes your home directory, your downloads directory, a  dedicated applications directory, a USB thumb drive, a CD-ROM or DVD, or  even a network file share. 27 Mar 2022




The place to look for Appimages

[https://www.appimagehub.com/](https://www.appimagehub.com/)

Regards

---

### Post by MAFoElffen on 2023-03-02
64bit appimage's cannot run on 32bit OS... Has been tried by users already.

You would get an error similar to this:
```

bash: ./KeePassXC-2.1.4-x86_64.AppImage: [COLOR=#ff0000]cannot execute binary file[/COLOR]

```
To be the Devil's Advocate :twisted: ... There are Linux 32bit Browsers:
Pale Moon Browser
Chromium Browser
Falkon Browser
SeaMonkey Browser
Epiphany Browser
(More...)
I still recommend installing fresh Debian 32bit as OS: 
[https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-11.6.0-i386-netinst.iso](https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-11.6.0-i386-netinst.iso)
[https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/11.6.0-live+nonfree/i386/iso-hybrid/debian-live-11.6.0-i386-gnome+nonfree.iso](https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/11.6.0-live+nonfree/i386/iso-hybrid/debian-live-11.6.0-i386-gnome+nonfree.iso)

---

### Post by ajgreeny on 2023-03-02
I suspect you might have a similar problem trying to run firefox direct from the downloaded .tar.gz even though Mozilla does produce a 32bit version of the tar.gz archive simply because your OS version may not have some of the necessary library files or versions of files.
Try it if you wish by going to [https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release](https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release) and choosing the 32bit version of firefox 110. That will however, not overcome the lack of support for the OS even if firefox does run.

Unfortunately I have no way to test this as I don't have any 32 bit systems, and  certainly none that date all the way back to the 15.10 times.

---

### Post by grahammechanical on 2023-03-02
I am not recommending anything but here is an Appimage of a browser that has an i386 download

[https://www.appimagehub.com/p/1280979](https://www.appimagehub.com/p/1280979)

[https://github.com/kamranahmedse/pennywise/releases](https://github.com/kamranahmedse/pennywise/releases)

Regards

---

### Post by him610 on 2023-03-04
++ Debian
Here is where you can get 32bit Debian, [https://www.debian.org/distrib/]("https://www.debian.org/distrib/")

Another alternative for i86 32bit machines is Raspberry Pi OS for PC and Mac found here: [https://www.raspberrypi.com/software/operating-systems/]("https://www.raspberrypi.com/software/operating-systems/") Look at the bottom of the page. It used to be called Raspbian OS.
> Raspberry Pi Desktop
Compatible with: PC and Mac
Debian Bullseye with Raspberry Pi Desktop
Release date: July 1st 2022
System: 32-bit
Kernel version: 5.10
Debian version: 11 (bullseye)
Size: 3,440MB 
I have it installed on Acer AOA netbook from 2008. It is a little slow, but it works just fine. It uses Chromium 32bit ver 90+ (however, it is updating now)

---

### Post by guiverc on 2023-03-04
As I still use Ubuntu on old IBM Thinkpad using pentium M (*thus i386 only*), the latest `firefox` available currently is

```
firefox | 110.0.1+build2-0ubuntu0.18.04.1 | bionic-security | source, amd64, arm64, armhf, i386, ppc64el, s390x
```

I've used `firefox`, but on old *i386* devices I usually opt for `lynx` on that device, as most of what I want to read is just the text & text based browsers are faster. If I want to stream something on youtube I'll use `chromium` which is 

```
chromium-browser | 110.0.5481.100-0ubuntu0.18.04.1 | bionic-security/universe | source, amd64, arm64, armhf, i386
```

on my old *i386* pentium M laptop using Ubuntu 18.04 LTS.  Within two months I expect that machine to have been re-installed with Debian, like I've already done with many of my other *i386* hardware.

I've used all my *i386* hardware in QA of both Ubuntu & Debian (*mostly flavors for recent Ubuntu releases as GNOME barely walked on i386*), and of ~12 devices used in that QA; only 1 performed better on Ubuntu *flavor(s)* than the equivalent Debian system, and whilst I was interested it why, the box was just too unpowered & a *pain* to use thus I just ignored it as an *anomaly*.

---

### Post by him610 on 2023-03-05
RE: #17
This is what the desktop for 32bit Rasperry Pi OS (Debian) looks lilke .... 
[URL="[url=https://i.imgur.com/hom4Wuy.png]
  [img]https://imgur.com/hom4Wuyl.png[/img]
[/url]"][url=https://i.imgur.com/hom4Wuy.png]
  [img]https://imgur.com/hom4Wuyl.png[/img]
[/url][/URL]
You can also see the specs of my Acer AOA inside the terminal.
Chromium version 90.0.4430.212-1~deb10u1 i386 [installed]

You can probably download and configure 32bit Debian to look like this also. I think I will try it.
Have fun and enjoy the learning experience.

---

