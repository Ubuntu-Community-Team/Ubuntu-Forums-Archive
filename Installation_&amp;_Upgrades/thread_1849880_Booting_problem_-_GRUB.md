---
title: "Booting problem - GRUB"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by kenik123 on 2011-09-25
Hello,
I have problem with GRUB 2 on ASUS EEE
I copy HDD data from old to new by command "sudo cp -a ..." (Because old is bigger than new..)
Them I CHROOT and reinstall grub.
Do not boot.

From live CD ubuntu i try reinstal GRUB by GRUB-Repair ( Grub to partition, grub to MBR nothing work)
 always i see after reboot

File not found
grub rescue>

log is here:
[http://paste.ubuntu.com/693717/](http://paste.ubuntu.com/693717/)

I try all I found on web for this problem but nothing help.

Thank you in advance for help.

Best regards

Vašek  Keberdle

---

### Post by drs305 on 2011-09-25
kenik123,

Welcome to the Ubuntu forums.

The first thing I notice in your RESULTS.txt is that the / and swap partitions have the same UUID in fstab. For now, we can try to repair fstab and see if just that change fixes things. Boot the LiveCD and mount your Ubuntu partition for editing:
```

sudo mount /dev/sdb2 /mnt
gksu gedit /mnt/etc/fstab
```


This will open fstab for editing. Change the first to the second:
> UUID=eb42bb1a-2587-4bbd-a57e-779e1c473582       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=986b31f1-0499-4e56-b4d4-8eafd18576d2 none            swap    sw              0       0
UUID=eb42bb1a-2587-4bbd-a57e-779e1c473582 none            swap    sw           $

> UUID=eb42bb1a-2587-4bbd-a57e-779e1c473582       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=986b31f1-0499-4e56-b4d4-8eafd18576d2 none            swap    sw              0       0
UUID=[COLOR="DarkRed"]**5f248bcb-3819-4575-8b5f-050dae2ddf11**[/COLOR]      none            swap    sw           $

Save the file, unmount the partition, then reboot:
```
sudo umount /mnt
sudo reboot
```

I don't know if that is the only problem, but at least it needs to be fixed.

---

