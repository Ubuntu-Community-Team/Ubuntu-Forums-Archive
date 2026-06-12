---
title: "Karmic Koala on Macbook 2,1"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelvington on 2009-10-14
I'm switching from a Macbook Pro to a smaller, more portable black Macbook 2,1 configured to dual-boot Ubuntu Karmic Koala and OS X Snow Leopard. I'm spending most of my time in Ubuntu, with just a few problems. Here are my experiences.

* Most everything Just Works.

* Multitouch on the trackpad is great. Big improvement from earlier versions of Ubuntu.

* Wifi just works. What a relief!

* For audio, I had to install the ALSA sound mixer and explicitly turn on the speakers and headphones. Well documented and easily Googled.

* For iSight, I had to fish out the firmware from an OS X Tiger installation. Well documented and easily Googled. Upgrading the kernel seems to clobber the extracted firmware, so I've had to do it twice so far.

* Video works fine until I try to use an external monitor. Then: Kaboom. Mirrored output works OK, but if I uncheck mirrored output and activate the settings, the X server locks up the system and I have to reboot. I have not yet tried it with an VGA projector, but this is a showstopper for me (I do a lot of presentations). Alt-Function switching among VTs doesn't work.

* Bluetooth is nonfunctional. I can pair devices but none of them, so far, actually work. For instance, I can pair with my Blackberry 8300, but I can't even query it for services, much less use it as a tethered device. Keyboard and mouse also won't work.

I like the Mac hardware, but it's frustrating that stuff that works perfectly well on a $250 netbook doesn't work on the Mac. I blame Apple's inability to fully implement standards.

On the Apple side, I bought Snow Leopard specifically because it claimed to support MS Exchange calendarding only to be sorely disappointed. OS X lacks Ubuntu's robust support for FUSE filesystems (such as sftp). The lack of visual customizability is lame. And it's barenaked compared with Ubuntu when it comes to useful software. So I continue to spend nearly all of my time running Linux.

---

### Post by mabovo on 2009-10-15
I have the same configuration white MacBook2,1 with OSX Snow, Windows 7 and Karmic.

Everithing works out of the box.

I am strugling with grub/grub2 because rEfit sometimes doesn't show the menu options and I need to press ctrl-D.

For while I am continuing updating Karmic to the latest kernel and grub packgs and hope to solve these inconveniences soon.

---

### Post by benjamimgois on 2009-10-15
Could you post some pictures or even a video of your MAC booting Karmic ?

---

### Post by linuxopjemac on 2009-10-16
Can you please report your findings with Compiz ? I am very interested in the support for the Intel video card...
I would also like to know how long the boot process takes. I am using 8.10 and it works just fine with a 2.6.30 or 2.6.31 kernel.

---

### Post by jdriessen on 2009-10-17
I'm running 9.10 on Macbook2,1

Boot times are awesome (better than 9.04)
Screen brightness keyboard controls not working
high pitch whining noise coming from CPU. (this doesn't happen in Snow Leopard)
Compiz is running great, better performance compared to 9.04
Grub2 is working for me (via refit). i get an error about a depreciated command (from grub)
boot screen is a bit choppy - the sliding white bar under the ubuntu logo (loading screen) is very choppy.
touchpad works great, smoothness of scroll is good, not as great as OS X but now usable without tweaking.

I'm quite happy with 9.10.
I'm wondering if there will be a community documentation on running karmic on Macbook2,1?

---

### Post by FFuser on 2009-10-17
* Screen brightness controls not working
* CPU noise
* Choppy boot
* It seems to be quiet hot
* Suspend/Hibernate miserably fails

* bluetooth seems to work without problems (only small test with my phone)
* Grub2 seems to work

---

### Post by linuxopjemac on 2009-10-17
Does anyone of the developers here know whether these issues are going to be fixed ?

---

### Post by yelvington on 2009-10-17
Here's a [desktop screenshot]("http://twitpic.com/lvs3r").

Compiz effects -- the limited ones available in Ubuntu -- work fine, but as I hate windows that look like they're on LSD, I'm sticking with the intermediate settings.

I have no heat problems; in fact, the Macbook runs way cooler than the Macbook Pro that I'm giving back to the "spare" pool. Screen brightness (F1/F2) works fine. 

Boot process is slightly slower than Snow Leopard but WAY faster than Tiger. I can't swear to the version of Grub I'm running. This was a distribution upgrade from Jaunty Jackalope. 

Suspend/restore results in a kernel warning, but [a note on the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451815") suggests it might be a benign timeout warning.

---

### Post by mabovo on 2009-10-17
> **benjamimgois said:**
> Could you post some pictures or even a video of your MAC booting Karmic ?

The third icon should not appear on the screen.

---

### Post by mabovo on 2009-10-17
> **FFuser said:**
> * Screen brightness controls not working
* CPU noise
* Choppy boot
* It seems to be quiet hot
* Suspend/Hibernate miserably fails

* bluetooth seems to work without problems (only small test with my phone)
* Grub2 seems to work

Did You update the keyboard firmware available from Apple after Snow installation ?

Have You installed pommed and removed mouseemu ?

The screen brightness controls are working without problems here on my Mac2,1

---

### Post by FFuser on 2009-10-17
> **mabovo said:**
> Did You update the keyboard firmware available from Apple after Snow installation ?

Have You installed pommed and removed mouseemu ?

The screen brightness controls are working without problems here on my Mac2,1

Why do you assume I have snow?

mouseemu is uninstalled, pommed was not installed (but eject key and sound keys work without problem)

After installing pommed the brightness keys do work. Although I see pommed as a hack (also becasue I don't get osd-notifications like I get when I change the sound volume)

---

### Post by jdriessen on 2009-10-17
I installed pommed GTK (via Ubuntu Software Center)
screen cotrols work now. (after a restart and launching pommed GTK client)

---

### Post by yelvington on 2009-10-22
The X bug that was causing the error messages on awakening from suspend mode supposedly has been fixed, but Karmic updates have suddenly stopped. Perhaps that's in prep for the official launch.

---

### Post by yelvington on 2009-10-23
OK, I got some more updates. Good progress. Dual monitors are now working fine if I reboot. Plugging in a monitor and trying to detect is still an X crasher.

Overall I'm really liking Karmic on this laptop.

---

### Post by linuxopjemac on 2009-10-25
What I found was that one cannot see the progess of the battery charging. I am using Karmic Koala Desktop version RC on a MacBook 2,1. It stays at 100% loaded while it's only at 20% probably. I have no idea if this is a known bug, but I just wanted to give my 2 cents. Keep up the good work. I am very very impressed by the results!!!

---

### Post by FFuser on 2009-10-25
> **linuxopjemac said:**
> What I found was that one cannot see the progess of the battery charging. I am using Karmic Koala Desktop version RC on a MacBook 2,1. It stays at 100% loaded while it's only at 20% probably. I have no idea if this is a known bug, but I just wanted to give my 2 cents. Keep up the good work. I am very very impressed by the results!!!

I only had this once (just a few days ago) but it was after my battery was completely empty. (and I booted with it)
Afterwards (after a reboot) it was correct. (So I guess pulling out the cord for a while and plug it back in, and/or rebooting would have fixed it for me)

---

### Post by linuxopjemac on 2009-10-25
I was in the live environment and yes, the battery was absolutely empty before, just like you FFuser.

---

### Post by kelvin.illa on 2009-10-26
The brightness settings work with pommed but it's reset every reboot. It's really annoying.

---

