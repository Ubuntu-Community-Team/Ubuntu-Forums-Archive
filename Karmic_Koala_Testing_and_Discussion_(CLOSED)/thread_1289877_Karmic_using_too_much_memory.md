---
title: "Karmic using too much memory"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by viniciuscarvalho on 2009-10-12
Hello there! I've just got my Vaio FW465J which ships with a Radeon 4650.
As I could not wait for Karmic I tried the Beta version.

After installing it I tried to install Catalyst 9.9 from AMD drivers download. After installation, it crashed the system for good. Could not startup X server.

So, format the partition and tried again, this time not using the installer instead used the restricted drivers support of ubuntu. It installed the catalyst and everything was almost running ok.

Besides a few bugs from Avant-Window-Manager frozing from time to time, and eclipse not displaying a few panels and icons when using Extra Effects from Appearance. Everything was ok.

I'm running the 64bit version of karmic BTW.

Well, the first thing I noticed is that the effects are slower and not as smoother as they were on my previous older and with a simple Intel GMA graphics.

Second, When I try to change the appearance it takes a good time (from 10-15 seconds) and it closes all windows (it seems that X is restarted) something that did not happened on my old computer.

Also, I noticed that my ubuntu uses more resources than the Vista installed on it :(. Just to startup it eats up 700mb of resources, Xorg taking 200mb :O I wonder how could linux be using more memory than a windows distro.

I do not know if it is an issue with Karmic (beta version) or Catalyst, the 64bit version, or a combination of any of those.

Could someone please help me with this? Has someone here had problems with Catalyst drivers, does it worth to use them? I really do not want to use 1.3GB of my RAM just to read a PDF and have one window of firefox (my actual usage of memory)

Regards

---

### Post by sandyd on 2009-10-12
> **viniciuscarvalho said:**
> Hello there! I've just got my Vaio FW465J which ships with a Radeon 4650.
As I could not wait for Karmic I tried the Beta version.

After installing it I tried to install Catalyst 9.9 from AMD drivers download. After installation, it crashed the system for good. Could not startup X server.

So, format the partition and tried again, this time not using the installer instead used the restricted drivers support of ubuntu. It installed the catalyst and everything was almost running ok.

Besides a few bugs from Avant-Window-Manager frozing from time to time, and eclipse not displaying a few panels and icons when using Extra Effects from Appearance. Everything was ok.

I'm running the 64bit version of karmic BTW.

Well, the first thing I noticed is that the effects are slower and not as smoother as they were on my previous older and with a simple Intel GMA graphics.

Second, When I try to change the appearance it takes a good time (from 10-15 seconds) and it closes all windows (it seems that X is restarted) something that did not happened on my old computer.

Also, I noticed that my ubuntu uses more resources than the Vista installed on it :(. Just to startup it eats up 700mb of resources, Xorg taking 200mb :O I wonder how could linux be using more memory than a windows distro.

I do not know if it is an issue with Karmic (beta version) or Catalyst, the 64bit version, or a combination of any of those.

Could someone please help me with this? Has someone here had problems with Catalyst drivers, does it worth to use them? I really do not want to use 1.3GB of my RAM just to read a PDF and have one window of firefox (my actual usage of memory)

Regardsit ain't only you. also running catalyst + xorg and getting (see screenshot)
EDIT: filed bug
[https://bugs.launchpad.net/xserver-xorg-driver-vesa/+bug/450048](https://bugs.launchpad.net/xserver-xorg-driver-vesa/+bug/450048)

---

### Post by QIII on 2009-10-13
Hmmmm...

Interesting.  Just did a quick survey.  Xorg on my nVidia machines is taking about 1/10 the memory as is being used with ATI/Catalyst on that machine.

---

### Post by sandyd on 2009-10-13
you know....
its a bug in the ATI driver.
definately.
i had some time this morning so i decided to install the driver using envyng this time.
restarted and xorg squished into 150mb.
Ive also tried different drivers, but this option uses the least memory.

---

### Post by screaminj3sus on 2009-10-13
Why are you using cat 9.9, a beta in 9.10 is in the karmic repos and it works better with karmic.

---

### Post by viniciuscarvalho on 2009-10-13
> **screaminj3sus said:**
> Why are you using cat 9.9, a beta in 9.10 is in the karmic repos and it works better with karmic.

I am not. As I said, after the second installation I let Karmic "Memory Leaker" Koala install the driver. Today after using it for a whole day, after the end of the day I was using 2.8 GB even after closing every single application on my desktop.

Running free and vmstat displayed something around 1-1.5 GB of Shared + Cached memory, what about the others 1.2GB????????

So I finally removed the drivers from ATI. And run all applications I run during the day (Firefox, PDF Readers, Open Office, Eclipse, J2EE Servers, Virtual Box), at the end, after closing all apps, memory is only 580mb.

I'm not an expert in linux memory management, but anyone can see the problem here.

The problem is without the drivers I can't even run desktop-extras, and I really enjoy AWN and desktop effects.

I think I might try to go back to 9.04. So anyone has a better alternative, I don't want to install the system again :(

Regards

---

### Post by viniciuscarvalho on 2009-10-14
> **carlee said:**
> you know....
its a bug in the ATI driver.
definately.
i had some time this morning so i decided to install the driver using envyng this time.
restarted and xorg squished into 150mb.
Ive also tried different drivers, but this option uses the least memory.

Thanks for the hint on envyng. I used it as well. It installed the 8.6.xxx version of Catalyst. Now memory is back to normal, I opened several heavy memory applications, closed them, and got back to 700mb use of memory.

The only thing, is that with this new driver I'm not able to use the Virtual Resolution and have two monitors side by side. When I configure it on the display it asks me to logout but every time I come back, it is using mirror screens and not a side by side virtual resolution.

Also, amdccle (Catalyst Control Center) stop working:
Parse error on line 12 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.


Here's my Xorg.conf:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

Regards

---

### Post by QIII on 2009-10-14
Remember that you are using a Beta driver on a Beta OS.

The Xorg resource consumption issue seems to be the ATI driver not Karmic.

*nix does not manage memory the same as Microsoft OSs.  Memory "usage" may remain high even after everything is closed.  It is not "gone".  *nix is just holding it in an outstretched hand to pass off again as it is needed.  This is not necessarily memory leakage.

Not that memory leaks don't occur in *nix.  But in this case, if anything is leaking memory it is the driver, not Karmic.  You demonstrated that by removing the driver.

---

