---
title: "Messsed Up Edgy Eft by installing a dual boot with Feisty"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Nelson-Ray on 2007-01-16
Hello I have my computer set up like this :

/dev/hda1 Windows XP
/dev/hda2 /boot
/dev/hda3 /swap
/dev/hda5 / (Feisty)
/dev/hda6 / (Edgy Eft)

The other day I got tempted with Feisty and installed it on /dev/hda5 and used /dev/hda2 as /boot partition. I chose to format the /boot partition during the installation and this is where the trouble began (the /boot partition was used prior as the /boot partition for Edgy). The installation of Feisty 's Grub picked up the Windows XP installation on /dev/hda1, but did not pick up Edgy Eft on /dev/hda6. Grub now has no setting for Edgy Eft at all. Furthermore since the /boot partition was formatted, I believe the vmlinuz and initrd files for Edgy was deleted as well. 

Although Feisty works fine so far, I would like the option to boot back into Edgy. Could someone provide help in restoring Edgy in Grub, as well as reinstalling the vmlinuz & initrd files necessary to boot Edgy? 

Thanks...

---

### Post by dcstar on 2007-01-16
> **Nelson-Ray said:**
> Hello I have my computer set up like this :

/dev/hda1 Windows XP
/dev/hda2 /boot
/dev/hda3 /swap
/dev/hda5 / (Feisty)
/dev/hda6 / (Edgy Eft)

The other day I got tempted with Feisty and installed it on /dev/hda5 and used /dev/hda2 as /boot partition. I chose to format the /boot partition during the installation and this is where the trouble began (the /boot partition was used prior as the /boot partition for Edgy). The installation of Feisty 's Grub picked up the Windows XP installation on /dev/hda1, but did not pick up Edgy Eft on /dev/hda6. Grub now has no setting for Edgy Eft at all. Furthermore since the /boot partition was formatted, I believe the vmlinuz and initrd files for Edgy was deleted as well. 

Although Feisty works fine so far, I would like the option to boot back into Edgy. Could someone provide help in restoring Edgy in Grub, as well as reinstalling the vmlinuz & initrd files necessary to boot Edgy? 

Thanks...

You should be able to manually edit your grub.lst file and add in the info to boot off hda6, as far as the files go, I may be able to post them later. - Sorry, they are far too big to upload to the forum......       :(

---

