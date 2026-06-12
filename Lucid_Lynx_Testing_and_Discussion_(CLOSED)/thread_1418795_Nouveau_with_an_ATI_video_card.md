---
title: "Nouveau with an ATI video card"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Didius Falco on 2010-03-01
I keep getting nouveau updates installed, but from everything I've read, it only works with nVidia graphics cards.

My video card is an ATI Radeon HD 4870. My MB is a Gigabyte GA-MA790GP-DS4H, which has an AMD chipset, so I've no nVdia parts on this machine at all.

I don't mind leaving them installed until the official release of Lucid, but I can't see where I could be any help in bug reporting, since, as far as I can tell, they'll never get used...

Should I leave these installed? Is there some use for them that I'm missing?

---

### Post by tito_torrisi on 2010-03-01
I have a Geforce card and your ATI drivers installed as well. (And also all other x-org drivers).
I guess thats on purpose, whysoever...

---

### Post by Seren on 2010-03-01
I guess it is in case your graphic card suddenly dies and you have to swap a spare one, not necessarily from the same constructor.

But don't worry if you have an ATI card the Nouveau driver is not even loaded. What is wasted is some room on your HDD, but I don't think the xorg driver is really big, a few hundred kilobytes at most.

'll /usr/lib/xorg/modules/drivers/' to get the list of all the useless graphic drivers installed.

On my install, that directory is taking 5,3 MB.

---

### Post by Didius Falco on 2010-03-01
Yeah, that makes sense - now that you've said that, I remember seeing intel stuff as well.

I'm not hurting for space, so I'll just let 'em sit there all bored and lonely. ;)

---

### Post by psyke83 on 2010-03-01
> **Didius Falco said:**
> I keep getting nouveau updates installed, but from everything I've read, it only works with nVidia graphics cards.

My video card is an ATI Radeon HD 4870. My MB is a Gigabyte GA-MA790GP-DS4H, which has an AMD chipset, so I've no nVdia parts on this machine at all.

I don't mind leaving them installed until the official release of Lucid, but I can't see where I could be any help in bug reporting, since, as far as I can tell, they'll never get used...

Should I leave these installed? Is there some use for them that I'm missing?

Well, this is the complete list of drivers installed on everybody's system, regardless of the hardware in their machine:

```
conn@portable:~/Downloads$ dpkg -l | grep xserver-xorg-video
ii  xserver-xorg-video-all                            1:7.5+1ubuntu9                                  the X.Org X server -- output driver metapack
ii  xserver-xorg-video-apm                            1:1.2.2-1                                       X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                            1:0.7.2-1                                       X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                            1:6.12.99+git20100126.e5933fd7-0ubuntu2         X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                          1:1.2.2-1                                       X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                         1:1.3.2-1ubuntu1                                X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                          1:0.4.1-1                                       X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                          2.11.7-1                                        X.Org X server -- Geode GX2/LX display drive
ii  xserver-xorg-video-i128                           1:1.3.3-1                                       X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                           1:1.3.2-1                                       X.Org X server -- i740 display driver
ii  xserver-xorg-video-intel                          2:2.9.1-1ubuntu6                                X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-mach64                         6.8.2-2                                         X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                            1:1.4.11.dfsg-2                                 X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                       1:1.2.4-1                                       X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau                        1:0.0.15+git20100219+9b4118d-0ubuntu3           X.Org X server -- Nouveau display driver (ex
ii  xserver-xorg-video-nv                             1:2.1.15-1ubuntu3                               X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome                     1:0.2.904+svn812-1ubuntu1                       X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                           6.8.1-2                                         X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                         1:6.12.99+git20100126.e5933fd7-0ubuntu2         X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-rendition                      1:4.2.3-1                                       X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                             1:0.6.3-1                                       X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                        1:1.10.4-1                                      X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                         1:2.3.1-1ubuntu1                                X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion                  1:1.7.3-1                                       X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-video-sis                            1:0.10.2-1                                      X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                         1:0.9.3-1                                       X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                           1:1.4.3-1                                       X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                        1:1.3.3-1                                       X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                          1:1.2.3-1                                       X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                            1:0.2.0-4                                       X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-video-vesa                           1:2.3.0-1                                       X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                         1:10.16.8-1ubuntu1                              X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                         1:1.2.3-1                                       X.Org X server -- Voodoo display driver

```

The nouveau driver is just one of many drivers on your system, and it's perfectly safe to keep installed. The only issues that may occur would be to have the binary drivers (NVIDIA and ATI) installed on systems without the respective hardware, because they use different OpenGL libraries that interfere with Mesa/DRI in the open drivers.

---

### Post by ranch hand on 2010-03-01
If you go to synaptic and remove the ones you  do not need along with the meta package you will only receive updates on the ones you need.

I do that on stable OS'.  In testing I feel it is better to leave them to make sure they update correctly and so forth.

I also leave them on my single drive external enclosure as I lone it to other folks to try Linux with.  They will probably need a different driver than I do so I leave them all.  I also use it to boot to any old boxes that come my way.

This is the reason they are all there.  There is no way for Ubuntu to know what you are going to need so they throw in all of them.  This is part of the reason that Linux in general and Ubuntu in particular work out of the box, most of the time, on just about any computer.

---

### Post by SeePU on 2010-03-01
Does the ATI Radeon HD 4870 work well in Lucid?  How is the proprietary driver for you?

Can you watch videos and use Google Earth okay?

Anyone have a HD 5770 card?  I am wondering since I am pondering updating my GPU card to a Radeon card but I'm hesitant because it's ATI, afterall...;)

---

### Post by alphacrucis2 on 2010-03-01
> **SeePU said:**
> Does the ATI Radeon HD 4870 work well in Lucid?  How is the proprietary driver for you?

Can you watch videos and use Google Earth okay?

Anyone have a HD 5770 card?  I am wondering since I am pondering updating my GPU card to a Radeon card but I'm hesitant because it's ATI, afterall...;)


ATI haven't released a proprietary driver that will work with Lucid yet as far as I know. This seems to happen every cycle that an fglrx driver that works with the latest ubuntu comes out at the last minute before the ubuntu release.

---

### Post by Didius Falco on 2010-03-01
> **SeePU said:**
> Does the ATI Radeon HD 4870 work well in Lucid?  How is the proprietary driver for you?

Can you watch videos and use Google Earth okay?

Anyone have a HD 5770 card?  I am wondering since I am pondering updating my GPU card to a Radeon card but I'm hesitant because it's ATI, afterall...;)

The 4870 is working perfectly - I'm not using the  fglrx binary driver for ATI because it hasn't been released for Lucid yet, but the Devs are hard at work on it. I'm using the open source xserver-xorg-video-radeon driver. 

Videos play just fine, and so does Google Earth.

I hope this helps...

Regards,

Didius

---

### Post by SeePU on 2010-03-01
> **Didius Falco said:**
> The 4870 is working perfectly - I'm not using the  fglrx binary driver for ATI because it hasn't been released for Lucid yet, but the Devs are hard at work on it. I'm using the open source xserver-xorg-video-radeon driver. 

Videos play just fine, and so does Google Earth.

I hope this helps...

Regards,

Didius
It might help. :)   Is the open source driver aready installed or enabled or do you have to activate it somehow.  How would you switch back and forth if you wanted to try a 'new' driver?  Say, a new binary driver is released or it's beta or experimental and you wanted to try it out, how would you switch?  What's the steps?  What if the  new binary driver has bugs or you're not satisfied with the performance so you decide to go back to the open source driver?  Is it just the reverse steps and if so, what are they?

Answering those questions will help, I'm sure! ;)

My current card is an older generation Nvidia GF 7950 GT card so I'm not familiar with either ATI driver install, sorry. :)

---

### Post by Didius Falco on 2010-03-02
> **SeePU said:**
> It might help. :)   Is the open source driver aready installed or enabled or do you have to activate it somehow.  How would you switch back and forth if you wanted to try a 'new' driver?  Say, a new binary driver is released or it's beta or experimental and you wanted to try it out, how would you switch?  What's the steps?  What if the  new binary driver has bugs or you're not satisfied with the performance so you decide to go back to the open source driver?  Is it just the reverse steps and if so, what are they?

Answering those questions will help, I'm sure! ;)

My current card is an older generation Nvidia GF 7950 GT card so I'm not familiar with either ATI driver install, sorry. :)

The xorg driver is already installed - that's the 2D "basic" driver. you have to install the 3D driver. The easiest way is to go to System/Administration/Hardware Drivers and have it check to see if any drivers are available.

There is also a Help file available there. Here are a couple of relevant extracts from it:

> To use a proprietary driver for a device:

1. Press System &#9656; Administration &#9656; Hardware Drivers.

2. Find the driver which you would like to enable and read the description.

3. Press Activate to enable the driver. You may be asked to enter your password.

4. The  proprietary driver may have to be downloaded and installed.

5. You may need to restart your computer to finish enabling the driver.

If a proprietary driver is causing problems, or you would just like to turn it off, follow the procedure below:

1. Press System &#9656; Administration &#9656; Hardware Drivers.

2. Find the driver which you would like to disable and read the description.

3. Press Remove to disable the driver and continue using a free driver, if available. You may be asked to enter your password.

4. You may need to restart your computer to finish disabling the driver.

You can also (again, when it becomes available) download drivers direct from ATI and compile/install them. Things get a lot trickier if those drivers give you a problem.

Personally, I just use the Hardware Drivers version - a lot less hassle in the end.

Regards,

Didius

---

