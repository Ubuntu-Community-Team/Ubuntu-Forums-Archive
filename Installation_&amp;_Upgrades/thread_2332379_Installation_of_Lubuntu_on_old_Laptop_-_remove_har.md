---
title: "Installation of Lubuntu on old Laptop - remove hard drive?"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2016-07-31
Hi there,

I'm trying to intall Lubuntu on an old laptop to use as a NAS / web server / for general messing about.... The laptop is ancient, has 128mb ram and a 800mhz processor. It's running Win XP.

I have tried various installation methods without success:

- Unetbootin install to HDD (same partition as Windows - there is no other option in unetbootin) - The installation competes but no grub bootloader appears and the Laptop just boots into Windows.

- USB stick intallation has the following issues:[INDENT]- The laptop does not seem to boot my Lubuntu usb stick (which boots on all other boxes).
- I think the BIOS settings are correct, but the laptop keyboard doesn't work, so I can't change the BIOS settings anyway.
[/INDENT]

I know I could probably use the alternative installer burned to a CD, but I have no optical drive or media to hand.

I've decided what I need to do is:

(1) Remove the HDD from the laptop;
 (2) Attach it to my Lubuntu box via a usb caddy;
(3) Install Lubuntu on the HDD;
(4) Replace into laptop.

Is there a method for doing this? Or any method for doig the install via Windows (other than unetbootin which installs, butt won't show a grub menu).

Kind regards,

Steve

---

### Post by djchandler on 2016-07-31
You need more RAM, if you can find it. Try Star Micro ( [https://starmicroinc.net/](https://starmicroinc.net/) ), but it looks like your gear is too old even for them. Oldest laptop ram currently is DDR. You probably need SD ram. Otherwise, you'll need to run from CLI (no GUI).

Installing to your HDD on another computer probably will not work, unless all hardware is identical.

You may be able to use damn small linux, ( [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) ). The latest release is 8 years old, probably very vulnerable.

---

### Post by sudodus on 2016-07-31
I agree with *djchandler* that 128 MB RAM is not enough for Lubuntu.

What CPU is it, a Pentium III?

You can try a mini system with text screen installed from Ubuntu **mini.iso** or **Ubuntu Server**. You can also move the hard disk drive to another computer and install a [tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](https://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300) from a compressed image file, and then move the hard disk back to your old computer. Installed linux systems are more portable than we might think, at least as long as you do not install any proprietary driver.

You can also try some ultra-light linux distro, for example Tiny Core, Wary Puppy or TahrPup.

See also the following link about old hardware: [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by gordintoronto on 2016-07-31
Even if you can get some version of Linux running on 128 MB, it's not enough memory to run a web server, or much of anything. Add memory or trash the laptop.

---

### Post by yancek on 2016-07-31
> Unetbootin install to HDD (same partition as Windows - there is no other  option in unetbootin) - The installation competes but no grub  bootloader appears and the Laptop just boots into Windows.


What you describe above is referred to as a frugal install which basically puts the Live CD of Lubuntu on your windows partition.  There should be an entry in the windows boot menu for unetbootin and selecting that should take you to Lubuntu.  You can then use this as a Live CD, meaning a read-only filesystem on which no changes will be save on reboot or use it to install Lubuntu some where else.  Grub isn't used so you won't see a Grub menu.  With regard to the usb, do you know if the machine is even capable of booting from a usb?  Have you done it before?

---

