---
title: "New install of lubuntu on Acer: trackpad doesn't work"
date: 2017-06-03
forum: Installation &amp; Upgrades
---

### Post by youlookgreattoday on 2017-06-03
I installed lubuntu this morning on an Acer Aspire One cloudbook model a01-131-c7dw.  The trackpad does not work and I'm currently using a mouse.  I've read the following posts and page

[SOLVED] Ubuntu 16.04 Touchpad not working
[SOLVED] Touchpad doesn't work and doesn't shutdown
SynapticsTouchpad official Ubuntu documentation ([https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad))

Using xinput list, it doesn't appear that my system identifies a trackpad as existing as the output lists:
Virtual Core Pointer id=2
Virtual core XTEST pointer id=4
Microsoft Compact Optical Mouse id=10

I've attempted to reinstall the synaptics drivers (sudo apt-get install xserver-xorg-input-synaptics) but the system tells me I already have the latest version (1.9.0-lubuntul)

While the SynapticsTouchpad page has a section on "Determine whether a touchpad has been detected" it doesn't really say what to do if there wasn't one detected and there is no ADBmouse detected.

I'm trying to set this up as a netbook for my wife and really need the trackpad to work.  Any help you can provide would be greatly appreciated.  NOTE: I am *not* competent in linux / lubuntu, so please consider that as you request information or suggest commands / actions.  Thanks!

---

