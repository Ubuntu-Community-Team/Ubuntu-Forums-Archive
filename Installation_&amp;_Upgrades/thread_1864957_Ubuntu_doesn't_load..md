---
title: "Ubuntu doesn't load."
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by MuzgontarAco on 2011-10-19
I just got a new laptop and can't load Ubuntu. It boots, loads the first menu but then when i click on try or install everything stops at:

[[img]http://www.shrani.si/t/2L/11p/yC5a9u/img20111017220054.jpg[/img]](http://www.shrani.si/?2L/11p/yC5a9u/img20111017220054.jpg)

When i first got a laptop i booted from an USB stick (ubuntu 11.04) with no problem, downloaded a Windows DVD and installed it. after a few days i decided to finally install ubuntu but it stopped there (the photo above). it happens the same with ubuntu (11.04 and with 11.10), kubuntu and xubuntu.

**[EDIT]** I installed 11.04 once but had all kinds of problems with it and could not boot into windows, so i had to farmat and clean install windows**[EDIT]**

Laptop:
Acer Aspire 5750G
Core i5-2430M
Nvidia GeForce GT 520M (or integrated)
4 GB DDR3 RAM

Sorry for my bad English but I'm tired and frustrated with this problem, and have no energy to google check my spelling ;P

i searceh for solution with no problem, if i missed something please point me there.

Thanks for any help you can give me.

lp aco

---

### Post by raja.genupula on 2011-10-19
Hi
  Have you tried installing ubuntu with different USB and different ISO's of Ubuntu.check your ISO's checksum for errors.

---

### Post by MuzgontarAco on 2011-10-19
i tried with USB, CD, DVD, installed under windows (installed in windows, but booted the same as in the picture). nothing worked.

sometimes i get this as well:

[[img]http://www.shrani.si/t/i/wB/5YgmT4i/img20111019211834.jpg[/img]](http://www.shrani.si/?i/wB/5YgmT4i/img20111019211834.jpg)

EDIT:
I even updated bios. it worked b4 installing windows but not now. (??)

EDIT 2:
checksum is OK

---

### Post by MAFoElffen on 2011-10-19
> **MuzgontarAco said:**
> i tried with USB, CD, DVD, installed under windows (installed in windows, but booted the same as in the picture). nothing worked.

sometimes i get this as well:

[[IMG]http://www.shrani.si/t/i/wB/5YgmT4i/img20111019211834.jpg[/IMG]]("http://www.shrani.si/?i/wB/5YgmT4i/img20111019211834.jpg")

EDIT:
I even updated bios. it worked b4 installing windows but not now. (??)

EDIT 2:
checksum is OK
So...

First: 
- Did it "Run" the Live Image when you selected the "try" option?
 -- I'm thinking that it didn't because you didn't know to use a start up for that chipset, "nomoseset"  To use that withe the LiveCD (cd or usb), boot > first screen is black with a person/keyboard (input) icon at the bottom. Press the escape key > That will bring up a keyboard selection box in low graphics. Press the escape or enter key > That will get to the advanced install menu > press F6. That will popup a dropdown menu for boot options. > Arrow down to "nomodeset" and press the spacebar. > Press ecape to leave that menu (keeps the selection(s) > Select Try without installing.

If that boots to a workable desktop, install from there. 

During the install process, there will be a menu that has 2 radio button on the lower half of that box saying "download updates while installing" and "download/install 3rd party software"... select both.

After the install process ends, it will ask you to reboot to finish the installation... DON'T YET.

Go to Places.  Find your installation dirve/partition- where it got installed and open it.  Doing this will mount it. This is an important step. 

Look in /etc/X11/ and see if an xorg.conf file exists... On the new Oneiric install process and those 2 radio button selections, sometimes it installs the video driver <> most times not.

Then open an editor (Applications > Accesories > Text Editor) and put this text into a new file.
```

options nouveau modeset=0

```Save as... Maneuver to your installed partition > go to /etc/modpobe.d/ and name the file nouveau-kms.conf

That will turn off Nouveau.  Nvidia and Nouveau don't play nice together and by the errors you posts, that seems extremely true on your hardware.

Reboot.  With Nouveau turned off, it should boot into the graphics in a VESA mode.  If not tell me and I explain how to boot with a "nomodeset" kernel boot option...  If it does boot, login > Look to right-most of the top desktop taskbar > click on the user_name > Select System Settings > Select Additional Drivers > Install your driver, which should be nvidia current.

Good luck.

---

### Post by MuzgontarAco on 2011-10-20
MAFoElffen new problem..
 first screen with a person/keyboard (input) icon at the bottom does not appear.. it did b4.. 

man I'm going nuts with this laptop #-o

EDIT:
found  an alternative

---

### Post by MuzgontarAco on 2011-10-20
[I]Could not save the file /etc/modprobe.d/nouveau-kms.conf.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


heeelp.. how to save this???[/I]

**EDIT:**
It works! thank you.. if i c you in person, I'll buy you a beer

---

### Post by MAFoElffen on 2011-10-20
> **MuzgontarAco said:**
> [I]Could not save the file /etc/modprobe.d/nouveau-kms.conf.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


heeelp.. how to save this???[/I]

**EDIT:**
It works! thank you.. if i c you in person, I'll buy you a beer
You're very welcome. Please use the thread tools and mark this "Solved."

---

