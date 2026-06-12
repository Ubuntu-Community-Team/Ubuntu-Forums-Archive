---
title: "CPU fan speed controller"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by ephexeve on 2010-12-16
Has anyone any program which can increse and decrease the CPU fan speed?
I already tried the lm-sensor, but didn't work for me.
Anyone?
Thanks in advance.

---

### Post by psusi on 2010-12-16
lm-sensors is pretty much it.  The kernel knows how to do it if your bios correctly implements ACPI, but unfortunately, most don't.  The fallback is lm-sensors and fancontrol.  Lucid and later kernels are more strict about drivers accessing IO ports owned by ACPI so you have to pass a boot parameter to allow the drivers lm-sensors uses to work correctly.  I'll try to look it up when I get home.  Something about acpi_lax_resources or so.

---

### Post by ephexeve on 2010-12-16
I stayed the whole night up trying to figure how that lm-sensors works.. 
But no effect.
Thanks

---

### Post by Frogs Hair on 2010-12-16
lm sensors only display information . Have you investigated why the fan seems to be running faster or are you just looking for fan control software ?

---

### Post by ephexeve on 2010-12-17
It's just the way it is.
When I used windows, I had a program called FanSpeed.
Which I could lower my fan speed, then my room would be quite.
I am just looking for a fan control, yes.
I tried my Bios using the Qfan (Asus), but then it not only lowers the speed of my CPU, but the speed of all my fans/coolers in it. I only want the CPU.
Just a fan controller software, all I need.
Thanks again

---

### Post by Frogs Hair on 2010-12-17
I searched for something like speedfan for Linux with no luck :however , I did find some scripts but they were 5 years old . Source Forge may a good place to look, there is a lot of software there and it takes a while to view it all.

---

### Post by Frogs Hair on 2010-12-17
This is one of many options I found at Sourceforge. [http://sourceforge.net/projects/fancon/](http://sourceforge.net/projects/fancon/)

---

### Post by ephexeve on 2011-02-01
That only check the temp

---

### Post by ntgoulart on 2011-11-25
I am looking for the same. Something that reduces the CPU fan speed.
Have you found anything yet?

---

### Post by NauTiluS1 on 2011-11-25
test with the fancontrol

is a program that is managed through a script.

more information, see "man fancontrol"

pd: I'm using google translator if not well understood.:)

my conf fancontrol

> INTERVAL=5
DEVPATH=hwmon0=devices/platform/w83627ehf.656
DEVNAME=hwmon0=w83627dhg
FCTEMPS=hwmon0/device/pwm1=hwmon0/device/temp2_input hwmon0/device/pwm2=hwmon0/device/temp2_input
FCFANS=hwmon0/device/pwm1=hwmon0/device/fan2_input hwmon0/device/pwm2=hwmon0/device/fan2_input
MINTEMP=hwmon0/device/pwm1=56 hwmon0/device/pwm2=39
MAXTEMP=hwmon0/device/pwm1=75 hwmon0/device/pwm2=58
MINSTART=hwmon0/device/pwm1=150 hwmon0/device/pwm2=75
MINSTOP=hwmon0/device/pwm1=0 hwmon0/device/pwm2=60
MAXPWM=hwmon0/device/pwm1=90 hwmon0/device/pwm2=255


sea

---

