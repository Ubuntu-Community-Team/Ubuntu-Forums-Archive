---
title: "[solved] Ubuntu livecd won't boot with Sony DRU-810a"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by wari on 2008-08-27
Today i had to install ubuntu (8.04 desktop) on a colleague's computer and i found the surprise that it didn't boot at all from livecd.

I tried changing some BIOS settings, the memory modules, flashing the motherboard bios, but either didn't work.

Suddenly i thought that it could be a optical drive issue. I tried disconnecting the flawed dirve and installing with an old spare CD-ROM drive, and it worked like a charm! :)

After installing the whole system and some additional software, I put back the original drive, but suprisingly again it didn't boot from the hard disk :(... WTF! I said my self.

The problem... FIRMWARE. The flawed drive had version 1.0a. I downloaded new firmware (version 1.0f) and booted onto windows (with the drive disconnected) and connected it after. To make it work, just go to the device manager and refresh the hardware list (something like "Find new plug-n-play hardware") and run the flasher app (downloaded from [http://sony.storagesupport.com/node/839](http://sony.storagesupport.com/node/839)) do a few clicks and wait a few seconds, and you're done.

Now you can reboot safely.

Comments? Questions?

---

