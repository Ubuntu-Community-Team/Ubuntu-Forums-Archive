---
title: "Add RAID driver during install -"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by CRCarl on 2010-09-01
All - 
   I need to add the LSI drivers for the 9750 RAID controller during the install. These drivers are not included in 10.04 (or 10.04.1) and I need to install onto the RAID device I've created. LSI provides the drivers and instructions here - 

[http://kb.lsi.com/KnowledgebaseArticle15881.aspx]("http://kb.lsi.com/KnowledgebaseArticle15881.aspx")

Here are my steps, with the drivers on a USB drive - 

```

Boot from the installation CD and select Install Ubuntu Server. 
Press CTRL+ALT+F2 to switch to console 2 while Ubuntu detects the network.

   # mkdir /mnt2 /3ware
   # mount /dev/sda1 /mnt2
      NOTE: LSI drivers are at /dev/sda1, via USB
   # cp /mnt2/9750-server.tgz /3ware
   # cd /3ware ; tar zxvf 9750-server.tgz
   # umount /mnt2
            
*** Remove the USB flash before insmod command **

   # insmod /3ware/2.6.32-21-generic/3w-sas.ko

Press CTRL+ALT+F1 to return to the installer. Continue the installation as usual.  Do not reboot when the installation is complete. Press CTRL+ALT+F2 to switch to console 2 again.
  
   #  cp /3ware/2.6.32-21-server/3w-sas.ko  /target/lib/modules/2.6.32-21-server/kernel/drivers/scsi
   #  chroot /target
   #  /sbin/depmod  -a  2.6.32-21-server
   #  update-initramfs -u -v 
   #  exit

Press CTRL+ALT+F1 to return to the installer. Reboot to complete the installation.

```

There are no errors, but after I reboot I just get "GRUB" in the upper left corner, nothing else.

Ideas? Thanks.

---

### Post by tregora on 2010-10-11
I haven't been able to get it to work either.  

From LSI's website h[ttp://kb.lsi.com/KnowledgebaseArticle14546.aspx]("ttp://kb.lsi.com/KnowledgebaseArticle14546.aspx")
"Linux kernels 2.6.33 and newer include native support for the 3ware 7000/8000/9500S/9550SX(U)/9590SE/9650SE/9690SA/9750 series controllers."  

I was able to download a ubuntu 9.10 x64 ISO from 3ware and install using it.  

[http://www.lsi.com/lookup/License.aspx?url=/DistributionSystem/User/AssetMgr.aspx?asset=54054&prodName=3ware%20SAS%209750-8i&subType=Driver&locale=EN]("http://www.lsi.com/lookup/License.aspx?url=/DistributionSystem/User/AssetMgr.aspx?asset=54054&prodName=3ware%20SAS%209750-8i&subType=Driver&locale=EN")

On a side note I was actually trying to get either FreeNAS or Openfiler installed on the card and neither worked so I tried Ubuntu.  At least this gets me working although managing each service individually is a pain (NFS, ISCIS, ect.).  Hope that helps.

---

### Post by jpeirce on 2010-11-09
tregora: To fix your GRUB error, just re-install grub either before rebooting into the OS after installation, or while booted into a rescueCD.

Say your installation was on /dev/sdg, / was on sdg2 and /boot was on sdg1, you'll want the following mounts:

mount /dev/sdg2 /target
mount /dev/sdg1 /target/boot
mount -t proc none /target/proc
mount --bind /dev /target/dev
mount -t sysfs none /target/sys

Then chroot into target:

chroot /target /bin/bash

Then reinstall grub
grub-install /dev/sdg

Obviously, replace sdg with the correct drive for your install.

Hope this helps!

---

