---
title: "Confirming 12.04 Install Image Fails to Boot on Nvidia Card"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-05-01
This has been reported elsewhere, and bug reports filed, but I can confirm that the 12.04 iso image (burned on a USB stick in my case) won't install if there is an Nvidia GTX-550TI in the slot.

Here is what I see:

1. Loading operating system...
2. Purple screen, for a very few seconds.
3.  Black screen, cursor flashing
4. Disk activity light flashes off and on for 20-30 seconds
5. Disk activity stops flashing, screen still black with cursor

I want to stress that no Grub menu is displayed. There is no way to edit the kernel options or get to a shell.

The same image on the same USB stick works with no issues with an AMD card in the slot.

I believe this is a problem with all 3.2-3.3 kernels. 

Does anyone know if Ubuntu is going to patch their kernel and update the download image?  This problem means a large number of Nvidia owners cannot install 12.04.

---

### Post by RobinSchouten on 2012-05-01
Hmm... I'm experiencing something similar to this using a GTX 580. 

What happens when you don't select live mode, but just go straight to install on hdd?

---

### Post by buzzingrobot on 2012-05-01
> **RobinSchouten said:**
> Hmm... I'm experiencing something similar to this using a GTX 580. 

What happens when you don't select live mode, but just go straight to install on hdd?

I don't get that far.  The only thing I see on screen is a cursor.

---

### Post by jefsview on 2012-05-01
I had troubles as well with a GTS 450, but it also wouldn't let me install other OS's, either, like Crunchbang (debian). 

I figured it was because my 450 GTS doesn't have a dedicated power supply, since it was not being detected.

I threw in my older 9800 gt with dedicated power supply and didn't have a problem. After install, I simply switched them out and re-installed the drivers.

-- Jeff

---

### Post by buzzingrobot on 2012-05-01
> **jefsview said:**
> I had troubles as well with a GTS 450, but it also wouldn't let me install other OS's, either, like Crunchbang (debian). 

I figured it was because my 450 GTS doesn't have a dedicated power supply, since it was not being detected.

I threw in my older 9800 gt with dedicated power supply and didn't have a problem. After install, I simply switched them out and re-installed the drivers.

-- Jeff

From what I can find out, it seems to be in the kernel.  There have been bug reports here and it was a discussed  on the Fedora boards, where it affected the kernel in their Fedora 17 beta and a kernel they put out in Fedora 16 updates. They've done some kind of a patch.  (Here's one thread: [http://forums.fedoraforum.org/archive/index.php/t-277242.html]("http://forums.fedoraforum.org/archive/index.php/t-277242.html") From that, it looks like the installer recognizes the Nvidia card, then tries to load the open source Nouveau driver, and everything crashes.)

My plan, if I got to Grub, was to tinker with kernel options and get the thing to work, do the install, and then grab the closed driver.

I wonder if there's a fixed kernel out there and if there's a way to use it to build a new install image, rather than wait for the updates to come out?

Right now, I'm sitting here installing Debian Squeeze, which uses a 2.6 series kernel, and all is going well at the moment.

---

### Post by buzzingrobot on 2012-05-01
Ok, I'm gonna let this Debian install finish, but then I'll try to install from the alternate text-based image. If that goes belly up, I'll try an 11.10 install and the upgrade.

---

### Post by buzzingrobot on 2012-05-01
Success.

First, Debian Stable installed with no problems, confirming that the hardware was OK.

Trying to install the alternative text-only 12.04 image failed with the same symptoms mentioned earlier in this thread.

I successfully installed 11.10, from a USB stick.

Then, I ran Update Mangager to update 11.10.  I made sure Nvidia's driver had been installed.  Checking Additional Drivers showed it had been. The Update Manager offered to upgrade to 12.04. I declined at that point.

I edited Grub's command line to include "acpi=off no_apic" and ran update-grub.  I don't know if that was necessary, but fingers have pointed at acpi as the culprit.

Ran Update Manager and accepted its offer to upgrade to 12.04. After 45 minutes and 1486 files the machine booted into 12.04.

I removed what I'd added to grub's command line, ran update-grub, and rebooted.  Successfully.

I think I have a few services running that I don't need.  But the monitor is running at the correct resolution and, so far, everything is working. Yay.

---

### Post by RobinSchouten on 2012-05-01
Nice going! Some people will greatly appreciate your workaround!

I, however, will wait for Canonical to fix this in the official Ubuntu image.

---

### Post by buzzingrobot on 2012-05-01
I read about the problems with Nvidia cards one day after I'd ordered this card.  It's got a reputation as a quiet card and I wanted to replace the noisy AMD card in that machine.  Hence, the stubbornness. The card really is quiet, too.

I believe the plan is to release kernel updates 3 weeks after 12.04's release, which would be in mid-May.

---

