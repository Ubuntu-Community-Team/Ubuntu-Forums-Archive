---
title: "VBox 3.2.10 usb?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by David52 on 2010-11-06
I run ubuntu 10.04lts (lucid lynx) and I have virtual box  installed. I have windows xp loaded inside vbox 3.2.10 it works but can't get to reconize the usb ports. I have folowed the steps in the guidelines, loaded by root DKMS programs inside windows, it does find the cdrom but no usb?What do I need to do please to get vbox pick up the usb ports?
david 52

---

### Post by lkraemer on 2010-11-07
There are two versions of VirtualBox, OSE (NO USB Support in the repo) and
PUEL (Downloaded from VirtualBox.org) that supports USB Devices.

Be sure that in Ubuntu you go to SYSTEM -> ADMINISTRATION -> USERS & GROUPS,
then scroll down to the VirtualBox group and check your name, then logout and
log back in Ubuntu.

If you installed the VirtualBox PUEL version (NOT the OSE Version) your USB
will work fine. You just need to create a filter so it finds the device,
when you start VirtualBox.  Scroll down to the USB setup portion.


Now when Windows is up and running Right Click on the USB icon in the
lower toolbar and check the one you want to use.

Just be sure to 1. REMOVE (unmount) the USB Device from within Windows when you are
done using it. I usually also 2. Right Click on the USB Icon in the Lower Toolbar
and UNCHECK the USB I'm done with.   ZIT-ZOT...Done! 

REF:
[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Be sure to also install Guest Additions if you are running Windows..

lk

---

### Post by David52 on 2010-11-07
Thanks for the info my friend. I will try this later sunday nite and get back with you. As for yur question on windows/ubuntu that is the way it is set up on duel boot. But I will be running VBox 3.2.10 with windows xp loaded inside. My version of ubuntu is only say 3 months old and I do run the desktop version. Got to go. Tks for the help and I will let u know wats up with the usb ports.
david

---

