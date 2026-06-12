---
title: "GRUB: Lost ability to boot old Kubuntu version"
date: 2023-04-20
forum: Installation &amp; Upgrades
---

### Post by osgmqjno on 2023-04-20
I haven't had a boot issue in over a decade and a lot has changed. I hope someone can help.

I had Kubuntu 18.04 on an HDD. I installed 22.04 on a new SSD but left the HDD in so I could boot it if necessary. It shows up on the grub menu at boot.

I didn't test the old boot right away, and there could have been some cockpit error on my part, but when I recently tried to boot the old HDD it gave me the Kubuntu splash screen then dumped me into emergency mode: "Press enter for maintenance, press CTRL-D to continue".
I'm able to enter grub and look around in the old file system. I listed the partitions and found my new Kubuntu on (hd0). (hd1) however is reported to have no recognizable file system. But when booted into the new install I am able to mount and navigate the old drive, so nothing has been lost.

I'm thinking the safest route would be to break open the box, disconnect the SSD, and try to use the Kubuntu 18.04 live disk (I throw nothing away) to reinstall the boot files. I just want to make sure I don't wipe the rest of the old HDD. I wouldn't lose any data because I backed it all up before the upgrade. I just want to take the simplest route to regaining bootability of the old disk.
What's the best way to do that?

---

### Post by MAFoElffen on 2023-04-20
I would agree that it the safest route to approach that...

Disconnect the drive.

Boot off an Ubuntu 18.04 LiveCD.

Mount the installed filesystem.

Reinstall and configure Grub.

---

### Post by yancek on 2023-04-20
Reinstalling Grub to 18.04 on the HD will require you to access the BIOS to select that drive to boot and do the same to boot 22.04 on the SSD.  Have you tried entering the BIOS and selecting the HD as first boot rather than trying to boot from the 22.04 Grub menu?  If that works, no need to reinstall Grub on 18.04 since it had previously booted..

---

### Post by oldfred on 2023-04-20
If UEFI install, you may have both systems booting from one ESP. 

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Ubuntu only wants one ESP on first drive for UEFI booting.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Remove esp flag from first drive's ESP before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) &

---

