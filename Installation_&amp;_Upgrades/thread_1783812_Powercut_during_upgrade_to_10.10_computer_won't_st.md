---
title: "Powercut during upgrade to 10.10 computer won't start at all now"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Dunchillin on 2011-06-16
Hi all,
I was in the process of upgrading to 10.10 today and had got as far us unpacking packages with 29 minutes to go and my computer froze.  After about an hour and a half it was still frozen (still 29 minutes to go), so I restarted the computer...except it failed to restart.

I got a Ubuntu logo pop up and a few red spots light up underneath it, and then my name appears on the screen in a white box, but with nothing else to click.  I clicked on my name anyway and the writing changed to 'ubunto 10.10'.  There is a clock running (correctly) in the bottom right corner and when I hover on it the date pops up, so I seem to be somewhere desktopish, but there is nothing else on the screen, nothing to click, typing commands doesn't seem to do anything...and none of my files are, of course, visible either.

I tried to reboot from a cdrom but it didn't work.  When I looked in bios all my hard drives and disc drives were disabled and I can't seem to enable them.

Any help would be fantastic!  Please...

---

### Post by dozycat on 2011-06-16
Try to load the default configuration in the bios, and then try boot and load one of the old kernels from the boot menu.

---

### Post by Dunchillin on 2011-06-16
> **dozycat said:**
> Try to load the default configuration in the bios, and then try boot and load one of the old kernels from the boot menu.

Can't see **how **to load default config in bios! Tried loading from everythig on the boot menu and got the same screen, but this time I noticed this message pop up the the top right corner for a couple of seconds:

> 
"Configuration defaults for gnome power manager have not been installed properly. See your administrator"

---

### Post by dozycat on 2011-06-16
I thought your machine was stopping before trying loading the os. If you got  that message you said, you must be able to load from cd or usb to try repair from the menu of installation of ubuntu. Search how get the boot menu of your machine, sometimes is f8 when is  booting.

---

### Post by Dunchillin on 2011-06-16
Yes F8 is the boot menu.  But whatever I try to boot from (CDRom, HDD) it makes no difference, I end up at the same screen.  I found the defaults option in bios too but nothing change when I did that either.

The full message that pops up (now I've had time to read it 8 or 9 times) is:
> INSTALL PROBLEM! The configuration defaults for gnome power manager have not been installed correctly. Please contact your computer administrator

---

### Post by jerrrys on 2011-06-16
turn off ACPI ?  don't know if you can get there, but here's the link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

if this works, you will have to find a fix for acpi

---

### Post by dozycat on 2011-06-16
I believe  you already tried to boot with live 11.04 or 10.04?

---

### Post by Dunchillin on 2011-06-19
Hi all,
Finally managed to get in via usb and install 11.04.  But now having done that I'm not sure it really is 11.04!!  I say this because my desktop looks nothing like the online screenshots of Unity...looks more like a spectrum zx interface!  Have I done something wrong?

---

