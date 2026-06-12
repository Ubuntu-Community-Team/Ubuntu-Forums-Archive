---
title: "installing xp after ubuntu"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by geoff4376 on 2010-02-03
Let me just start off by saying that I am kind of new to this, so please bear with me if you would.  That said, I need to install windows xp on a pc that already has ubuntu 9.10 on it.  XP will be installed to a separate HDD all together just to avoid all of the partitioning mess.  I want to set it up to dual boot. Can I just boot from the Win XP install cd and just have everything work out all peachy?  The pc is a Dell Optiplex GX260 if it makes a difference.  Thanks in advance!

---

### Post by yogesh.girikumar on 2010-02-03
Hi,


Installing any windows OS after installing a Linux affects the MBR on the hard disk.

So, it's always better to install Windows first and Linux OS later.
       

If you installed Windows after installing linux and if your GRUB is messed up, 
You can try the following steps to restore GRUB. ( After having installed Windows ):
       

1. Boot into the live CD of ubuntu
2. Open terminal : Applications -> Accessories -> Terminal
3. Type the code as follows:

```
$ sudo bash
# mkdir /mnt
# mount /dev/sda1 /mnt
# chroot /mnt
# mknod /dev/sda b 8 0
# mknod /dev/sda1 b 8 1
# cd /boot/grub
# grub-install /dev/sda
# exit
# reboot
     
```Please also refer to the following links where similar discussions seem to have taken place:

      [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=1372893](http://ubuntuforums.org/showthread.php?t=1372893)
       

Let me know if that works.

---

### Post by oldfred on 2010-02-03
If you have two hard drives it is slightly better as you do not have to overwrite MBRs.
One MBR can have windows and the other grub. But you have to make sure you have the correct drive set as boot or first to boot in BIOS.

I would set the new drive as first in BIOS and windows should just install to that (and not even see the Ubuntu drive). Then switch the Ubuntu drive to boot in BIOS. If you have grub2, all you have to do is 
sudo update-grub

If drive was not in system when ubuntu was installed grub may only have one drive in device.map and not see the windows drive.
If it complains about a device map 
sudo grub-mkdevicemap
sudo update-grub

If you did overwrite grub.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

