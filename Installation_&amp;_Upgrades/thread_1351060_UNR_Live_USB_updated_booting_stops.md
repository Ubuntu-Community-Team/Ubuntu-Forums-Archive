---
title: "UNR Live USB updated: booting stops"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Tux@Linux on 2009-12-10
Hi,

I made a bootable USB stick with persistent Ubuntu Netbook Remix as explained on the Pendrive Linux site and it booted fine. Then I decided to update the packages and then the updating  process encountered a problem while updating a Grub package: I was asked if I wanted to install it to sda, sdb, sdc or sdd. Since I booted from the Live USB stick (/dev/sdd), sdd seemed a logical choice, because I didn't want my Grub from another Linux distro on sda to be overwritten. Then theupdater reported that Grub hadn't been found on sdd.
After all finished I had to reboot after updating and during bootup from USB I got error reports saying (if I remember well) that no image file was found, so rebooting wasn't possible any more.

Did I make a mistake by indicating sdd as a target for the grub update? I can't imagine.

What went wrong and what should I do next time while udating Grub packages ?

Tux@Linux

---

