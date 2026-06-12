---
title: "VBOX OSE - Error"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by westony on 2010-02-03
> Failed to create the VirtualBox COM object.
The application will now terminate.
Could not load the settings file '/home/martin/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.9-linux'.
The source version is not supported.


Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {3f4ab53a-199b-4526-a91a-93ff62e456b8}



Any one know how to fix this ?

---

### Post by drwmir on 2010-04-15
Hi,

had the same problem, found a solution:

Just delete the .virtualbox folder and start virtualmachine again. Should work.

Ciao

Attention: every parameters of vm will be deleted

---

### Post by isbiyanto on 2010-04-15
yeah...
just delete, it's work for me too, thanX

---

