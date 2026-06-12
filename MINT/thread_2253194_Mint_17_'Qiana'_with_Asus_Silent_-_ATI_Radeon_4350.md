---
title: "Mint 17 'Qiana' with Asus Silent - ATI Radeon 4350"
date: 2014-11-18
forum: MINT
---

### Post by idan_hahn on 2014-11-18
Hey,

I'm trying to Install 'Qiana' - (Mint 17 32bit cinnamon) on My old computer that runs with **Asus Silent - ATI Radeon 4350**. 
After installing I'm getting either black screen for normal boot or "safe mode style" with low resulotion and software video renderizing.
I tried implementing several solution I've found online but with no success.
The solution I rememebr trying:
1. download ATI software driver from ATI solution center - failed due to **lots** of incompetabilty issues with mint 17.
2. configuring Xorg file
3. removing  fglrx
and **MORE** but they're all failed and most of the guides are just incomplete or wrong.
Please, Can someone provide a full, well explained and working solution?
Thanks

---

### Post by ajgreeny on 2014-11-18
You will not be able to use the ATI/AMD proprietary driver for that 4350 or any 4000 series graphic card, so you are right to uninstall it.

You may have to use one or other of the available boot options to get to a desktop and then edit /etc/default/grub to make the option permanent.

I wonder if you requested to add third party packages and to update whilst you installed as that would account for the fglrx driver being added, even though it will not work; silly of the installer, I know, but that's what it does.

Regrettably I have no real experience of AMD graphics any more, so I don't know which boot option may be needed but have a good search and I imagine you may find it.  For nvidia cards **nomodeset** often gets to a GUI from which it's possible to sort out the problem easier than with a command line, so at the grub menu hit E to edit the line and replace the words **quiet splash** with **nomodeset** then hit Ctrl+X to boot.

---

### Post by coffeecat on 2014-11-18
*Thread moved to **MINT**.*

---

### Post by buzzingrobot on 2014-11-18
Pretty sure Cinnamon relies on hardware acceleration for acceptable performance. 

You can use the "nomodeset" kernel boot option. (Here's one of many howto's around the net: [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu).)  "Nomodeset" should allow the machine to boot up into a generic sub-optimal display.  At that point, launch Mint's "Driver Manager" (Menu -> Administration -> Driver Manager).  If drivers are available for it, select one and allow it to be installed. If one driver is recommended, use it.  I'd suggest opting for open source over any proprietary driver that may be listed.  Reboot to activate a new driver.

Be aware that a previous attempt to install a driver might interfere with this if that driver was incorrectly or incompletely removed.

---

### Post by idan_hahn on 2014-11-18
I've tried getting the Drivers from "Drier Manager" but there's no recommended drivers regarding radeon 4350 (there's no recommended drivers there at all)

---

### Post by QIII on 2014-11-18
Hello!

You are getting no recommendation for a driver because the only one that will work with your adapter, the open source Radeon driver, is already installed by default.

Cheers!

---

### Post by idan_hahn on 2014-11-18
That's bad news, does it means there's no hope for radeon 4350 with mint 17?

---

### Post by buzzingrobot on 2014-11-18
> **idan_hahn said:**
> That's bad news, does it means there's no hope for radeon 4350 with mint 17?

With Cinnamon?  Perhaps.

Try Mint's Mate release.  Mate does not require compositing or hardware acceleration, so it might be a better fit.

---

### Post by coffeecat on 2014-11-18
> **buzzingrobot said:**
> 
Try Mint's Mate release.  Mate does not require compositing or hardware acceleration, so it might be a better fit.

@idan_hahn, or try the Ubuntu version of Mate:

[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

Or try both. If they suit your hardware, you can see which you prefer.

---

### Post by Stinger on 2014-11-18
> **idan_hahn said:**
> That's bad news, does it means there's no hope for radeon 4350 with mint 17?

As QIII says, the opensource driver should work fine for you as it does for my radeon 4670.

try this command in terminal:
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type your password when asked for and post the output.
Maybe you have a conflict with an onboard graphics chip that can be disabled in BIOS ?

While you are at it, try this one too:
```
glxinfo | grep render
```
If it suggests you to install 'mesa-utils' just do it and run the command again.

BTW can we have all the specs of your PC, especially the motherboard  ?

---

