---
title: "Unable to install or recover GRUB2."
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by JimDanger on 2010-07-17
Here's the skinny:

Currently running Windows 7 64-bit, with Windows installed on the second of 3 hard disks.

Was previously running Ubuntu 9.10 that I installed using wubi. After upgrading to 10.04 within Ubuntu, I wasn't able to boot into any OS and was met with a grub-rescue> prompt. Using a Win7 DVD, I ran: bootrec /fixmbr to get rid of Grub and get back into Windows.

I then decided to stop using wubi and go for a full install. Within Windows, I deleted all the partitions on one disk, the which is actually the first disk of the 3 I have. I then booted from USB to a 10.04 live environment and ran the install app. At the partition area, I picked sda as it was the disk I had allocated to install Ubuntu. The setup did its thing but after the reboot, it just defaulted to Windows with no Grub prompt or anything. I've since attempted all the steps in [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") but nothing seems to change and it just continues to boot into Windows 7.

Some things I'm wondering:
- I'm running Win7 64-bit, but wanted to use 32-bit Ubuntu...any problem with that?
- Would it be a problem that Windows 7, which was installed first, is installed on the second of 3 disks and not the first?

Any help is appreciated and let me know if you need anymore information!

---

### Post by oldfred on 2010-07-17
Since you installed to sda your grub2 was probalby installed to sda, but since your windows is on another drive are you booting that drive in BIOS? Try changing drive you boot in BIOS.

If you want to know where everything is installed:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by JimDanger on 2010-07-19
Apparently it *does* matter if you installed Windows on the second of 3 drives. I kept thinking Windows was on the first hard disk, because Window's Disk Management snap-in shows C: as Disk 0. I'm assuming Windows labels any disk the C: drive is on as Disk 0.

Anyway, I did:
```
fdisk -l
```

Which displayed everything on sda, sdb, and sdc. I saw Windows was on sdb1, and sdb5 was labeled "Linux." I ran:

```
sudo mount /dev/sdb5 /mnt
sudo mount /dev/sdb5 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

...and it worked!

---

