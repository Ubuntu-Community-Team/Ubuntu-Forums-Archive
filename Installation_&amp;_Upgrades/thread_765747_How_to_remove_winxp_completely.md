---
title: "How to remove winxp completely?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by shelper on 2008-04-24
i have windows on my system
and i am installing ubuntu, moreover, i decide to give up windows completely
so, i wish after that i can delete windows completely
any idea how to do that?
like remove the whole partition?
and how can i merge the left free partition with ubuntu?:confused:

thanks atan!

---

### Post by gpilkay on 2008-04-24
If it's a fresh Ubuntu install, it's actually very easy, just tell it when the installer asks about partitions, let it use the entire disk (it's an option).  This is how I got rid of a broken and useless Windows ME installation.  While I prefer a duel boot, that old system was hopeless with Windows.  It works great with plain old Ubuntu, though.

---

### Post by logos34 on 2008-04-24
If you don't want to get rid of windows right away and overwrite the whole disk during installation as gpilkay suggested, you could use gparted on the live cd at some later date to delete XP partition, then grow/expand ubuntu left into the freed space.  This might take several hours, however. Just make sure during ubuntu install that root (/) and not /swap is right after windows.

---

### Post by Paul Gardil on 2008-04-24
If you want to keep your current Ubuntu (not do a fresh install), use gparted to delete the Windows partition, then expand the Ubuntu partition to use the freed space.  You may still see Windows in the boot menu (although choosing it would result in a grub error).  To get rid of it, do:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup
sudo gedit /boot/grub/menu.lst
```
Then look for the Windows item (probably at the end), delete all the lines in that paragraph (title, root, savedefault, makeactive, chainloader), and save the file.  Next time you boot, Windows will be gone from the menu.

If you make a mistake you can get back your old menu.lst from /boot/grub/menu.lst.bkup.

---

### Post by calraith on 2008-04-24
If you want to grow your existing Ubuntu installation, you'll have to use a [GParted live cd]("http://gparted.sf.net/livecd.php") to delete the NTFS partition, resize your ext3 (or whatever Linux filesystem you use -- not all can be resized), and possibly move or delete and recreate your swap partition.  After your partitions have been resized and rearranged, you'll need to mount and chroot to your system from the CD operating environment.  You'll have to modify /etc/fstab, since the UUIDs of your partitions will have changed.  You'll also need to modify /boot/grub/menu.lst to make sure grub is looking to boot the correct partition, and to remove the boot entry for Windows.  Finally, you'll need to rerun grub-install /dev/sda.  **Back up important documents and any customized configuration files and other stuff that'd be a pain in the butt to recreate before repartitioning!  **Although you'll be OK if you're careful, lots can go wrong when you mess with your partition tables.  It's safest to assume that you are going to blitz your system and be prepared to reinstall from scratch just in case.

- or -

You could just delete the contents of your NTFS partition and use it as storage / backup.  It's handy to have a storage partition not part of your root filesystem in case you ever want to wipe out and reinstall Ubuntu.

---

### Post by shelper on 2008-04-28
thank you guys so much!

---

