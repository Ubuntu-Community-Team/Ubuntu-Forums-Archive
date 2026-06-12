---
title: "Getting temperature data from nvidia cards with nouveau"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmmL on 2010-03-09
Is there any way to acquire temperature data from the sensors on nvidia graphics card using nouveau? I'm loving the smooth startups and VT switching, but the proprietary driver allowed me to know the temperature of my card. Can this be accomplished with nouveau?

I need to keep an eye on this information; I have a 8600M GS which has nvidia's solder fault so I know that one of these days it will fail on me. Before the cards fail there seems to be a general trend towards overheating, so I'm hoping the temperature data will forewarn me.

---

### Post by Ichtyandr on 2010-03-09
I use xsensors it displays various data, perhaps you could give it a try, its in universe

---

### Post by jmmL on 2010-03-09
> **Ichtyandr said:**
> I use xsensors it displays various data, perhaps you could give it a try, its in universe
Thanks for the help, but it's not quite what I'm after.

xsensors uses data gathered by libsensors to *display* temperature information. That's fine, if the information has been collected in the first place. I need to collect the information, and for that libsensors has to be able to access my graphics card's sensors via a driver of some sort. The proprietary nvidia driver supports the collecting of this information - what I need is a way to get the information without using nvidia's binary.

---

### Post by Ichtyandr on 2010-03-09
> **jmmL said:**
> Thanks for the help, but it's not quite what I'm after.

xsensors uses data gathered by libsensors to *display* temperature information. That's fine, if the information has been collected in the first place. I need to collect the information, and for that libsensors has to be able to access my graphics card's sensors via a driver of some sort. The proprietary nvidia driver supports the collecting of this information - what I need is a way to get the information without using nvidia's binary.

I hope I got you correctly, xsensors relies on lm-sensors and works on nouveau. I use nouveau without proprietary nvidia drivers, and it shows voltages, temperatures (CPU and MB) and CPU Fan Speed.

---

### Post by alexmurray on 2010-03-10
libsensors doesn't interface with the proprietaty Nvidia driver either, instead the driver provides its own interface vis libXNVCtrl to access (or you can use nvidia-settings to query the temperature from the command line). Basically what's needed is for the nouveau driver to support reading this info (which I am almost 100% sure it doesn't) from the hardware and then a way for userspace to access this information from the driver - which could use the hwmon kernel interface and then libsensors would automatically support it without any need for an update... so in short talk to the nouveau guys directly about adding a hwmon interface to the nouveau driver.

---

### Post by francesco_m on 2010-03-10
> **alexmurray said:**
> libsensors doesn't interface with the proprietaty Nvidia driver either, instead the driver provides its own interface vis libXNVCtrl to access (or you can use nvidia-settings to query the temperature from the command line). Basically what's needed is for the nouveau driver to support reading this info (which I am almost 100% sure it doesn't) from the hardware and then a way for userspace to access this information from the driver - which could use the hwmon kernel interface and then libsensors would automatically support it without any need for an update... so in short talk to the nouveau guys directly about adding a hwmon interface to the nouveau driver.

Matthew Garrett proposed [1][2] a patch that adds basic support for reading the internal GPU sensor, but his work never reached nouveau due to licensing problems.

[1] [http://lists.freedesktop.org/archives/nouveau/2009-November/004083.html](http://lists.freedesktop.org/archives/nouveau/2009-November/004083.html)
[2] [http://lists.freedesktop.org/archives/nouveau/2009-November/004087.html](http://lists.freedesktop.org/archives/nouveau/2009-November/004087.html)

---

### Post by jmmL on 2010-03-10
> **francesco_m said:**
> Matthew Garrett proposed [1][2] a patch that adds basic support for reading the internal GPU sensor, but his work never reached nouveau due to licensing problems.

[1] [http://lists.freedesktop.org/archives/nouveau/2009-November/004083.html](http://lists.freedesktop.org/archives/nouveau/2009-November/004083.html)
[2] [http://lists.freedesktop.org/archives/nouveau/2009-November/004087.html](http://lists.freedesktop.org/archives/nouveau/2009-November/004087.html)

Thanks for the information everyone. I was just hoping I was missing something obvious, but I guess support for it will be a while. I don't get the licensing conflict - the code borrowed from nvclock was GPL - so surely this is fine to mix with the nouveau code which is also (presumably) GPL?

---

### Post by jmmL on 2010-03-10
Just spotted something that does 99% of what I want. Install nvclock and run```
sudo nvclock -T
```That will give you the temperature of the GPU. I think it's reporting the right temperature - although it's about 7C higher than usual at 74C. Not good.

Edit: Marking as solved.

---

