---
title: "Ubuntu 10.10 Install HORRIBLY slow"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by TheTFo on 2010-12-09
Hello,

I've been trying to install Ubuntu 10.10 on my machine from a USB Stick, but the install process has been insanely slow.  Much slower than any of my previous Ubuntu installs, well over 10 hours before I finally quit.  Here are my specs:

[COLOR=#DF8D00]*_AMD Athlon II X4 640_*[/COLOR] Propus 3.0GHz Socket AM3
GIGABYTE GA-880GMA-UD2H AM3 AMD 880G SATA
[COLOR=Black][COLOR=#DF8D00]*_Western Digital WD5000AAKS_*[/COLOR][/COLOR]
Mushkin Enhanced Silverline 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 PC1333

I've run Memtest86+ no issues.

I'm attempting a Windows 7 Dual boot.  Windows 7 installed fine.  I've split the drive in two 3 partitions via gParted,  50% NTFS, ~50% Ubuntu and 10gig Swap.  These operations seemed to work fine.

I've heard of other Western Digital drives having Ubuntu issues.  Could this be related?

Any help is appreciated, Thanks!

---

### Post by TheTFo on 2010-12-09
Should I be trying 10.04 64bit,  or possibly 32bit 10.10 or 10.04?

---

### Post by Ross92 on 2010-12-09
I'm having this same problem!  I'm about to give up on ubuntu and just try to find another distro to use.

---

### Post by TheTFo on 2010-12-10
I had shutdown the computer after I had thought the install failed.  I booted up last night, and noticed that I had GRUB up, and booted into Ubuntu.  I was notified there were issues with packages that didn't finish or were damaged, and that I needed to do a partial upgrade.  I followed the steps, and all is well now.  System is extremely fast and responsive.

---

### Post by mörgæs on 2010-12-10
> **Ross92 said:**
> I'm having this same problem!  I'm about to give up on ubuntu and just try to find another distro to use.

Do you still have the problem? If so, it might be a good idea to try a few different options, first of all the alternate ISO.

If using a USB stick, it should be created with the latest version of Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

10.04 is also a good option. It is supported through april 2013, a year longer than 10.10.

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by TBABill on 2010-12-10
Installs taking that kind of time are signs of errors, definitely not normal to a 10.10 install. I never wait more than about 20 minutes to have an install finish loading on even my slower machines. Is it possible the md5sum was not run and verified for the iso after download? Sounds like files with errors trying to be resolved unsuccessfully. I would try 10.04 but make sure to run md5sum on the iso you download to make sure it is error free before creating the image. I suppose it could also be a hardware issue if the system just appears to hang, but if there are file errors I would suspect either the download, the burned image (or created image on the USB) or hardware (least likely if it was working fine previously and works fine in another OS).
 
Did these run the live session fine for all hardware?

---

### Post by acseven on 2010-12-11
Hi,

I had the same exact problem with my install. I am trying to setup ubuntu 10.10 correctly on my old (2006) Asus M3n/M3000n centrino laptop, and it has been very difficult to do anything.

So here's what I have done so far:

[LIST=1]
[*]This is a 100% processor usage issue. read on for more.
[*]Install Ubuntu using a usb stick: took more than 3 hours, but only started after 10 minutes or so of nothing (i.e. black) on the screen.
[*]I also ran ubuntu from the USB stick, same behaviour, extremely slow - didn't go very far because I decided to install on the hard drive to see it that was the problem.
[*]After successfully installing ubuntu, it takes ages to load (about 15 minutes or more). After it loads it gives a lot of gnome applet errors and asks for termination confirmation on all of them.
[*]application performance is dreadful. To get a sys monitor or terminal window open it takes about 3-5 minutes. the driver manager doesn't even open.
[*]On sys monitor (all processes) I can't see any active process other than sys monitor
[/LIST]

Could it be the video driver? I read somewhere something about "quiet splash" vs nomodeset, i915.modeset=1, i915.modeset=0, xforcevesa, but I don't know where to change it or if it does anything.

(shift key pressed on boot does nothing - I end up on the usual login screen)

Any ideas?

Thanks

---

### Post by mörgæs on 2010-12-11
Hi, welcome to the forum.

How much memory and which screen card does the machine have?

---

### Post by acseven on 2010-12-12
Hi,

It has 1Gb RAM on an Intel 855GM+ (82852 integrated graphics).

I can say that I also have tried these two "solutions", with no luck:
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511)
- brian-rogers graphics fix (kernel downgrade)


(also - dunno if related - on boot I get an error on calling asus_laptop CWAP or something similar)
(also.2 - probably no related - the wireless card wasn't working - it's a broadcom bcm4309 rev 03, but after some messing around it's kind of working - not very stable connection).

---

### Post by mörgæs on 2010-12-13
Have you thought about installing Lucid Puppy for comparison? 

If you install a minimal Ubuntu without GUI, is the machine up to normal speed?


I know that these suggestions are not very specific to the problem. Maybe someone else has better ideas...?

---

### Post by acseven on 2010-12-13
Hi, thanks for the reply. 

Where can I find the one without a GUi?

Thanks

---

### Post by acseven on 2010-12-13
> **mörgæs said:**
> If you install a minimal Ubuntu without GUI, is the machine up to normal speed?

I tried the minimal 10.10 install on a USB pen drive and surprinsigly it has a similar behaviour. It's *extremely* laggy for text mode operation.

It starts with a blue to select the Installation type, then blackness for a minute or two, then "Starting system log daemon: syslogd, logd." (2 minutes), blackness, then "Trying to enable the frame buffer..." (1 minute) and after that starts with screen refreshes (ascii menus): a frame takes about 4 seconds to fully render a screen - i.e. from left-up corner to right-down corner.

In process procedures (e.g configuring network) appears to be fast. Screen changes are not.

A command-line is similar ... 

I stopped using both at the network config as I didn't have a cable connection at the time.


> **mörgæs said:**
> Have you thought about installing Lucid Puppy for comparison?

Yes I did; it took a few minutes (5-7?) to load drivers and initial startup, and after it fully loaded the interface it ran smooth/normal. Wierd thing was a few minutes later I was kicked back to command line mode and couldn't get back to graphics mode yet...
edit: breaks when I try to open quickpet.



Cheers!

---

### Post by mörgæs on 2010-12-14
I guess I am running low on good ideas. Trying a minimal 10.04 might be worth the while, though.
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

A wired internet connection is highly recommended while installing.

---

### Post by acseven on 2010-12-14
> **mörgæs said:**
> I guess I am running low on good ideas. Trying a minimal 10.04 might be worth the while, though.
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

A wired internet connection is highly recommended while installing.

Thanks for the input, I'll try to see those recommendations.

I am now trying Xubuntu and this is more stable so far, and though it does behave better, it isn't snappy or acceptable - takes ages to load the system and any app.


Cheers

---

### Post by acseven on 2010-12-19
I reinstalled ubuntu 10.10 with a wired connection and that didn't help much. :S

The wierd thing is that a youtube video plays fine while the entire system is laggy as snails... 

Anyone know why can't I open the additional drivers window? it searches for drivers but after that nothing happens. In xubuntu it opened (eventually).

Cheers

---

