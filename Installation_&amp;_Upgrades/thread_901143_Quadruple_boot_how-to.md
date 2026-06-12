---
title: "Quadruple boot how-to"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by rootnoverify on 2008-08-26
Hello to all community members..I would like to know how can I add Ubuntu to my system with an existing triple boot scheme (winXP, Vista, and RHEL5). winXP and Vista are on two separate partitions on a 250-gig sata disk while RHEL5 is on a separate 80-gig disk. I would like to install ubuntu on the 80-gig disk where my RHEL5 installation is. can i also install ubuntu without the bootloader and just add it via RHEL5's grub.conf? I was thinking installing ubuntu with the bootloader might jeopardize my existing  triple boot scheme (Vista can burn, but i can't afford losing xp and rhEL5). Thanks in advance and more power!

---

### Post by prshah on 2008-08-26
> **rootnoverify said:**
> how can I add Ubuntu to my system with an existing triple boot scheme (winXP, Vista, and RHEL5).  can i also install ubuntu without the bootloader and just add it via RHEL5's grub.conf? I was thinking installing ubuntu with the bootloader might jeopardize my existing  triple boot scheme 

Yes, you can add ubuntu without the need for the bootloader; nearing the end of the installation, click on "Advanced" (it appears just before the finish, I think) and choose not to install a bootloader.

Then you can add the parameters manually to your redhat installed GRUB; but you may need to do a update-grub from redhat before the options take effect (not sure about this).

If you are worried that your boot integrity might get violated, you can back up the MBR _before_ you attempt the ubuntu installation; you can do this from your existing redhat installation; ```
sudo dd if=/dev/hda of=/root/mbrbackup bs=446 count=1
``` Repeat the above command for each disk, and replace /dev/hda with your actual disk device id. Be very careful with the dd command, a single mistype will cost you a lot.

---

### Post by rootnoverify on 2008-08-26
Thanks a lot prshah. I'll try doing that as soon as I get home. Have a good day..

---

