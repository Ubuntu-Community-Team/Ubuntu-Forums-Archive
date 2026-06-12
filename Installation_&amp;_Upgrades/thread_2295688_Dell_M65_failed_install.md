---
title: "Dell M65 failed install"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by Johnius on 2015-09-20
I'm currently running a Dell M65 and would like to install *buntu on it. I have attempted the install many times with different distros, versions, DVDs, USB, architecture, etc. etc. They all end the same way: Black screen power off. I've been able to get into the menus, but after selecting "Live", "Persistent", or "Install", things look okay for a little while, and then everything goes quiet. I'm getting to my wit's end since I've never had trouble like this before and all of my installation media works flawlessly on other hardware.

Is there a setting in the BIOS to disable other OS installs? Is there a way to have the bootloader write a log as to what the error might be?

---

### Post by grahammechanical on 2015-09-20
I am not certain but I suggest that you determine if the CPU is 32 bit or 64 bit. I think it is 32 bit because it is a Core Duo and not a Core2 Duo. You may need the i386 Ubuntu ISO image and not the amd64 ISO image.

[http://www.engadget.com/products/dell/precision/m65/specs/](http://www.engadget.com/products/dell/precision/m65/specs/)

[https://en.wikipedia.org/wiki/Intel_Core](https://en.wikipedia.org/wiki/Intel_Core)

Regards.

---

### Post by Johnius on 2015-09-20
I've used both types of images with the same result. The stickers on the chassis report Core2Duo. I checked the hard drive and the RAM for errors and found none. It's currently installing Windows XP flawlessly, which puzzles me even more.

---

### Post by Johnius on 2015-09-25
I pulled the hard drive and installed 15.04 on it and ran it perfectly on different hardware. Put the drive back in the laptop and magically didn't work anymore...

---

### Post by sudodus on 2015-09-29
I would try an older version of an Ubuntu flavour or re-spin with a lighter desktop environment than standard Ubuntu.

Lubuntu 14.04.1 LTS

LXLE 12.04.5

You may have problems with the graphics driver or wifi driver or with ACPI. In that case you can use a boot option, for example **nomodeset** or **acpi=off**

[BootOptions](https://help.ubuntu.com/community/BootOptions)

Please specify your computer! We know it is a Dell M65, but the hardware might be different from the standard.

- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier for us to help.

Maybe it works better with an ultra-light linux distro, for example Wary Puppy, TahrPup or Tiny Core.

---

### Post by Johnius on 2015-10-02
It's a core 2 duo with 4gb RAM. Graphics and nic are unknown as it will not boot. Older versions and lighter versions have the same problem. I believe Dell is responsible for locking all operating systems other than XP / Vista out at the BIOS level.

---

### Post by Geoffrey_Arndt on 2015-10-02
Dell has a ton of workstations and laptops certified for ubuntu and other linux distros.    They're actually more linux friendly than most other OEM's.

Did you try the nomodeset boot option suggested by Sudodus?    Any time I read about "black-screen" and power off/on that sends a signal about the graphics system.   When booting from nomodeset, you get a lower res display, but one that allows you to try the install of nvidia drivers via the official ubuntu repos (system settings>software & updates>additional drivers tab).

If using one of the other buntus (Ubuntu Mate is a good candidate) . . . be sure it's the 32 bit version also.   After trying nomodeset, trying an alternative 32 bit Ubuntu flavor would be my next option.

---

### Post by Johnius on 2015-10-04
I did try nomodeset with the same results. I'm using the Lubuntu text installer at the moment and it's gotten all the way to partitioning before it turns itself off. I almost got halfway through installing the base system once.

---

### Post by sudodus on 2015-10-04
Maybe the computer is overheated and turns off because of a lot of dust. Remove the dust (carefully to avoid static electricity) and try again.

There might also be a hardware defect, for example a RAM card or the motherboard might be bad. You can test RAM with memtest (that comes with the Lubuntu install iso file).

---

### Post by Johnius on 2015-10-05
> **sudodus said:**
> Maybe the computer is overheated and turns off because of a lot of dust. Remove the dust (carefully to avoid static electricity) and try again.

There might also be a hardware defect, for example a RAM card or the motherboard might be bad. You can test RAM with memtest (that comes with the Lubuntu install iso file).

I looked at both possibilities. I replaced the motherboard a month ago and ran memtest. It is currently running Windows 7 Home Premium 64-bit as flawlessly as an older computer can.

---

### Post by sudodus on 2015-10-05
Did you try the boot option **acpi=off** ?

---

### Post by Johnius on 2015-10-06
Yes

---

### Post by sudodus on 2015-10-07
- Maybe you should try with [many more boot options](https://help.ubuntu.com/community/BootOptions).

- Maybe you should test RAM with memtest.

- Maybe you have better luck with an ultra-light linux distro, for example Wary Puppy, TahrPup or Tiny Core.

- Maybe you can try knoppix. It is light but not ultra-light, and it is known to be good at identifying (and using) many hardware components.

---

