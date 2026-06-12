---
title: "Question after installation of Ubuntu on external HDD"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by marco1725 on 2016-02-15
Hello 
  I installed Ubuntu on external HDD while in my pc I've Windows. Can I disable the detect of Windows volume in Ubuntu?   
Thank you

---

### Post by Dennis N on 2016-02-15
> **marco1725 said:**
> Hello 
  I installed Ubuntu on external HDD while in my pc I've Windows. Can I disable the detect of Windows volume in Ubuntu?   
Thank you

You can prevent all other OS from showing on the grub menu by disabling the os prober and then updating grub to rebuild the menu. Two commands will do it, done one after the other:

```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

```

---

### Post by oldfred on 2016-02-16
Dennis N's instructions will eliminate the Windows boot option.

But if you want to hide the mount of the NTFS partition(s), you actually have to add mount entries into fstab that say to not mount it.

Some examples:
 # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

If Windows 8 or later with fast start on, or hibernation, the NTFS driver will normally give an error message if you try to mount it.

---

