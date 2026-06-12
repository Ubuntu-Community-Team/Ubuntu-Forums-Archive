---
title: "Ubuntu boot broken after reinstalling XP (dual-boot pc)"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by macguges on 2014-02-16
I'm posting a new thread for BudTuba's issue, [http://ubuntuforums.org/showthread.php?t=2204900](http://ubuntuforums.org/showthread.php?t=2204900)  I appreciate that my dad tried to get help on his own while I was away; now that I'm here tonight, I'm stumped too.

When I was here a week ago, I ran grub-install after reinstalling Windows XP for my dad.  I had confirmed that both Ubuntu and XP would boot from grub before I left.  Today I observe that choosing Ubuntu from the grub menu immediately leads to a blank text screen with a flashing underscore, and that syslog hasn't recorded any new messages since the night I left.

Tonight I found a tool called Boot-Repair, and I tried it, using the default options.  grub.conf had looked sane to me, I'd confirmed the kernel was passed a correct uuid for the root partition, but I figured I would try the novice-friendly tool.  It reinstalled grub, rewriting grub.conf, and produced a logfile [http://paste.ubuntu.com/6945794/](http://paste.ubuntu.com/6945794/)  However, our boot issue remains.

Is it possible the initrd is corrupt?  I'm reasoning that if the grub stage is correctly configured, the next boot stage is the initrd.  It's difficult to test any ideas without feedback either on-screen or written to the filesystem.  I'll look into kernel boot options next.

Thank you for any suggestions.

---

### Post by varunendra on 2014-02-16
> **macguges said:**
> grub.conf had looked sane to me, I'd confirmed the kernel was passed a correct uuid for the root partition..

Its current state doesn't look sane to me. Your current fstab -
```
UUID=169C6F5F9C6F387F /media/Windows_D ntfs-3g users 0 0
UUID=94e4cd7f-097d-4794-9d78-84b7f3ab4926 / ext4 users 0 1
UUID=1769F3AD485785EF /media/Big_Boy ntfs-3g users 0 0
UUID=851b152e-8992-418b-adde-a4b30f7479cb swap swap sw 0 0
UUID=2830BEEB30BEBEDE /media/Old_Drive_D ntfs-3g users 0 0
**[COLOR="#FF0000"]#[/COLOR]UUID=c21f156a-a450-4409-bb3d-4a518f777029 /boot** ext2 users 0 2
```

So it seems your original mount-point entry for /boot is commented out (by Boot-Repair). In this case, I believe the "set root=" and "root=UUID=" entries should point to the same partition, while the "set root" entries in your grub.cfg are still pointing to /dev/sda5 (which is no longer mounted by fstab).

My understanding and troubleshooting skills with boot problems have become very rusty (I had given up when UEFI became de-facto for newer laptops), but I think you can easily reinstall grub manually to make everything good again, provided you know very well what is where and are sure that Ubuntu itself is not broken.

But.... if you are unsure, and/or there is not much to save on the Ubuntu installation, wouldn't it be easier to simply reinstall Ubuntu selecting correct mount points?

**PS.**
Why have you selected a separate partition for /boot? I don't see much advantage in that.

---

### Post by macguges on 2014-02-16
I've learned/realized that I had another option,  Recovery Mode.  From here I tried the different menu options.  Choosing options other than the root shell led to an infinite loop; within the root shell, remounting the filesystem read-write did not work.  I remembered that BudTuba had changed his /etc/fstab weeks ago, [http://ubuntuforums.org/showthread.php?t=2194669](http://ubuntuforums.org/showthread.php?t=2194669)

Using the LiveCD I reverted the /etc/fstab.  Then when I chose "repair broken packages" from the Recovery Mode menu, that script ran without errors, selecting several packages to download. After this process completed, the Unity desktop came up.  So I then rebooted, selected the standard Ubuntu option from grub, and confirmed that the system would again boot normally.

We did notice an unusual delay during the current boot sequence.  For several seconds there was a black screen in a high resolution graphics mode.  It happened again while rebooting, but it's still quite tolerable.

---

### Post by macguges on 2014-02-16
> **varunendra said:**
> Its current state doesn't look sane to me. Your current fstab -
```
UUID=169C6F5F9C6F387F /media/Windows_D ntfs-3g users 0 0
UUID=94e4cd7f-097d-4794-9d78-84b7f3ab4926 / ext4 users 0 1
UUID=1769F3AD485785EF /media/Big_Boy ntfs-3g users 0 0
UUID=851b152e-8992-418b-adde-a4b30f7479cb swap swap sw 0 0
UUID=2830BEEB30BEBEDE /media/Old_Drive_D ntfs-3g users 0 0
**[COLOR=#FF0000]#[/COLOR]UUID=c21f156a-a450-4409-bb3d-4a518f777029 /boot** ext2 users 0 2
```

So it seems your original mount-point entry for /boot is commented out (by Boot-Repair). In this case, I believe the "set root=" and "root=UUID=" entries should point to the same partition, while the "set root" entries in your grub.cfg are still pointing to /dev/sda5 (which is no longer mounted by fstab).

I could've been mistaken, but I had assumed those different UUIDs reflected that grub and the kernel would have different roots, when grub is installed to a different partition from the primary filesystem.

> **varunendra said:**
> 
**PS.**
Why have you selected a separate partition for /boot? I don't see much advantage in that.

Having a separate /boot partition allows you to use a more conservative filesystem to store the kernel and boot loader, possibly protecting the kernel from corruption.  Since the operating system does not need these after boot-up, unmounting these files reduces risk of accidental changes to these files.

---

