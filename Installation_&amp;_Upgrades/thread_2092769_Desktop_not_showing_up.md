---
title: "Desktop not showing up"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Dexy on 2012-12-08
Hello,

I installed ubuntu with no errors but when i get to log on screen i enter my password and hit log in but destop is not showing up ... i see only background ...

Also i tried to boot only from my usb and also desktop is not showing then i tried with "nomodeset" to boot from usb and that works ...

Then i reinstalled ubuntu with "nomodeset" checked but still desktop is not showing ... i think i need to set "nomodeset" manually again but i don't know how...

---

### Post by darkod on 2012-12-08
In the grub boot menu, highlight the ubuntu entry, hit 'e' for edit. That will show the boot lines. Use the arrows keys to position the cursor towards the end of the line starting with linux. After the 'quiet splash' add nomodeset.
Hit Ctrl + X or F10 to boot.

It should boot correctly. When it does, open the Dash (ubuntu logo icon in the Unity interface) and in the search line look for Additional Drivers.

Once you open that it should offer a video driver that you can activate. After that it should work without entering nomodeset every time.

---

### Post by Dexy on 2012-12-08
How to get in grub menu?

---

### Post by LuisGMarine on 2012-12-08
> **Dexy said:**
> How to get in grub menu?

When the computer is booting up, hold the SHIFT key.  This will grant you the access to the GRUB menu.

---

### Post by Dexy on 2012-12-08
Thanks, i entered but when i type that in search it says to me "Sorry, there is not..."

---

### Post by darkod on 2012-12-08
It doesn't find the additional drivers application or it doesn't show a driver inside it?

And which ubuntu version are you installing?

---

### Post by LuisGMarine on 2012-12-08
> **Dexy said:**
> Thanks, i entered but when i type that in search it says to me "Sorry, there is not..."

You must be using Ubuntu 12.10?  If this is the case then you are going to need to do the following steps instead.

Open up your system settings, Software Sources, and there should be a tab at the top that says something along the lines of "Additional drivers ..."

Click that tab and install the corresponding driver, nvidia or ATI.  I recommend doing the one labeled nvidia-current since it is more stable.  But if you have a newer card you might need the nvidia-current-updates.  I'm sorry but I don't have any experience with ATI cards, hopefully someone else can chip in.  :lolflag:

---

