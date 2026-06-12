---
title: "After Install Ubuntu w/ Persist to USB - Runtime Extremely Slow Running"
date: 2017-09-30
forum: Installation &amp; Upgrades
---

### Post by drzale on 2017-09-30
Hello all. I've been using ubuntu to manage servers via ssh for a while but have little experience with actual installation / partitioning / live boot USB creation, please forgive my noobiness. My macbook pro 2013 early 2015 and the SSD died. In the interim, wanted to just use usb live w/ persistence for basic things, since I still have a desktop for any real work.

I created an initial USB boot from desktop 17.04 image with Live Linux USB Creator on Windows. It loads up like a charm on macbook, and works great, but there was no persistence. Next, I put another usb in (on laptop), and did the Install Ubuntu from desktop of ubuntu to load it on there. Thought this might make persistent by default? The first attempt, after loading up the "real" copy, I kept getting errors related to everything being read only. I thought it might just be a bad stick, and tried doing the same one a different one. This time, it loads up, and I havent seen errors but the UI is immensely slow, like click system config icon in top right, and wait a full minute just for sub menu to load.

After looking through so many guides, all with different recommendations, from manual partitioning (either 1 partition or 2), different versions/flavors of ubuntu, I'm more lost than ever. Anyone have an idea of what I'm doing wrong / or need to do different? Not looking for anything fancy, would be okay with even just the 4 GB of persistent as opposed to using the 16 GB drive was planning to. Any help much appreciated!

---

### Post by sudodus on 2017-09-30
Welcome to the Ubuntu Forums :-)

You have two alternatives

1. A **persistent live drive**, which boots and acts like a live-only drive, but with the additional feature to store installed programs and saved files in a casper-rw file or casper-rw partition.

2. An **installed system**, installed like an ordinary installed system, but installed into a USB pendrive instead of installed into an internal drive.

In both cases it is important to have a **fast USB 3 pendrive**, otherwise the system will be very slow. Often the flash memory hardware is the bottleneck, so a fast USB 3 pendrive will make a big difference also when connected via a USB 2 port of the computer. A hard disk drive is also an alternative (in an external box when connected via USB2 or USB 3.

See the following links, and links from them,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

[askubuntu.com/questions/786986/boot-ubuntu-from-external-drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

It is a good idea to use a flavour of Ubuntu with a** light desktop environment**, ultra-light Lubuntu, medium light Ubuntu MATE or Xubuntu. It will make things faster, particularly if you have only USB 2 ports on the server computers. You can even install Ubuntu Server into a USB pendrive.

Finally, please notice that the memory cells of a pendrive are more sensitive to wear than the magnetic layer of a hard disk drive or the 'better' memory cells of a solid state drive (SSD). There are tweaks to reduce wear at

[help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

---

### Post by C.S.Cameron on 2017-10-01
If there is no internal drive, boot the Live USB, plug in the target USB. When you get to "Installation type" select "Erase disk and install Ubuntu".

---

