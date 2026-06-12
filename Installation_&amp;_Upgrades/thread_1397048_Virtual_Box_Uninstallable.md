---
title: "Virtual Box Uninstallable?"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by treacle80 on 2010-02-02
Hi,

I am a bit of a newbie and i am trying to install virtualbox on Ubuntu KK to rum windowsXP.

I have downloaded the package from the repository but when loading I get the message:

Failed to create the VirtualBox COM object.
The application will now terminate.
Could not load the settings file '/home/martinbell/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.9-linux'.
The source version is not supported.

Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {3f4ab53a-199b-4526-a91a-93ff62e456b8}

Please can anyone help as this is driving me crazy!!

---

### Post by rogue_0111 on 2010-02-02
Try downloading directly from Sun.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by treacle80 on 2010-02-02
Hi Tried that it says there is a conflict with virtualbox OSM even though it is uninstalled

---

### Post by spcwingo on 2010-02-02
You can try renaming or deleting your .VirtualBox folder in your home directory.  After that try firing up VBox again from a terminal and post back the error output, if any.

---

### Post by kaminarisama on 2011-02-24
> **spcwingo said:**
> You can try renaming or deleting your .VirtualBox folder in your home directory.

This worked for me. I guess that I had some old settings in there.

Thx.

---

### Post by spcwingo on 2011-02-24
> **kaminarisama said:**
> This worked for me. I guess that I had some old settings in there.

Thx.

No prob, bro...glad to see you got it going.  Now I'm just wondering if the OP has his going too so we can mark this one as [SOLVED].

---

