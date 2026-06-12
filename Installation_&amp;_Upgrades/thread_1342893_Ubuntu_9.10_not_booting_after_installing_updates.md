---
title: "Ubuntu 9.10 not booting after installing updates"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by axelredd on 2009-12-01
Hello I am new to Ubuntu, first time I installed it so sorry if this question has been asked before. I don`t even know what to search for on the forums :|

My problem is that after installing the Ubuntu updates last night I started having problems booting it. I remember getting some error about GRUB but I didn`t even know what GRUB was so I kinda ignored it :(

What happens is that after I choose Ubuntu from GRUB, the logo appears and then after some (loading) time, the screen goes black and CapsLock keeps bleeping (???)

I installed it from a usb stick, on another partition than WinXP. Like I said, everything worked well until the damn updates :/

Anybody who can tell me what to do, or point me to the right (already opened) thread?
Thank you in advance :D

---

### Post by darkod on 2009-12-01
After the update, do you still have the old kernel version 2.6.31-14 in grub menu? If you do, try if that will boot correctly. 31-15 might not work, but 31-14 yes.

---

### Post by axelredd on 2009-12-01
I get the same error :s

Should I reinstall it and just wait with the updates until they are more stable?

---

### Post by darkod on 2009-12-01
Not yet, reinstall grub2 first. Something else might have caused it, I did the updates too and it's fine.

You can reinstall grub2 like this:
Boot with the ubuntu cd and select Try Ubuntu. Then open terminal (Applications -> Accessories -> Terminal) and execute:
sudo fdisk -l (small L)

Post the results back and I'll tell you how to proceed for grub, I need some info from the fdisk. You can get online with Try Ubuntu option too, so just post those results and I'll be waiting to tell you what to execute next.

---

### Post by axelredd on 2009-12-01
Ok, will do as soon as I am back home.

Thanks for the swift replies btw :)

---

### Post by axelredd on 2009-12-01
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       30401   223713157+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+  83  Linux
/dev/sda6            5101       17653   100831941    7  HPFS/NTFS
/dev/sda7           17654       30401   102398278+   7  HPFS/NTFS

Disk /dev/sdb: 4039 MB, 4039114752 bytes
37 heads, 36 sectors/track, 5922 cylinders
Units = cylinders of 1332 * 512 = 681984 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5923     3944444    b  W95 FAT32

Is this what you wanted to see?

---

### Post by darkod on 2009-12-01
OK, from this it seems /dev/sda5 is your Ubuntu partition of 20GB.

If you have booted with the ubuntu cd as I said previously, now in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

See if any error are reported during the grub install. If not reboot and check how is it working.

---

### Post by axelredd on 2009-12-01
Sorry for the late reply. Something happened with my ISP and I could not connect until now.

I did what you said in your last post, gave me no error whatsoever but it still did not fix the problem. :(

---

### Post by Lacho on 2009-12-01
I had the same problem, followed the advice of reinstalling Grub from the Live CD follwing step #12 Reinstalling GRUB 2 from LiveCD in [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275).

it basically said what was stated here, but I keep having the same problems, and now a screen came up during reboot asking me which Grub I wanted to run, and then another blue screen asking if I wanted to liberate space for the swap and other options.

I will once again reinstall Grub, and keep you posted.

---

