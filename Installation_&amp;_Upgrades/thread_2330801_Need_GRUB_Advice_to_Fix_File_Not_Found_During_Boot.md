---
title: "Need GRUB Advice to Fix File Not Found During Boot"
date: 2016-07-15
forum: Installation &amp; Upgrades
---

### Post by jamoody on 2016-07-15
I upgraded from 12.04 to 14.04 and now receive 3 File Not Found messages during boot as described in [http://askubuntu.com/questions/460908/error-while-booting-ubuntu-14-04](http://askubuntu.com/questions/460908/error-while-booting-ubuntu-14-04).  I want to try the solution posted there but realize I need to tread carefully with GRUB updates.  The steps identified in the other thread are:
  sudo grub-install /dev/sda
  sudo update_grub
  sudo reboot
My question is: I've got /boot on /dev/sda1, does that mean I want to specify "grub-install /dev/sda1" instead of /dev/sda? 

$ df /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   27G   21G  56% /

My motherboard is ASRock P45X3 so it looks like it's BIOS and not EUFI.

---

### Post by jamoody on 2016-07-15
FYI, comparing /boot/grub/grub.cfg from my 12.04 system with my 14.04 system it looks like the following 3 lines were added to grub.cfg in 14.04 but the corresponding modules were not:
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
I assume these are the 3 files not found.

---

### Post by Dennis N on 2016-07-15
> My question is: I've got /boot on /dev/sda1, does that mean I want to specify "grub-install /dev/sda1" instead of /dev/sda? 
No, in BIOS mode installations, you want to install grub to /dev/sda even if you use a separate boot partition. Otherwise, it would not boot at all.

---

### Post by jamoody on 2016-07-15
Glad I asked :-)  I'll cross my fingers and give it a try.  Thanks.

---

### Post by jamoody on 2016-07-19
Worked like a charm.  File Not Found messages at boot are gone.  Thanks.

---

