---
title: "grub misconfigured when usb drive plugged in"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by berthiggins on 2009-09-09
I use my laptop both on my lap or on my desk
 when on my desk I have several usb drives plugged in.
If a grub update runs with the usb drives plugged in then grub assigns the wrong disk as the root drive for the kernel.
I think this is because the drive assignations are changing with the extra disks.
should the system be using UUIDs?
Is this a bug and if so has anyone else seen it? It seems that this would not be acceptable behaviour to a casual user?

---

### Post by lindsay7 on 2009-09-09
What do you mean by a "grub update"?  Can you post the output of fdisk -l from the terminal with all the usbs plugged in.  You may have a mbr set up on one of the usb drives.

---

### Post by berthiggins on 2009-09-10
By grub update I mean  the program that runs after an update or if you make changes to grub to update /boot/grub.cfg

Also I can boot with a corrected grub.cfg ( done by hand not the grub-update programe ) I can boot the laptop only without the USB plugged in with it plugged in aparently /dev/sdb1 no longer exists.
This is a complete change in behavior to previous versions even earlier versions of Karmic.
Here is the O/P from sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2a4d2a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS

Disk /dev/sdb: 16.1 GB, 16135487488 bytes
255 heads, 63 sectors/track, 1961 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00037ece

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1873    15044841   83  Linux
/dev/sdb2            1874        1961      706860    5  Extended
/dev/sdb5            1874        1961      706828+  82  Linux swap / Solaris

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd65b3b13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9612    77208358+   7  HPFS/NTFS
/dev/sdd2           13132       48641   285234075    7  HPFS/NTFS

There is a start able disk on the USB bus but IMHO this should not get configured as kernel root by grub-update or stop the machine booting.

---

### Post by berthiggins on 2009-09-11
bump!

---

### Post by VMC on 2009-09-11
You can check grub.cfg before and after you plug in one of your usb drives, and see where its storing the menu for usb's. Then maybe check one of the files in /etc/grub.d. Have you altered the 40_custom file?

---

### Post by berthiggins on 2009-09-11
hi thanks for the ideas!
I have not modded the 40 file grub.cfg only gets wrongly set up if I have the usb drives mounted when grub-update runs ( ie during an update)
This was not a problem before Karmic I am just trying to find out if this is a known bug or intended behaviour.
The other problem being that the system cannot find the boot drive with the usb connected it seems that although fstab uses uuid grub2 is fooled by the addition of /dev nodes.
I really just want to know if this is happening to anyone else or if I have a file or setting corrupted during an upgrade?

---

### Post by VMC on 2009-09-11
The only thing I was suggesting was maybe to delete grub.cfg, unplug usb then issue update-grub. Save that grub.cfg then delete and plug-in usb drives and then update-grub and compare grub.cfg's 

Also, as someone else mentioned, maybe one of your usb drives has its own mbr. Is your pc set to boot off usb? I have mine set to ask questions first.

---

### Post by berthiggins on 2009-09-12
Thanks for the reply
The laptop is set to give a boot menu and Karmic is booted from an SD card there is windows xp on the main HDD this has always been there.
when the usb drives are connected It starts to boot into Karmic but times out waiting for the boot device the message is that sdb1 ( the flash disk does not exist)
If the usb is unplugged boot is normal.
If the usb devices are plugged in when grub-update runs then boot device becomes /dev/sdc which seems to imply that the extra disks have added a /dev node. while it is logical for nodes to be added is it not more logical to use UUIDs as dev nodes shifting will give problems like it used to with fstab?



This happens when the

---

### Post by VMC on 2009-09-12
What does both ```
sudo blkid
``` and ```
sudo fdisk -l
``` show when all drives are plugged in?

---

### Post by Kokopelli on 2009-09-12
OK this is a  bit of a rant but grub2 does not handle changing number or position of drives well.  Unless devices.map matches the number of drives correctly, grub2 configures itself using device path even though I specifically have /etc/defaults/grub set to use UUID.  Grub2 should be using UUID unless I specifically tell it not to.  Instead if devices.map is not exact if falls back on device paths which will almost definitely break grub.cfg for me since HD device path is dependent on what I am doing.  I should not have to configure devices.map by hand everytime grub.cfg may be reconfigured.  This will particularly be a problem post release where I set updates to run using cron.

Right now, sometimes I do not notice a grub update necessitating me mounting my laptop hard drive on my desktop to correct grub.cfg by hand.   One day I will get an update that triggers grub-config when I am not at my house and that will make my computer unbootable till I get home or use a bootable image.

EDIT: Thought I might explain in more detail.

Most of the time the Karmic install resides on the secondary hard drive of one of my two thinkpads.  In both cases that would make the Karmic install sdb.

so my device.map is usually set as follows:

(hd0)   /dev/sda
(hd1)   /dev/sdb

if grub-update runs in this configuration grub.cfg uses UUID.

Sometimes I boot the same disk from my HP laptop using esata.  In this case the two internal drives are sda and sdb and the karmic install is sdc.  if I do an update when configured this way without changing device.map it will rewrite grub.cfg using /dev/sdc as the root, making it unbootable on the thinkpads.

Sometimes (rarely) I boot the drive on my desktop using esata making the karmic install sdg.  Same breakage as the HP.

Finally if I am on the road I will not have the docking station so will put the karmic install into one of the thinkpads as sda.  When I do this I reconfigure device.map so as not break grub.cfg on update but if I were to forget an update would make this unbootable as well.

In all of these scenarios Karmic performs flawlessly across hardware changes except grub-update.

EDIT2:  To be fair in all of the above scenarios I am pretty sure Karmic will still be bootable in the exact configuration at the time of grub-update, but I change configuration quite a lot.  Additionally with the added variances of USB-keys or external hard drives being attached/detached it is annoying.

---

### Post by berthiggins on 2009-09-12
Thanks for the comment I was starting to think it was just me!

---

### Post by maestrobwh1 on 2009-09-12
Me too.  Just know that you should maybe do something like

sudo cp /boot/grub/menu.cfg /boot/grub/menu.cfg.bak

Also take note of what your external drive would be as /dev/sdXY w/o other devices plugged in at boot.  This way, if it is misconfigured, you can hit "e" for the boot entry at start and temporarily fix it.  I had to do this and change /dev/sdc1 to /dev/sdb1 or I could not get a full boot.

Last, maybe take note if you upgraded if grub.cfg is changed before you shut down/reboot.  

I am annoyed that karmic went by way of this, because it obviously has some kinks in it.

---

### Post by Kokopelli on 2009-09-13
I do not know for certain if this will help but I added "/usr/sbin/grub-mkdevicemap" to my /etc/rc.local.  That way the device.map is rebuilt on each boot.  Not the most elegant of solutions but as long as the HD list does not change between boot and configuration of grub this should stop the problem.  

If people are having problems other than a disparate device.map or I misdiagnosed the problem this will not solve it though.  Time will tell for me.

---

