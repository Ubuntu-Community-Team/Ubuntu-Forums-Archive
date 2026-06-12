---
title: "Black screen in Lucid Beta 2"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rdunton on 2010-04-11
My computer is booting up into the logon screen.  However, once I enter my password, I hear the logon sound but the desktop does not display.  If I enter failsafe graphics mode, it works and goes to the desktop.  Apparently it must be a graphics driver issue, but I am not sure how to fix it.  Ubuntu 9.10 worked fine on this computer.  My computer has an ATI Radeon Xpress 200 graphics adapter.  Thanks in advance for any help.

---

### Post by dino99 on 2010-04-11
is it a fresh install or an dist-upgrade ?
by default Lucid dont need xorg.conf, so rename it if you want to keep it or simply remove it.

If you search on forums you will find lot of trouble with ATI cards. Looking at your card maybe you will find usefull comments.

You can check: system -- admin -- hardware drivers to see if your driver is detected and activated.

you can try with synaptic to remove/purge your driver then reinstall it.

Of course, viewing logs (system admin log viewer) will give you some usefull indications.

---

### Post by rdunton on 2010-04-13
*bump*

---

### Post by rdunton on 2010-04-13
My installation of Lucid was an upgrade from Karmic.  My video worked fine in Karmic, but as I mentioned in my first posting, it does not work in Lucid unless I go into recovery mode and use the failsafe graphics mode.

> You can check: system -- admin -- hardware drivers to see if your driver is detected and activated.

I checked that and it tells me that there are no proprietary drivers in use on this system.

---

### Post by rdunton on 2010-04-16
Bump

---

### Post by iClouseau88 on 2010-04-16
I have the same video card.  Here's how I solved my problem:

1. When the Humanity theme first appear, hit the spacebar;
2. Installation boot menu appears, hit F6;
3. Popup shows "acpi=off", "noapic", "nomodeset" and other items but just select these 3 using arrow and ENTER keys individually;
4. You may also want to hit F3 to select video mode i.e. 1024x768 or 800x600 otherwise a very fine screen resolution is very hard to read;
5. Type vga=792 on the BOOT window: Boot= vga=792 acpi=off noapic nomodeset;
6. Press ENTER

---

### Post by rdunton on 2010-04-16
I solved my problem with a clean install, but that isn't very good if people are going to need to do a clean install on their systems to get it working properly.  I have read on these forums that many people just upgrade their systems as I did, but this time it seems it may not work properly with some video cards, especially some of the most popular video cards.  I have seen problems with ATI and NVidia, the two largest video card manufacturers.

---

### Post by QwUo173Hy on 2010-04-16
You upgraded to an 'under construction' release, so hopefully people won't be affected by this issue come final release on April 29th.

Were you prompted by the package manager to upgrade or did you just do it on your own initiative? I wouldn't like to think that people can accidentally upgrade to a beta through the gui.

---

### Post by jerrylamos on 2010-04-17
> **rdunton said:**
> I solved my problem with a clean install, but that isn't very good if people are going to need to do a clean install on their systems to get it working properly.  I have read on these forums that many people just upgrade their systems as I did, but this time it seems it may not work properly with some video cards, especially some of the most popular video cards.  I have seen problems with ATI and NVidia, the two largest video card manufacturers.

In running pre-Alpha's, Alpha's, and Beta's usually upgrade works for a while but then things happen and a re-install from daily build gets me going again.  I dual boot so re-install is no big deal, just install in another image and copy over anything needed in the updated version which is ill.

Cheers, Jerry

---

### Post by QwUo173Hy on 2010-04-18
Hi Jerry. In spite of the 'official' standpoint, my experience in the past with linux in general is that a fresh and up to date install can iron out some problems. I've been practicing this for so long now that I wouldn't actually notice if it's no longer necessary - I don't give upgrades a chance really.

I'm curious, do you experience this much?

---

