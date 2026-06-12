---
title: "Ubuntu 11.10 black screen on boot"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by tuanita on 2012-03-07
Dear,
I've been trying to install Ubuntu 11.10 for the last 3 days in a row and i get stock on boot, cant go any further . My laptop configuration is:
I have an Hp Pavilion6 6149sf
PROCESSOR: AMD A6-3410MX (quad core)
RAM / 6GB
GRAPHICS: AMD RADEON HD 6750M / AMD Radeon (TM) HD 6520G (dual graphics)
HDD: 750GB

I've tried installing through dvd drive, a usb and still I get the same thing with both. I need help.
thanks in advance

---

### Post by tuanita on 2012-03-08
166 views and no one has to say nothing !!!
:confused:

---

### Post by WthIteh on 2012-03-08
Can you see the initial menu showing options for "trying without install", "install ...", etc.? And screen goes black afterwards, or it's black from the beginning?

My guess is that the problem is due to "dual graphics" which is not well supported yet. Try to disable the dual graphics from BIOS before booting from CD and then try it again.

---

### Post by tuanita on 2012-03-08
> **WthIteh said:**
> Can you see the initial menu showing options for "trying without install", "install ...", etc.? And screen goes black afterwards, or it's black from the beginning?

My guess is that the problem is due to "dual graphics" which is not well supported yet. Try to disable the dual graphics from BIOS before booting from CD and then try it again.

Yeah i wish i could disable dual graphics but there's no such option!

---

### Post by MAFoElffen on 2012-03-08
> **WthIteh said:**
> Can you see the initial menu showing options for "trying without install", "install ...", etc.? And screen goes black afterwards, or it's black from the beginning?

My guess is that the problem is due to "dual graphics" which is not well supported yet. Try to disable the dual graphics from BIOS before booting from CD and then try it again.
@WthIteh
Bingo. But really not as bad as Optimus.

Once installed, then boot to recovery > select "root" and install ATI Catalyst drivers.

Read this: [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

ATI seems to be one-up on nVidia, as their Linux drivers do support hybrid-graphics.

Thing is to get the system installed. Some users can do it via using nomodeset or radeon.mode=0... other users have to install with the Ubuntu Alternate Install disk.

If you can install from the LiveCD using "try" then install from the desktop... then you have a chance "delay" the reboot after the install by just openning the browser and downloading your drivers to your filesystem, before you reboot.

The ATI Catalyst Settings utility does have a setting for turning the discreet chipset on/off.  It appears only it the hardware it is installed on says it's there.

---

### Post by pavi_elex on 2012-03-09
Try to boot from .iso file.

---

### Post by pehden on 2012-03-16
I got the same issue, Aspire 7560-Sb416   black screen on boot, the LED back light doesnt even turn on. I have to use ubuntu 10.04 just to get it on. 


AMD Radeon HD 6520G w/512MB Ram cant install latest version.

---

### Post by bdflex on 2012-03-19
I have an hp g60-235dx with intel graphics and have been messing with ubuntu 11.10 for the past 2 days. I have tried nomodeset, i915.modeset=1, and i915.modeset=0. It either boots into a blank screen, gets a kernal panic, or gets a bunch of errors on the text screen thats too much to list. I'm using the try ubuntu feature. Now I'm stuck. Any ideas on what i should try next?

---

### Post by pehden on 2012-04-03
> **pehden said:**
> I got the same issue, Aspire 7560-Sb416   black screen on boot, the LED back light doesnt even turn on. I have to use ubuntu 10.04 just to get it on. 


AMD Radeon HD 6520G w/512MB Ram cant install latest version.



My work around was to install 10.04 and install the drivers for the AMD card, then upgrade, run recovery mode do reconfigure video drivers, reboot
worked, upgraded to 11.04 then reinstalled AMD drivers via failsafe graphics boot then worked.

---

### Post by raja.genupula on 2012-04-03
> **pehden said:**
> My work around was to install 10.04 and install the drivers for the AMD card, then upgrade, run recovery mode do reconfigure video drivers, reboot
worked, upgraded to 11.04 then reinstalled AMD drivers via failsafe graphics boot then worked.

for better Help , its better to create a new thread .

---

