---
title: "Dual Boot, Windows 7 and Ubuntu 13.10"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by AyJJ7fd on 2014-01-09
Hello all. Currently my setup is a bit wonky, with a Windows drive and a Ubuntu drive (both internal). Both work, but don't play nice together, and I have to boot into BIOS each time I want to boot into Windows.
My goal is to have both drives show up in grub, and be able to easily boot Ubuntu or Window with a simple boot menu.
Now, I have no important data on either drive, so I'm able to reformat and partition the drives any way that would make this setup work.
I am a beginner when it comes to drive partition types, so if you could please spell out any instructions I need, that would be great.
Thank you for your help!

---

### Post by electrohandyman501 on 2014-01-09
Since no one else has asked yet..... what version Windows and Unbuntu.

---

### Post by deadflowr on 2014-01-09
Boot into Ubuntu and tell us
what is the output for
```
sudo update-grub
```
run this command in a terminal.

---

### Post by AyJJ7fd on 2014-01-22
> **electrohandyman501 said:**
> Since no one else has asked yet..... what version Windows and Unbuntu.

Windows 7 and Ubuntu 13.10

> **deadflowr said:**
> Boot into Ubuntu and tell us
what is the output for
```
sudo update-grub
```
run this command in a terminal.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Ubuntu 12.10 (12.10) on /dev/sdc2

---

### Post by deadflowr on 2014-01-22
Interesting.
Now, quick question, when using Ubuntu(because I know Windows wouldn't work) can you access the Windows drive.
Opening the file manager, is the windows drive listed in the side panel devices section?

---

### Post by AyJJ7fd on 2014-01-22
> **deadflowr said:**
> Interesting.
Now, quick question, when using Ubuntu(because I know Windows wouldn't work) can you access the Windows drive.
Opening the file manager, is the windows drive listed in the side panel devices section?

Yes, there is a 1TB drive (the Windows drive). Its listed, but I cannot access it:

"Error mounting /dev/sda2 at /media/XXX/2C3771603FEA0CBD: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/XXX/2C3771603FEA0CBD"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

---

### Post by deadflowr on 2014-01-23
> [COLOR=#000000]"Error mounting /dev/sda2 at /media/XXX/2C3771603FEA0CBD: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dm ask=0077,fmask=0177" "/dev/sda2" "/media/XXX/2C3771603FEA0CBD"' exited with non-zero exit status 14: **Windows is hibernated**, refused to mount.[/COLOR]
[COLOR=#000000]Failed to mount '/dev/sda2': Operation not permitted[/COLOR]
[COLOR=#000000]The NTFS partition is in an unsafe state. **Please resume and shutdown**[/COLOR][COLOR=#000000]**Windows fully (no hibernation or fast restarting)**, or mount the volume[/COLOR]
[COLOR=#000000]read-only with the 'ro' mount option."[/COLOR]

Your error message says it is in hibernation, which means it never fully shutdown.
You'll have to figure out how to shut it down.
I have no clue about that.
But therein lies the issue.

---

### Post by AyJJ7fd on 2014-01-23
> **deadflowr said:**
> Your error message says it is in hibernation, which means it never fully shutdown.
You'll have to figure out how to shut it down.
I have no clue about that.
But therein lies the issue.

Ok, fixed that issue fairly quickly. Now I can access the Windows drive. Now what?

---

### Post by deadflowr on 2014-01-23
If you re-run the update-grub command is the windows entry listed?

---

### Post by AyJJ7fd on 2014-01-24
Figured everything out. Had to repartition my Ubuntu drive to MBR, then it worked out fine.

---

### Post by Rick1971 on 2014-01-24
huh.Ii have no problem and I have the same type of setup

---

