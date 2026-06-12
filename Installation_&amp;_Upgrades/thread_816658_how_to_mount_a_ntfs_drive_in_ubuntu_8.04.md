---
title: "how to mount a ntfs drive in ubuntu 8.04"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by krishnakittu on 2008-06-02
i have 3drives which are in ntfs format.i have data in those drives.when i am trying to access the drives it is showing to mount the drives.when i did so the following message is shown
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /mnt/mount -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /mnt/mount ntfs-3g force 0 0



can u plz...help me out of this problem:(

---

### Post by Pumalite on 2008-06-02
Close Windows down properly.

---

### Post by aysiu on 2008-06-02
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo mount -t ntfs-3g /dev/sda6 /mnt/mount -o force
```

---

### Post by ladr0n on 2008-06-02
Boot into windows and shut down properly.  This kind of thing happens when you either hibernate Windows (which causes Windows to vomit the contents of its RAM all over your hard drive in the form of pagefiles), or Windows doesn't properly clean up its NTFS journal before shutting down.  

In other words... Choice 1

--Edit--
If he forces the mount, couldn't that potentially corrupt the NTFS volume?  I may be wrong, but I was under the impression that forcibly mounting an NTFS partition was a bad idea.

---

### Post by jualin on 2008-06-02
the "force" command should work however when you get that message is because of an unclean shutdown so you should access windows and shut it down correctly.

Edit: I think it may corrupt the NTFS file system, if it wasn't a bad idea then I assume that you would not have to "force" the mount. So I would go for the clean shutdown

---

### Post by kvarley on 2009-03-20
I can't do a clean shutdown of the drive from windows as I installed Ubuntu over it.

---

### Post by Pumalite on 2009-03-20
Post:
```
sudo fdisk -lu
```

---

### Post by Mark Phelps on 2009-03-20
> **vitium said:**
> I can't do a clean shutdown of the drive from windows as I installed Ubuntu over it.

Huh?? You can't install Ubuntu natively in an NTFS partition; you can only install it in an NTFS partition "inside Windows" via Wubi.  And, in that case, Windows is still there and bootable.

Don't understand how you can have Ubuntu sitting in an NTFS partition without Windows.

Perhaps the fdisk will tell us.

---

### Post by jualin on 2009-03-22
> **vitium said:**
> I can't do a clean shutdown of the drive from windows as I installed Ubuntu over it.

Are you using Ubuntu 9.04 or 8.04?
If you want to mount a NTFS partition that was not shutdown properly, use the force command and force it to mount as described above. Hope this helps!

---

