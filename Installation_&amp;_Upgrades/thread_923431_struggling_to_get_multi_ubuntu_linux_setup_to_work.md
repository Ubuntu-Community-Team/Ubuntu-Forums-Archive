---
title: "struggling to get multi ubuntu linux setup to work"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by falinx on 2008-09-18
Hey everybody,

I'm not really that new to linux but since I decided to start studying towards linux+ I've opened up a huuuuuuuge can of worms :).

So heres the issue, I can't get my 2nd hard drive to boot up. I have used the cp -ax option (after mounting and creating the partitions successfully) to backup all data to the new drive. I then grub-install on the drive to "grub" it. Now I need to be able boot it. Initially I was going to make it the primary drive and remove the original drive but that was overzealous of me... it's just never going to happen it would seem :) So I decided to settle for second place and just use the initial drive as the mbr with the boot loader etc but to no avail. If I try and amend menu.lst to point to the new drive it just boots up the old installation. Another thing that boggles my brain is how the frick /etc/fstab mounts drives in order to boot them. hd0 is not sda1 etc... I'm lost... very very very lost and I've been working on this issue for like 2 days.... Can anybody help pretty plz????

---

### Post by Elfy on 2008-09-18
Could you post some information for us :) Please use [noparse]```

```[/noparse] tags around each please.

```
sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
cat /boot/grub/device.map
```

---

