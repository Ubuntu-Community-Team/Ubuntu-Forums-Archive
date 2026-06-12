---
title: "Can I install to a specific partition without installing boot loader?"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2013-05-02
I want to install the latest Xubuntu to a specific HD partition and then run update-grub in my existing 12.10 system to add Raring to the boot menu. The installer does not appear to offer this as an option. 

While struggling with flakiness in the 64-bit install on two different USB devices, I discovered to my horror that the installer mounts every partition it can find. No! No! No! I know where I want to install and I don't want anything else touched at all. 

One way to achieve what I want is to install on a VM. The installer sees only the virtual HD drive and cannot damage anything else. I did this with Xubuntu 13.04 32-bit and I'm happy with the result. But VMs have their own limitations and it would be nice to install the 64-bit directly on the hardware. 

Any ideas?

---

### Post by darkod on 2013-05-02
The installer doesn't mount any partitions, I have no idea what you are talking about. If you do use live mode, open few partitions to see what's on them, and then start the installer with the Install icon without rebooting, yes, it will continue with those partitions you opened mounted. Otherwise, it doesn't mount anything.

Unfortunately, few releases ago they removed the option not to install a bootloader. There was a way to do it I think, with a specific boot parameter that you would need to boot with, but I don't remember the procedure any more.

What you can do is install grub2 to the partition where you are installing the new OS, and leave it there, it doesn't matter.
Or simply put it onto the MBR and then restore grub2 from the other installation that you want to use as main.

---

### Post by jcoles on 2013-05-02
The installer *does* mount partitions. Excerpt from dmesg:
> [   11.858206] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.885151] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[   11.885157] EXT4-fs (sda6): write access will be enabled during recovery
[   11.926136] EXT4-fs (sda6): recovery complete
[   11.926734] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   11.948923] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   12.086811] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

My installation failed with "Error mounting /tmp". Input/output error. I selected M (Manual Recovery) and dropped to a shell. That's how I was able to look at the log. 

The real problem turned out to be disk space for persistent files on the USB device. I used a 1GB device. I forget how much "Space used to preserve files across reboots" I allocated with UNetbootin, but it wasn't enough. Re-making the USB install drive with maximized the persistent file space solved the problem. 

I didn't follow your advice about the bootloader, but the installer quite intelligently included all of the existing entries in the new Grub boot list. It made 13.04 the default, of course. Even re-running update grub under 12.10 didn't change that. Not a big problem.

---

### Post by darkod on 2013-05-03
I guess we ae looking at mounting in a different way. The installer is scanning the disk to check all partitions, but not mounting them. Otherwise, how would you repartition during installation with the partitions mounted?

And live mode (Try ubuntu) is not the installer, live mode is live mode. In live mode for example, any swap partition found is mounted to speed up working. The installer is the Install Ubuntu option, which should leave all partitions unmounted so you can make changes to the disk during installation.

As for grub2, I never said it will not find all OSs on the disk. From your first port I understood you strictily want to use grub2 from 12.10 as default. Otherwise, the 12.04 installation will install its grub2 to the MBR which makes it the main OS, and will report any other OSs below in the grub boot menu.

If you do want to make 12.10 grub2 main, boot it once and run:
```
sudo grub-install /dev/sda
```

If your grub is on sdb use /dev/sdb instead. After that when you reboot the grub2 from 12.10 will be main, and 13.04 should be below it in the list. In case it's not you might need to do sudo update-grub from 12.10 but if i understood right you already did that earlier.

---

