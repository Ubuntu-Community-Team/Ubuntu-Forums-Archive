---
title: "Graphics issues so cant install"
date: 2019-12-03
forum: Installation &amp; Upgrades
---

### Post by urumiko2 on 2019-12-03
Hi I am trying to resurrect a vista based
Compaq Presario v6000 laptop.
To use as a basic web machine for my workshop.


Installing
lubuntu-19.04-desktop-amd64 from USB


Hardware is nforce 630M/GeForce7150m based
1280x800 display
and a broadcom B/g wifi card


The Boot menu loads fine, but if i progress to load the live desktop environment, it seems to make it to the desktop but the display is messed up. it looks like the screen is chopped in to segments and ghosted over itself. I cant see anything to try and rectify the issue.
if i try the Ubuntu installer this experiences the same Graphical issues right from boot.


I can get a console window using shortcut keys but its hard to read.. and i cant see what ive typed without hitting return a few times


I can blindly set the Resolution using xrandr. and while this does seem to do something, It doesnt fix the issue.
If i use the autoconfig flag in xrandir I get the "hourglass" and the machine seems to crash.




I'm thinking i may need graphics drivers.
I can download the drivers to the USB on another machine which come in a .run format but I have no idea how to load them.


I am completely new to linux more or less.


Suggestions?
Cheers.

---

### Post by mörgæs on 2019-12-03
Hi and welcome to the fora.

Normally people should go for the latest available Buntu version but in this particular case I suggest trying 18.04.3. 

The Nvidia 7xxx graphics cards *might* need (I'm not sure - a test will show) closed source drivers which are not available in later releases. Do you get a better result with 18.04 if you add closed source drivers as soon as you see the option?

---

### Post by artelius on 2019-12-03
can you post a photo of your screen?

---

### Post by rsteinmetz70112 on 2019-12-05
Which processor and RAM do you have? 
There were several versions with different processors, even a couple with Intel processors.

Typically Ubuntu will attempt to use the open source nouveau driver, it usually works OK although does have some issues.
There is also a generic vesa drivers which offer fewer features.
You may need some boot options to get the driver to load and work correctly.

Closed source drivers are available but may require some special installation of a chipset this old.

---

### Post by urumiko2 on 2019-12-05
HI all, I'll try and answer all together:

I tried [COLOR=#000000]18.04.3,  no difference

Here is a photo: [/COLOR]https://photos.app.goo.gl/PHvV5ahSaxPtXFpF9

It's actually a Presario V6500

Processor is an AMD TUrion 64 X2 Tl-59 1.9ghz

2GB Ram

I notice vista (installed)  is 32 bit.

I dont know how to add the CLosed source drivers?

---

### Post by mörgæs on 2019-12-06
> **urumiko2 said:**
> 
I dont know how to add the CLosed source drivers?

The option should be presented to you as part of the installation process.

---

### Post by urumiko2 on 2019-12-07
In the boot menu there is a Load 3rd party driver disk option or something on the F4 key but pressing it does nothing. THen if i continue to boot in to the installer i get the same graphical issues.
I would have thought there should be a way to boot to the command line without loading the desktop environment so i can install the drivers?

---

### Post by mörgæs on 2019-12-08
Yes, one can install a text-only system using the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD").

---

### Post by urumiko2 on 2019-12-10
Surely there must be a start up peramiter or file on the usb that i can alter that says don't load the gui?
Id be happy to read up on the relevant stuff myself if someone knows where or what I should look for in the documentation?

---

