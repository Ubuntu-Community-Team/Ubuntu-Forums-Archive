---
title: "Failure after trying to upgrade from Legacy grub to grub2"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by sefs on 2011-05-21
Hi all,

I moved from 8.04.2 to 10.04.2 and tried to upgrade from GRUB Legacy to Grub2.  I must have made a mis-step somewhere in the process as on boot it now tells me

```

GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 15
_

```

Is there a nuke from orbit, no finesse way of just ripping all the existing GRUB mess out and installing GRUB2 from Boot disk?

for instance should I be just be able to boot with a LIVE CD mount the primary disk of this machine and enter the below in a terminal without messing up any further?

```

sudo grub-install --root-directory=/media/PRIMARY_DISK /dev/sda

```

Thanks in Advance.

---

### Post by Quackers on 2011-05-21
If some vestiges of grub legacy are left over they seem to interfere with grub2 operation. It may be best to purge both grub and grub2 then re-install grub2 as per drs305's guide below.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-05-21
Grub 1.5 sounds like grub legacy in the MBR. And error 15 is often confusion between grub2 & grub legacy.

If you can install the simple two line version.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)


But often with mixed grubs you have to chroot into your system, uninstall both grubs and reinstall just grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by sefs on 2011-05-21
None of the above seemed to have worked. What I had to end up doing is what I suggested in the first post :S

---

