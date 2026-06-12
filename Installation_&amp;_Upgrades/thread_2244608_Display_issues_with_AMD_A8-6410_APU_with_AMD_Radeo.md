---
title: "Display issues with AMD A8-6410 APU with AMD Radeon R5 Graphics"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by ashik on 2014-09-17
I have recently purchased a Lenovo G50-45 laptop with the following configuration:
AMD A8-6410 APU with AMD Radeon R5 Graphics
4GB DDR3 RAM
Radeon HD 8550M graphics with 2GB Video RAM

I have tried the open source drivers from xorg as well as proprietary drivers (AMD Catalyst 14.6 Beta). I am having the following problems:
1. The display is very patchy. Display is not smooth, but concentric patchy areas appear all over the screen.
2. Cannot switch between the graphics devices.

I also tried to switch off the discrete graphics in the BIOS settings, but still the problem persists.

I checked another identical laptop running Microsoft Windows 8 and noticed that none of the problems I have mentioned appear there.

I believe it is a specific problem with Linux support of this particular device. If anyone can help, I would love to hear from him or her.

---

### Post by QIII on 2014-09-17
Hello!

I suspect that you may have improperly set up ATI Dual Graphics (not hybrid graphics, which is a combination of either ATI or NVIDIA graphics and an Intel GPU)

Let's get you back to a good place.

Since you have installed from ATI's website, please remove the driver thus:

```
sudo amdconfig --uninstall
```

and move any xorg.conf that may have been created

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```

Then reinstall some tidbits that may have been removed by the ATI installation process

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

If that gives you an error an error like "E: Internal Error, ...", try

```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
``` 

to satisfy multi-arch.

Then reconfigure

```

sudo dpkg-reconfigure xserver-xorg
``` 
Reboot and you should be back to the normal default installation and we can work from there to get ATI Dual Graphics set up.

I suggest working from the ATI driver in the repo for your release, because that was tested and found to work at the time of the Ubuntu release.  ATI and Canonical do a dance every April and October to get this right.

---

### Post by ashik on 2014-09-18
Hi Qill,

Thanks for your reply.

Please note that I have already tried the fglrx drivers (version 13.350.1) that are available in the Ubuntu 14.04 repositories. 
Then I have tried both the 14.4 and the 14.6beta drivers available in the AMD website.
Unfotulately, Lenovo support page does not provide any drivers for Linux.
([http://support.lenovo.com/in/hi/products/laptops-and-netbooks/lenovo-g-series-laptops/g50-45-notebook-lenovo](http://support.lenovo.com/in/hi/products/laptops-and-netbooks/lenovo-g-series-laptops/g50-45-notebook-lenovo) )

I all my attempts, I have observed that the display is full of concentric patches. (Looks very similar to multiple concentric halo patterns). 
And also I cannot switch between the two graphics card. (But everything works fine in Windows 8).

Thanks,

---

### Post by QIII on 2014-09-18
That's understood.  It is possible that the 8000 series adapter may not be supported by AMD in Linux yet.  But I don't know that for sure.

Have you gotten back to the point where the fglrx driver is cleanly removed and you are running the open-source driver?

When you get there, we can work on seeing if we can get the fglrx driver to work.  There is a step in the setup you may have missed.  If you did miss it, only one of your adapters will be set up, and even that may be incomplete.  The Catalyst Control Center will not know there is another adapter, so it won't give you the option to change between them.

If we find after installing the driver and doing that step that the driver still will not work, then we may have to consider alternatives -- like sticking to Windows.  That's not a bad thing if it means you can use your computer.

---

### Post by ashik on 2014-09-18
Hi QIII,

Thanks for your quick reply.

I have been freshly installing Ubuntu 14.04.1 and initially using the open source drivers from xorg.
Then after that I have installed the fglrx drivers.

One strange thing I noticed is that even though if I create a new xorg.conf file using
sudo amdconfig --adapter=all --initial
the contents of xorg.conf is changed to some minimal configuration the moment I log out or restart the machine. I cannot seem to permanently keep the configurations of my xorg.conf.

With regards to the present display, I can manage with it, even though I would prefer if the patchyness was resolved. (I always prefer to use Linux, so using Windows is out of the question.)

Thank you,

---

### Post by andrecanha on 2015-02-17
Hello, I just bought a new laptop ( HP 15-g023np) with the same processor and I'm having a similar problem. Altough my display isn't patchy, I can't switch between graphics cards.
Still haven't tried the experimental drivers from AMD because the packages seem to conflict with a few other that come installed by default in ubuntu.

Do you have any updates on this matter, or have you reported the problem to AMD unofficial help?

Thanks in advance.

---

### Post by giosimar on 2015-04-25
same problem... 
with 15-04 not patchy, but also not switch...

---

### Post by gurubie on 2015-07-24
This is complete BS. If AMD does not have their open source act together by now then they never will. I will no longer buy any AMD GPU or system with them or their CPU's. It's far to late.

That's not to say Nvidia isn't completely a jerk for not completely open sourcing their GPU binaries. It can at least work; but If that horse is not let run then forget them too. I have some new compatibility issues; that should not exist with Nvidia and because of this issue.

Be very careful with what GPU is in any device you buy. It's like they do not want you to know. I'm OVER IT!

NO SALE! Thus completes my research on THAT lappy.

---

### Post by QIII on 2015-07-24
Which open source driver does AMD produce?

AMD produces a proprietary driver. 

Then again, a rant need not be accurate...

---

