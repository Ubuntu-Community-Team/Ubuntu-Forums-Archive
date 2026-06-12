---
title: "Unable to install  on Dell XPs L702X"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by fsrepic on 2011-12-21
Hi forum,
 
I have recently purchased a Dell XPS L702X laptop running windows 7 ultimate. The laptop has two 500Gb HDD's that I have partitioned for various things under windows but I have left a 200Gb partition at the end of the second drive on which I would like to install Ubuntu 11.10.
 
Only problem is that when I try to install from CD drive I get the following error message after trying to load the CD driver:
 
sr 5:0:0:0: Attached scsi CD-ROM sr0
sr 5:0:0:0: Attached scsi generic type sg2 type 5
 
OR
 
udevd[125]: '/sbin/modprobe -bv pci:vxxxxxxxx' [184] terminated by signal 9 (Killed)
 
I have tried to load from a USB key as well and this gets a little further to the splash screen to choose to install or run from USB key and both selections end in the same result with the folowing error:
 
sr 5:0:0:0: Attached scsi CD-ROM sr0
sr 5:0:0:0: Attached scsi generic type sg3 type 5
 
followed by:
 
udevd[117]: timeout: killing '/sbin/modprobe/-bv pci:vxxxxxxxxxxxx' [190]
 
I can still break out of this and reboot so it's not completely hung up but it's not loading either.
 
Both sets of media have been independantly verified on seperate machines and run up fine so it would appear to be something peculiar with this laptop setup.
 
Any ideas would be appreciated.

---

### Post by gabethecabbage on 2011-12-21
Exactly the same problem here with a brand new toshiba satalite pro l770. I've performed many ubuntu installs before and so was surprised at how awkward this is proving.

Any help will be greatly appreciated.

---

### Post by Mustafa1 on 2012-01-12
I have the same problem with Toshiba laptop Satellite L770 I also tried Fedora 16 and got the same problem. It must be something wrong with the drivers for AMD APU's. Anybody figuered a work-around ....?

---

### Post by spawes on 2012-01-17
read [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) then

1. when you starting to boot from CD and see the picture, press any key
2. choose a language
3. press F6 and cross with space/enter button "acpi=off" (you need to try what else). Press Esc
4. Choose Install / try Ubuntu
5. after installation, try to boot in recovery mode. If fail, try boot option, for exaple "-- acpi=off", see Common Kernel Options in [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
6. install [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and try "Recommended repair"
7. if fail, try Boot-Repair -> Advanced options -> Grub options -> Add a kernel option: acpi=off or try to find out your own solution

So, my xps i starting now with acpi=off. By the time I will see If I need acpi=on.
This problem is probably caused by EFI mode in "new" bios in our laptops.

---

### Post by Ventolino on 2012-01-18
Thank you, the "-- acpi=off" let me install LinuxMint on my Dell XPS 17, both LinuxMint and Ubuntu hangs during instalation with the same problem

---

### Post by Ventolino on 2012-01-19
> **Ventolino said:**
> Thank you, the "-- acpi=off" let me install LinuxMint on my Dell XPS 17, both LinuxMint and Ubuntu hangs during instalation with the same problem

Today I upgrade the BIOS firmware, from my stock A14 version to latest A16 version from Dell support page, and it seems there is not need to do the "-- acpi=off" kernel option

---

### Post by sudarsun on 2012-01-29
Upgrading to A16 BIOS did not help for me.  I managed to boot only with the **nomodeset** kernel parameter.

---

### Post by sudarsun on 2012-01-30
Looks like the faulty **nouveau** driver is creating the fault during boot up.  Without **nomodeset** and/or **acpi=off**, booting leads to segmentation fault by the **nouveau** module.  When I disable the nouveau module by blacklisting it under **modprobe.d**, I am able to boot up cleanly using the **Intel Sandybridge Mobile** graphics driver.

```

filename: /etc/modprobe.d/nvidia-nouveau

# disable nouveau driver
blacklist nouveau
options nouveau modeset=0

```

---

### Post by YoungJules on 2012-01-31
Thanks sudarsun :KS, that worked for me on my new XPS L702X, which I *thought* would be a breeze to install!

Now at least it boots without having to specify acpi=off (which has consequences for multi-CPU detection and all kinds of other things too).

I just need to get rid of some 30 second pulseaudio/alsa hangs in the boot sequence... is making it take 1 1/2 minutes or more to boot.

Have you seen anything similar?

---

### Post by jerwilkins on 2012-02-11
Awesome thread all--the advice has been invaluable!

What might be the consequences of disabling the nouveau driver? Is it likely that this is something we'll be able to remove later?

Many thanks :)

---

### Post by sakuyaslove on 2012-03-01
How do you run the code referenced here?

---

### Post by jerwilkins on 2012-03-02
sakuyaslove, most of the options to get started can be set from the boot loader (using F6 per spawes's instructions).

Creating the /etc/modprobe.d/nvidia-nouveau can be done with ```
sudo nano /etc/modprobe.d/nvidia-nouveau
``` 
or 
```
gksudo gedit /etc/modprobe.d/nvidia-nouveau
``` for the GUI-inclined :)

Good luck!

---

### Post by sakuyaslove on 2012-03-02
Thanks.  I forgot my blank CDS today so I will try it when I get home and let you know how it goes.

---

