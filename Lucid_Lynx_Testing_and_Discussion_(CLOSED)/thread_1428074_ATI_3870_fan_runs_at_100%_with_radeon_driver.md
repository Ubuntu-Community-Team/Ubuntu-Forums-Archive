---
title: "ATI 3870 fan runs at 100% with radeon driver"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewthomas on 2010-03-12
Is there any way to, when using the radeon driver, to control the fan speed?  

In karmic I use the fglrx driver in order to be able to get the temperature of the GPU and adjust the fan speed accordingly, but I don't know how, if possible, to do this with the standard open-source radeon driver.  

I'd like to be able to run lucid on another computer that has a PCI-E 3870 card in it, but having the fan operating at 100% is way too loud.

Has anyone else had any success with fan control when using the radeon driver?

---

### Post by andrewthomas on 2010-03-13
> **zika said:**
> Did You try with
Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"                       
in /etc/X11/xorg.conf...?
(If You're using open-source radeon driver...)

(WW)  RADEON(0): Option "ClockGating" is not used
(WW) RADEON(0): Option  "DynamicPM" is not used
(WW) RADEON(0): Option "ForceLowPowerMode" is  not used

lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD  3870 [1002:9501]

---

### Post by Melcar on 2010-03-13
Those options you got on your xorg.conf only work in UMS mode.  Lucid uses KMS for the driver by default, that's why you're getting those warning entries.  If you want to use those options, you need to turn off KMS; that is done by adding:

```
radeon.modeset=0
```

... to your kernel parameter line from the grub2 menu.  Said options only lower core frequencies and not the voltage, so your card may not get that cool even with the options on (therefore keeping the fan on high speeds).

The best option is to use KMS power management.  I don't know if Lucid's kernel can do it, but you can use either the 2.6.34 rc1 kernel or the latest 2.6.33 from the drm-next tree, both of which you can get [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").  Once installed reboot and go into the grub2 menu, select your kernel, press "e", find the line that begins with the word "linux", and append the following line to the end:

```
radeon.dynpm=1 
```

This method of power management works similar to the power management with fglrx.  To check if dynamic clocks are working, run the following command in a terminal:

```
cat /sys/kernel/debug/dri/0/radeon_pm_info
```

It should come back with a listing of frequencies and tell you whether PM (power management) is on or off.  It is also recommended that you have up to date driver builds from the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa").  While this does nothing for your problem of not being able to control the fan, it should give you lower GPU temperatures which in turn should slow down the card's fan.  Also, since this is still pretty "new", you may experience some problems.

---

### Post by andrewthomas on 2010-03-13
Thanks for your reply.

> **Melcar said:**
> The best option is to use KMS power management.  I don't know if Lucid's kernel can do it, but you can use either the 2.6.34 rc1 kernel or the latest 2.6.33 from the drm-next tree, both of which you can get [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/").  Once installed reboot and go into the grub2 menu, select your kernel, press "e", find the line that begins with the word "linux", and append the following line to the end:

```
radeon.dynpm=1 
```This method of power management works similar to the power management with fglrx.  To check if dynamic clocks are working, run the following command in a terminal:

```
cat /sys/kernel/debug/dri/0/radeon_pm_info
```It should come back with a listing of frequencies and tell you whether PM (power management) is on or off.  It is also recommended that you have up to date driver builds from the [xorg-edgers ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa").  While this does nothing for your problem of not being able to control the fan, it should give you lower GPU temperatures which in turn should slow down the card's fan.  Also, since this is still pretty "new", you may experience some problems.

I was busy installing the mainline 2.6.33 kernel when you replied.  I have the xorg edgers ppa enabled and the ```
radeon.dynpm=1 
```does not seem to work.  I have no /sys/kernel/debug/dri/0/radeon_pm_info just an empty /sys/kernel/debug/dri folder. Here is as some info from xorg.0.log.
I should probably try the 2.6.34 kernel, right?
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-020633-generic root=UUID=c08d5877-3960-44b5-b310-443b67b31f9d ro quiet splash radeon.dynpm=1
PCI:*(0:2:0:0) 1002:9501:1462:1200 ATI Technologies Inc Radeon HD 3870 rev 0, Mem @ 0xe0000000/268435456, 0xfdde0000/65536, I/O @ 0x0000bc00/256, BIOS @ 0x????????/131072
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 6.12.191
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) [KMS] drm report modesetting isn't supported.
(II) RADEON(0): Default Engine Clock: 800000
(II) RADEON(0): Default Memory Clock: 1126000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "radeon"
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Dynamic Power Management Disabled
```

---

### Post by andrewthomas on 2010-03-13
I now have the 2.6.34 rc1 kernel installed. 
> **Melcar said:**
> 
```
cat /sys/kernel/debug/dri/0/radeon_pm_info
```It should come  back with a listing of frequencies and tell you whether PM (power  management) is on or off.

```
$ cat /sys/kernel/debug/dri/0/radeon_pm_info
state: PM_STATE_ACTIVE
default engine clock: 800000 kHz
current engine clock: 297000 kHz
default memory clock: 1126000 kHz
current memory clock: 1125000 kHz
PCIE lanes: 16
```It should come back with a listing of frequencies and tell you whether  PM (power management) is on or off.
While this does nothing for your problem of not being able to control  the fan, it should give you lower GPU temperatures which in turn should  slow down the card's fan.  Also, since this is still pretty "new", you  may experience some problems.
It does not seem to have done much to the fan speed.  There may be something wrong with the card's BIOS. When I used the fglrx driver, the fan still would go at 100%.  The only way I was able to get it to slow down was using a script to run the aticonfig utility in a delayed loop to read the temperature and adjust the fanspeed.

Any more ideas?

---

### Post by ubfu on 2010-03-13
Having same problem with Ati card driver.

---

### Post by andrewthomas on 2010-03-13
Does anyone know how to read a video card's BIOS? Mine is an MSI RX3870-T2D512E-OC

---

### Post by Melcar on 2010-03-13
I only know how to do it under Windows with Radeon BIOS Editor; it lets you modify things like fan settings.  Most BIOS have a very lax fan setting (they don't rev up until the card hits like +90*C) so it's weird that yours is still at full speed, unless your card is seriously heating up.  Some older BIOS didn't have good fan settings and they would default to full speed, and the only way one could "fix" it was with software like with the driver or other programs.

---

### Post by andrewthomas on 2010-03-13
I'm not at the computer with the problem right now, but the last time that system booted into Karmic with the fglrx driver, before initiating the fanspeed script, the fan was full force and the temp was around 37 C. 
 
btw, I actually have another 3870 which is an ASUS model and will install it in the machine tonight to see if I can get some different results.

---

### Post by Pappulo on 2010-03-13
I have the same problem with my Ati Mobility HD 4570. Gpu Overheating and fan always at full speed. However, it works good with Seven.

---

### Post by Melcar on 2010-03-13
It depends on the particular BIOS.  I got two HD3850s from different vendors and the fan settings in BIOS are different; on is set to turn full speed at 80*C and the other does not have any options and just turns the fan at full speed regardless of the temperature.  My HD4850 BIOS sets the fan to turn on full speed not until 110*C .  
The open source drivers are barely getting proper dynamic clock switching, but I would think fan control to be close behind.

---

### Post by aviramof on 2010-03-13
how can i install ati driver for hd3650 512mb ddr2 agp card for lucid?

---

### Post by Melcar on 2010-03-13
AMD hasn't made available their driver that supports Lucid, I don't think.

---

### Post by andrewthomas on 2010-03-13
I just installed Lucid on the computer with the ASUS mobo below and the ASUS 3870 card is quiet. The problem is definately the MSI card. I just put all this extra info at the bottom so someone reading this thread can keep it straight. I think that I need to try and learn more about the Radeon BIOS editor that you were talking about and fix the MSI card. It really sounds a bit like a hair dryer.
 
 
 
 
**AMD Phenom 9500-MSI K9A2 CF w/AMD790X-ATI HD2600XT PCIe 512MB-4GB DDR2 800MHz RAM-250GB SATA HDD-320GB PATA HDD**
 
**AMD Phenom 9500-ASUS M3A32-MVP w/AMD790FX-ASUS EAH3870 512MB PCIe-2GB DDR2 1066MHz RAM-300GB SATA HDD**
 
**AMD 5600+64x2-ECS NFORCE6M-A - MSI RX3870 512MB-4GB DDR2 800MHz RAM-80GB PATA HDD**

---

### Post by Melcar on 2010-03-13
[http://www.techpowerup.com/rbe/]("http://www.techpowerup.com/rbe/")

If you got a spare Windows install.  You can use [GPU-Z]("http://www.techpowerup.com/gpuz/") to extract the card's BIOS and the use RBE to open it.  [Flashing]("http://www.techpowerup.com/articles//overclocking/vidcard/34/8") the card is rather simple too.

---

### Post by andrek on 2010-03-13
I don't suggest playing with gpu BIOS as it is very likely to screw things up if you don't particularly know what you're doing.

I personally gonna wait for the official ati catalyst [ fglrx ] release that supports the newest xserver OR 2.6.34 kernel and proper -ati drivers with power management support.

---

### Post by andrewthomas on 2010-03-13
> **Melcar said:**
> 
 
[COLOR=black][FONT=Verdana]If you got a spare Windows install. You can use [GPU-Z]("http://www.techpowerup.com/gpuz/") to extract the card's BIOS and the use RBE to open it. [Flashing]("http://www.techpowerup.com/articles/overclocking/vidcard/34/8") the card is rather simple too.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks for the info. Should be able to do something about it next week.[/FONT][/COLOR]
 
> **andrek said:**
> I don't suggest playing with gpu BIOS as it is very likely to screw things up if you don't particularly know what you're doing.
 
I personally gonna wait for the official ati catalyst [ fglrx ] release that supports the newest xserver OR 2.6.34 kernel and proper -ati drivers with power management support.
I understand that flashing any BIOS, let alone a gpu's is a risky proposition. Yet I am already running the mainline 2.6.34 rc1 kernel with little, if any, improvement in fan noise. Additionally, the ATI cayalyst drivers that I use in Karmic provided no help without a script to poll the gpu temp and adjust the fan speed. I am just too curious at this point to wait it out. If this was my only card, it would be a different story , but luckily it is not.

---

