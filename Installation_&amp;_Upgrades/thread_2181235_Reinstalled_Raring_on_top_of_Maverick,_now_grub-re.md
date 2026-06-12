---
title: "Reinstalled Raring on top of Maverick, now grub-rescue appears just after BIOS!"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by barrings on 2013-10-16
Hello,
A few days ago I decided to install Raring on top of Maverick due to some major software/hardware issues that appeared to require a more recent release to fix.  Now, just to be kind, my computer boots and displays the infamous grub-rescue prompt.  I have 2 HDDs, one with Windows (that's where I am typing this from) the other with Raring.  The installation of Raring was far from smooth (first it hung, then it threw an error message on the second-to-last step), and I guess the obvious first step is to completely wipe the installation and start from scratch.  But, anyway, I digress.  The situation became more inexplicable when I tried to boot to the Raring HDD.  I logically expected this to boot into Raring, but for some reason, threw me into Windows.  Since I only use Ubuntu once in a while, this was a pleasant surprise.

To make matters worse, my BIOS does not allow me to set my Raring HDD as the default boot device.  I have no idea why.  The result being that every boot I have to select it with the boot device selection menu during BIOS.  

Does anyone have any insights as to what's going on here, and how to fix it?  I would like, ideally, to see the GRUB boot menu after my BIOS completes, showing memtest86+, Raring and Windows as options.  After that, I would like to set GRUB to automatically boot into windows, but I'll cross that bridge later.

Thanks a lot in advance for any help.

barrings

---

### Post by fantab on 2013-10-17
How old is this computer? Have you considered a BIOS firmware update? You can do it by visiting your manaufacturer's website, download the latest BIOS firmware for your Board.

You say that you install didn't go well, have you considered that it could be the problem.. sometimes, if there is no boot flag on the the HDD then BIOS won't allow it to be set as booting device.

Boot your Raring DVD/USB and "Try Ubuntu Without Installing", connect to internet and install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"), then generate a **BootInfo-Summary** and post the generated link here (only the link). That should tell us what is going worng with you boot.

---

