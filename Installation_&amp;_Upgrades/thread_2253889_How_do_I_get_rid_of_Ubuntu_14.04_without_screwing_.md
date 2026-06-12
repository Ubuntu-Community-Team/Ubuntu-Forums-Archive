---
title: "How do I get rid of Ubuntu 14.04 without screwing up my Windows 7 intstall"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by Joseph_Hiatt on 2014-11-23
I foolishly installed 14.04 dual boot on my Windows system because I wanted to run a few VMs under KVM.

After the install no applications appear in Unity.  I ran the verify and almost every .desktop file was corrupt.

I don't want Ubuntu 14.04 and I don't want to wipe my system and start over.

Miserable.

---

### Post by Mark Phelps on 2014-11-23
When you remove Ubuntu, it will still leave GRUB in the MBR and that will prevent you from booting anymore.  So, before you do that, boot into Win7 and run Startup Repair three times -- that's right, three times.  If it works, when you reboot for the last time, you should be booting directly into Win7.

After that, just use the Win7 Disk Management tool to remove the Ubuntu partitions.

You can then use the same tool to create a new NTFS partition in the place of the removed Ubuntu partitions.

---

### Post by carl4926 on 2014-11-23
> [COLOR=#000000]boot into Win7 and run Startup Repair three times [/COLOR]It's crazy isn't it

Of course if you have a Windows DVD it's quick and easy

---

### Post by Joseph_Hiatt on 2014-11-23
Thank you.

---

### Post by ubfan1 on 2014-11-23
And if repairing the Windows MBR fails, you can always move the grub files to one of the FAT Windows tools or system partitions -- just make a directory /boot and install grub there.

---

