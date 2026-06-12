---
title: "installing 11.10 on new laptop from DVD"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by pogo.possum on 2011-12-03
I am attempting to install Ubuntu 11.10 from a purchased DVD disk on a Toshiba Satellite Pro series 770 laptop.

I set the laptop to boot from DVD drive, and rebooted.  The initial screen appears, I enter English and Install Ubuntu.

The drive grinds for a while, then is silent.  The screen is black.
There is nothing on screen advising of installation progress.

Is this normal during the installation? If so, how long should the install take, so that I can know when I should give up on it.

---

### Post by oldtimer7777 on 2011-12-03
It would be better to create a Bootable Live USB Flash Drive of Ubuntu 11.10 to boot your computer from, and install it from the USB Live Flash Drive of Ubuntu 11.10.  It is really simple as long as you have another computer to use and to download and build your USB Flash Drive of Bootable Ubuntu and an internet connection, and naturally a USB Flash Drive.

You can create your own Bootable USB Flash Drive with the instruction on this page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

And here is a guide after you get that installed on your computer:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **pogo.possum said:**
> I am attempting to install Ubuntu 11.10 from a purchased DVD disk on a Toshiba Satellite Pro series 770 laptop.

I set the laptop to boot from DVD drive, and rebooted.  The initial screen appears, I enter English and Install Ubuntu.

The drive grinds for a while, then is silent.  The screen is black.
There is nothing on screen advising of installation progress.

Is this normal during the installation? If so, how long should the install take, so that I can know when I should give up on it.

---

### Post by pogo.possum on 2011-12-03
Yeah, tried that option last night. Downloaded iso from ubuntu.com, installed on my usb drive, set laptop to boot from usb, same result.  Reviewing the instructions at ubuntu.com, I see that the preparing to install Ubuntu screen never came up, so I guess I'm screwed :)

---

### Post by oldtimer7777 on 2011-12-03
> **pogo.possum said:**
> Yeah, tried that option last night. Downloaded iso from ubuntu.com, installed on my usb drive, set laptop to boot from usb, same result.  Reviewing the instructions at ubuntu.com, I see that the preparing to install Ubuntu screen never came up, so I guess I'm screwed :)

Instead of selecting install, just boot all the way in to the Live Desktop of Ubuntu and then select Install???

Can you get the live desktop to boot from the DVD or the USB?  You don't have to install it first to try it out as long as you boot from the USB or the Disc.

Just get it to boot for now to the Live Desktop and you should be OK.

---

### Post by pogo.possum on 2011-12-03
Nope, can't get to the live desktop either.  Trying linuxmint distro next, downloading it now

---

### Post by oldtimer7777 on 2011-12-03
> **pogo.possum said:**
> Nope, can't get to the live desktop either.  Trying linuxmint distro next, downloading it now

What are the specs, make model of computer you are trying to install Ubuntu Linux?

The more information the more we can try to figure out the culprit.

---

### Post by pogo.possum on 2011-12-03
Toshiba Satellite Pro model # 775D-S7330, screen res set to default of 1600 x 900.  I suspect a screen driver problem, since when ubuntu (also mint, for that matter), goes beyond the first couple of prompts, the screen goes black, although the usb thumb drive is still going.  Probably waiting for a result from a prompt that I can't see.

---

### Post by oldtimer7777 on 2011-12-03
> **pogo.possum said:**
> Toshiba Satellite Pro model # 775D-S7330, screen res set to default of 1600 x 900.  I suspect a screen driver problem, since when ubuntu (also mint, for that matter), goes beyond the first couple of prompts, the screen goes black, although the usb thumb drive is still going.  Probably waiting for a result from a prompt that I can't see.

AMD Radeon&#8482; HD 6520G
AMD Quad-Core A6-3400M Accelerated Processor
ATI graphics, ugh! Hate ATI. The worst graphics support when it comes to getting working in Ubuntu and Debian systems.. That could be your problem right there.  Overkill. I'm running last years model Toshiba. Cost around 350 from Fry's electronics.  But it has the recommended Intel Graphics that Ubuntu needs, and running Dual Core Intel Pentium. Want to trade it for something that works? Or maybe Ebay it, if you can't get it to take Ubuntu? It sells for around 550 new. 

Maybe someone here has more experience getting ATI graphics drivers working during installation of Ubuntu?? Maybe not.. :(

---

### Post by darkod on 2011-12-03
Have you tried downloading the Alternate Install CD (image) and burning a cd from it? The installer is text based and should work better for graphics related problems.

But on first reboot you might need to enter recovery mode (not the normal mode) to install the ATI driver.

I have a integrated HD3200 in my desktop mobo and after having some issues during 9.10 install it works fine these last few versions. You still need to install/activate the driver as soon as you boot first time but in my case at least it allows to boot so you can do that.

---

