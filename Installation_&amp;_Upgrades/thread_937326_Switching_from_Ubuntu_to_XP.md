---
title: "Switching from Ubuntu to XP"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by LegendFury on 2008-10-03
I recently installed ubuntu on my computer (which previously had XP) and I didn't like it. I chose the 2nd option which, I believe, wipes the entire hard drive. If it makes a difference, I installed the latest ubuntu using unetbootin. I have WinXP on a USB (for some reason, it won't read my CD drive at boot menu).

The problem is, whenever I try to boot my USB with WinXP in it, it says:

"could not find kernal image: linux
boot: "

Can anyone help? Thanks.

---

### Post by cariboo on 2008-10-03
I think you have a problem there. To qoute from Wikipedia

> Supports mainstream Linux distributions, including, but not limited to, Ubuntu, Fedora, openSUSE, CentOS, Debian, Linux Mint, Arch Linux, Mandriva, Slackware as well as FreeDOS, FreeBSD and NetBSD.

Unetbootin does not seem to support windows that is why you are getting a kernel not found error.

Have a look at this page, it may help:

[http://www.vandomburg.net/installing-windows-xp-from-usb/](http://www.vandomburg.net/installing-windows-xp-from-usb/)

You have to have access to a working computer of course.

---

### Post by LegendFury on 2008-10-03
Is there any way to do this with just a USB drive? Thanks for the reply.

---

### Post by LegendFury on 2008-10-04
Can anyone help please? Thanks.

---

### Post by caljohnsmith on 2008-10-04
I'm not sure exactly what's going on based on your description, but you could start by making sure the Windows USB drive has a Windows MBR (Master Boot Record) since it sounds like it may not. Just boot your Windows Install CD, press "r" at the first main menu to get the recovery console, and run:
```
fixmbr
```
Try that first and let me know what happens, and we can work from there.

---

### Post by LegendFury on 2008-10-05
> **caljohnsmith said:**
> I'm not sure exactly what's going on based on your description, but you could start by making sure the Windows USB drive has a Windows MBR (Master Boot Record) since it sounds like it may not. Just boot your Windows Install CD, press "r" at the first main menu to get the recovery console, and run:
```
fixmbr
```
Try that first and let me know what happens, and we can work from there.

The CD won't read at boot menu though.

Is there a way to just run windows apps on Ubuntu? I also need to to install motherboards drivers, but can't since they won't open.

---

### Post by cariboo on 2008-10-05
To fix your problem you are going to nedd another computer. There are two other ways to fix the problem, buy another cdrom drive, You may even be able to pick one up for free if you look around. Try garage sales. You may be able to create an iso file from the windows files you have on your usb device, if you can do that, then you can install virtualbox if you cpu is capable of virtulaization.

You windows executeables will not work on linux. Unless you have really wierd hardware, most of it should be detected during boot up and the drivers will be enabled. The only thing you may need proprietary drivers for is you video card. if you have a fairly recent video card go to System-->Administration-->Hardware Drivers and select the driver for your video card.

Personally I think finding another cdrom drive is your best bet, as a matter of fact if you are near Willaims Lake drop by and I'll give you one.

Jim

---

### Post by LegendFury on 2008-10-05
But the CD drive works fine when I put a CD in at the desktop screen, just not at the boot screen.

And for some reason, it doesn't install the drivers for my motherboard, so the PC runs a lot slower than it should.

---

