---
title: "ubuntu 12.04 (LTS): Cannot modify bootmenu"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by mabra on 2012-10-28
Hi !

I came accross debian and I am now on ubunto because of the LTS [2017]. I installed a plain server and added
LXDE, probably one, two tools.

Then I followed the instructions to modify the grub(2) boot-menu:

[http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM](http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM)

I created a custom entry, I 'grub-mkconfig' -ed the configuration
and updated via 'update-grub' and viola, the '/boot/grub/grub.cfg'
is changed as expected.

Reboot. It does not work, no new/extra menue-item. I checked '/boot/grub/grub.cfg' and the entry is there.

Any ideas, what could have been gone wrong ??

Thanks anyway!

br,
++mabra

BTW: Just to re-check. I've done this on another machine
using debian (testing) and it works as expected.

---

