---
title: "Video Driver on Cd no go"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by srlake314 on 2011-04-01
Hey all.

I just installed Ubuntu on my brand new system that I built.  I put in my cd for my HD 5770 video card, and an icon shows up on my screen XFX_VGA_V9.8C text under it.

However when I try to access it in anyway, I try to open with autorun prompt, I get a message "This medium contains software intended to be automatically started. would you like to run it?"

I click on run and get "Error autorunning software, cannot find the autorun program."

Is there anyway that I can run this disk.  It's important for setup.  I cant copy the disk to the desktop, I get errors.

Help!

---

### Post by dieselglock on 2011-04-01
Hello,

Did you try and go to applications/places/system menu and pick system/administration/hardware drivers menu and see if there are any video drivers there?

The disk you are trying to run is probably an .exe

Len

---

### Post by srlake314 on 2011-04-02
Isnt there a way to run it though as an exe in linux?

---

### Post by Frogs Hair on 2011-04-02
> **srlake314 said:**
> Isnt there a way to run it though as an exe in linux?

Yes , with a program called Wine , but I don't think it will work for installation software . To find a driver for your video card , Try System > Administration > Additional Drivers or Hardware Drivers.

Select it and Ubuntu will search for available drivers , it is usually best to pick the most current driver if more than one is offered .  Next it will install and you will asked to reboot.

---

### Post by srlake314 on 2011-04-02
I had tried copying the entire cd to my desktop, and then right clicking and checking the allow to run as exe.  It came up with errors.  I just want to make sure Im not missing any software for the Radeon HD 5770.

---

### Post by gordintoronto on 2011-04-02
> **srlake314 said:**
> I had tried copying the entire cd to my desktop, and then right clicking and checking the allow to run as exe.  It came up with errors.  I just want to make sure Im not missing any software for the Radeon HD 5770.

The disc contains Windows software, which is completely useless in Linux. Run Administration/Hardware Drivers to get the appropriate software for Ubuntu.

---

