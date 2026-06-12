---
title: "Help - Uninstall Win XP from Dual Boot with Edgy"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Wardo on 2007-03-06
I've been dual booting Ubuntu (Edgy) on a PC that has a Windows XP partition. I decided it is time to move all the way to Ubuntu and want to uninstall Windows from its partition and format the partition to ext3 so I can use it with Ubuntu.

I think the easiest way to do this would be through GParted. However, I am not sure about that, since in GParted the Windows (NTFS) partition is flagged as **boot**. Would I only need to flag my main Ubuntu partition with **boot** and unflag the NTFS?

Is it possible, after uninstalling Windows, to resize my main Ubuntu partition to occupy the previous space of the Windows one?

Can anyone help?

---

### Post by Kateikyoushi on 2007-03-06
It's not necessary to do anything with the boot flag, just delete the ntfs and make a new partition, If you want you could resize the partition to take up the space but I would rather recommend to make a /home partition.

You can do all this with gparted.

Except for removing windows from grub. For that 
```
sudo nano /boot/grub/menu.lst
```

---

### Post by Wardo on 2007-03-06
> **Kateikyoushi said:**
> It's not necessary to do anything with the boot flag, just delete the ntfs and make a new partition, If you want you could resize the partition to take up the space but I would rather recommend to make a /home partition.

You can do all this with gparted.

Except for removing windows from grub. For that 
```
sudo nano /boot/grub/menu.lst
```

Kateikyoushi,

Thanks for the help! But I still have a few doubts:

1) Deleted NTFS partition and created a new one EXT3. However it is mounted as the late NTFS partition on /media/windows. Is it possible to change this mount point to /home?

2) About removing windows from grub, I'm not so sure about what I need to delete in the menu.lst. 

Here is a screen shot of the part I think I need to delete, can you confirm this is it?

---

### Post by mikewhatever on 2007-03-06
When creating the new partition, was there an option to mount it?

In the GRUB menu.lst delete everything below the following line:
### END DEBIAN AUTOMATIC KERNEL LIST

---

### Post by Kateikyoushi on 2007-03-06
You can change the mount point for the partition.
Make a new directory for it.
> sudo mkdir /media/DIRECTORYNAME

Then edit your /etc/fstab to point to the right directory.
You can remount the partitions with the following command.
```
sudo mount -a
```

To move /home to this partition read this guide. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

Yes you have to edit there the windows entries if you are unsure just comment the lines by putting a hashmark # at the beginning, those lines will be ignored.

---

### Post by Wardo on 2007-03-06
> **mikewhatever said:**
> When creating the new partition, was there an option to mount it?

In the GRUB menu.lst delete everything below the following line:
### END DEBIAN AUTOMATIC KERNEL LIST

When creating new partition with GParted there was no option to where the mount place was going to be.

---

### Post by Wardo on 2007-03-06
> **Kateikyoushi said:**
> You can change the mount point for the partition.
Make a new directory for it.


Then edit your /etc/fstab to point to the right directory.
You can remount the partitions with the following command.
```
sudo mount -a
```

To move /home to this partition read this guide. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

Yes you have to edit there the windows entries if you are unsure just comment the lines by putting a hashmark # at the beginning, those lines will be ignored.

Ok, everything is done and working fine now. Pointed in fstab to right directory, and hashed out the entries in the grub menu, now it boots up with no mention of other OSs, and the partition if fully usable in my /home as a new folder.

Thanks for the help.

---

