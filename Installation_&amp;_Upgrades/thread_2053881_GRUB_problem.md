---
title: "GRUB problem"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by DJ_Cyberdance on 2012-09-06
Many things have already been written about Grub and problems it causes - but I haven't found a suitable solution yet, I hope someone is able to help.

I have an Ubuntu 10.04 installation I moved from one harddrive to another. To do so, I copied the contents to the new partitions using cp -af src/* dest/

I modified the /etc/fstab file on the new drive by replacing the uuids of the old drive/partitions with the new ones.

I removed the old hard drives and booted the system from a grml live CD. I launched grub (from the new harddrive) and executed find /boot/grub/menu.lst, root (hd0,0) and setup (hd0,0). Then I restarted without CD.

I did NOT modify the menu.lst file because after removing the old hard drive (hd0) the new one became (hd0). However, the old one was an ATA drive, the new one is a SATA drive.

Of course, I changed the boot sequence in the BIOS.

The system hangs at the following stage:

[B]Grub stage 1.5
Grub loading, please wait...[/B]

I have changed the boot sequence a couple of times as I have read that might cause this issue but that did not really change the situation. Any suggestions what else I could try?

---

### Post by darkod on 2012-09-06
> **DJ_Cyberdance said:**
> 
I removed the old hard drives and booted the system from a grml live CD. I launched grub (from the new harddrive) and executed find /boot/grub/menu.lst, root (hd0,0) and setup (hd0,0). Then I restarted without CD.


The procedure you described is for the older grub1. Ubuntu since version 9.10 comes with grub2 which doesn't use menu.lst and doesn't install with setup(hd0,0).

Were you using the older grub1 if you were only upgrading your system from before 9.04 and never told grub to upgrade to grub2 also? Or you actually have grub2 and this is why you can't boot now?

Look into /boot/grub/ whether there is grub.cfg and core.img files or not?

---

### Post by DJ_Cyberdance on 2012-09-06
I need to check, I'm not at this machine at the moment. However, as far as I can remember I have always been using menu.lst for configuring grub. I definitely never upgraded intentionally, I only installed system upgrades regularly by apt-get upgrade.

I once did an upgrade from 08.04 to 10.04. I doubt grub2 was installed then either. However, I guess I'll boot from GRML again, chroot to the new device and then apt-get install grub2. I've just checked out [https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading).

I'll give that a try, thanks so far for the quick response! Any further hints?

---

### Post by darkod on 2012-09-06
Actually, if you are familiar using chroot, I would purge all grub1/grub2 config and install grub2 again (the actual package name is grub-pc).

So, once you are in with chroot, it would be like:
```
apt-get remove --purge grub grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

The last command is what is used to install grub2 to the MBR of a disk, in this case i assumed sda. If you want to install to sdb, etc, just change that accordingly.

Those commands would purge all grub1/grub2 related config including in grub-common. Then it will install grub-pc (grub2), create the config file, update it if there are other OSs to detect, and finally install it on the MBR of the disk.
After that just boot from that disk and all should be fine. This is a very clean approach since at the beginning gets rid of any possible mixed configurations between grub1 and grub2, it just removes everything.

---

### Post by DJ_Cyberdance on 2012-09-07
Awesome, thank you so much! Worked like a charm! After everything was done, I upgraded the system to 12.04.1. However, I can't get Grub to booting a default menu entry (the first one). I checked out /etc/default/grub where the delay has been set to 10 secs. But it still won't boot automatically.

Apart from that, in 1 out of 2 boots the system hangs right after manually choosing the first menu entry. After a reboot everything is fine. I haven't figured out what the problem here is. However, I remember seeing some error message popping up a couple of times, unfortunately it disappeared immediately. It said something about prefetching and an error. It was displayed too shortly so I could not read it. Any hints?

---

### Post by oldfred on 2012-09-07
If it is part of the boot process it probably is in the log file dmesg.

Use Log File Viewer and open dmesg. See if you can find the exact message, it is a long list of everything it loads. I always look for errors, long times between processes, or tasks repeating and then failing (or maybe even working).

---

