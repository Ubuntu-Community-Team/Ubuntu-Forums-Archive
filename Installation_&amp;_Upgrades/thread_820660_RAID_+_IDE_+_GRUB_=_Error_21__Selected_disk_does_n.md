---
title: "RAID + IDE + GRUB = Error 21 : Selected disk does not exist"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by groo028 on 2008-06-06
My computer is configured as follows:
2x160GB SATA drives in a RAID array
1x120GB IDE drive 

I had Feisty installed on the IDE drive with GRUB on the same drive. Whenever I wanted to boot into Ubuntu I would select "Boot from IDE drive" and everything was working flawlessly. 

I decided to install Hardy and overwrote my old Feisty installation and installed GRUB on the IDE drive again. I started getting "Error 21: Selected disk does not exist" when I tried to boot. So I followed some instructions to reinstall GRUB but I managed to overwrite my RAID MBR as well. I am now stuck with Error 21 when I try to boot from my RAID and my IDE drives.

Any suggestions?

---

