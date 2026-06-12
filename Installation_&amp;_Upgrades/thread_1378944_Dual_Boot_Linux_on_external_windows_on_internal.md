---
title: "Dual Boot Linux on external windows on internal"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by nuggety on 2010-01-12
Hi All,
 
I am trying to install ubuntu on an external hard drive, with windows installed on my internal hard drive.
 
I want to be able to add windows to the GRUB menu so i can choose linux/windows without having to plug in/plug out my external HDD.
 
Thanks,
 
Scott

---

### Post by raymondh on 2010-01-12
[QUOTE=nuggety;8650897 
I want to be able to add windows to the GRUB menu so i can choose linux/windows without having to plug in/plug out my external HDD.
 [/QUOTE]

Scott,

I am assuming that

-  windows is in an internal that is set to boot first in BIOS ... and there is no other internal HD
-  The external will/is permanently plugged into the system

You'll need a bootloader in the MBR of the internal that will dual-boot as well as 'chainload' Ubuntu.  Some folks here like using easyBCD.  I prefer to use GRUB.

If it were me, and both assumptions above are correct, I would install GRUB (using a liveCD) in the MBR of the internal HD and then.  If it does not pick up on Ubuntu, I would then chainload Ubuntu.  [See DRS305's guide to GRUB2]("http://ubuntuforums.org/showpost.php?p=7505203&postcount=1").  If you are using Grub-Legacy, see this [post by catlett]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1").  To chainload ... see this [HERMAN guide]("http://members.iinet.net.au/~herman546/p15.html").

If the external is not permanently attached to the system, I would just keep the windows bootloader in the MBR of the internal and GRUB in the external .... my control to boot will now be thru BIOS quick-change (where you choose which HD boots first upon start-up)

Hope this helps,

Raymond

---

### Post by oldfred on 2010-01-12
I would go with the recommendation of grub on the external and windows boot in the MBR of the internal. You can set in BIOS to boot first from the external and if it is not there it will boot the internal.

Grub may want to install to the internal if it is the boot drive when you install. You can use the advance button on the screen where it wants to finalize the setup of the partitions to insure which drive it installs grub into the MBR.

If you have grub in the MBR of the internal and the grub files in the external, you will not be able to boot windows, if the external is not plugged in, as grub needs the additional files from the external.

---

### Post by darkod on 2010-01-12
> **oldfred said:**
> 
If you have grub in the MBR of the internal and the grub files in the external, you will not be able to boot windows, if the external is not plugged in, as grub needs the additional files from the external.

+1

If you let grub2 go to the MBR of the internal, with its config files on the ubuntu partition on the external, you won't be able to boot anything with the external unplugged.

---

