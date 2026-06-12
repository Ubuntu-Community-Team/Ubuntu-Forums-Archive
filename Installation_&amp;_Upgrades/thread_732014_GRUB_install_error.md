---
title: "GRUB install error"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by boebi on 2008-03-22
When installing Ubuntu, GRUB gives me an error.
I first start with installing dmraid into ubuntu, succesfully, no problems.

Then I select my partitions to install to, no problem.
At about 95% of the installation progress, it says something very similar to this:
> 
GRUB cannot be installed (hd0), this is a fatal error.


And it quits installing.


When I re-boot my pc, the WINDOWS BOOTLOADER gives me 2 options, Vista or Ubuntu.
Vista works.
Ubuntu (after a LONG loading time) just gives me a sort of Terminal. It said something about debiant there..
When I select Ubuntu, and then insert the live cd, it boots Ubuntu with desktop (and option to install again)


Humz, help?

---

### Post by m_cubed on 2008-03-22
how many / what size are the hard drives in your computer?

---

### Post by Pumalite on 2008-03-22
You should boot an Ubuntu Live CD and post the following, so people can help you better:
sudo fdisk -lu

---

