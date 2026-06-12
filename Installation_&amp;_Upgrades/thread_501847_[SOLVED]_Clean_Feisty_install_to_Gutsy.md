---
title: "[SOLVED] Clean Feisty install to Gutsy"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-07-15
OK boy oh boy I'm confused.

After a week of trying to get a Canonical issued Feisty (desktop cd) to install and run the cdrom, it did. Now I'm using  the Gutsy to upgrade in hopes of getting wireless up & running swiftly, as this is a "friends" computer. His xp died and I convinced him to try linux.

This is a Toshiba Satellite 1905-s304 laptop.

As I type, Feisty is using the Gutsy desktop cd to upgrade 763 packages. This is not the first time I tried this. It's the 3rd. Never mind!

Once this is upgraded, will it have "sense" of a Linksys WUSB11v4 usb wireless adapter? The adapter is using one of the 2 usb ports.

What steps will I have to take to get the wireless part up & running? I already had Synaptic Package mgr. install ndiswrapper/utils.

---

### Post by rjfioravanti on 2007-07-15
you can type 'lsusb' into terminal to make sure its even recognized

after that you can google around or use these forums to search for instructions on the specific name of the wireless usb device

You will probably need to find the XP windows driver for the device, and you ndiswrapper to get the card working

most usb devices dont have native linux support... so we use the ndiswrapper

good luck!

--- ps... giving your friend gutsy as a "conversion attempt" may not have been a good idea, he is going to get lots of updates on a regular basis, and it will be hard to show him with an alpha version of the OS that it is a good idea

---

### Post by rjfioravanti on 2007-07-15
sorry i didnt see you said you already install ndiswrapper

Try to find ndiswrapper instructions specific to your device

If you cant then just use the most generic instructions you can find

this one here looks right
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Mark_in_Hollywood on 2007-07-25
THREAD CLOSED


I have reinstalled Feisty

---

