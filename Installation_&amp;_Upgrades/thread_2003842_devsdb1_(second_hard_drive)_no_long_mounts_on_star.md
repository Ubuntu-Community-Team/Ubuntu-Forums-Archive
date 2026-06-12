---
title: "/dev/sdb1 (second hard drive) no long mounts on startup"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by chrisgclark on 2012-06-14
Hi,

I installed Ubuntu 12.04 last weekend and my second hard drive automatically was mounted in /media/SecondHardDrive when Ubuntu first booted.  

Yesterday a bunch of upgrades installed and now my second hard drive does not auto mount.  I can see it in the BIOS and the hard drive can be mounted using:

sudo mount /dev/sdb1 /media/SecondHardDrive -t ntfs

I can view all the hard drive's files under /media/SecondHardDrive so hard drive is working fine.  

Any ideas why it has stopped auto mounting?   This was useful as it displayed an icon for my second hard drive on the left hand task bar and didn't require a mount command to access my files.

Thanks.

Chris

---

### Post by darkod on 2012-06-15
Check whether you have an entry for it in /etc/fstab with:
```
cat /etc/fstab
```

If there is none, you should make an entry which would be something like:

```
/dev/sdb1   /media/etcetc   ntfs   defaults   0   0
```

Note: Do that with the partition unmounted. To test, execute:
```
sudo mount -a
```

That should mount it or report any errors that might exist.

---

### Post by chrisgclark on 2012-06-15
Hi Darkod,

Adding the following to /etc/fstab worked perfect and I can now see the second hard drive on the left hand task bar following a reboot.

[B]/dev/sdb1 /media/SecondHDisk    ntfs    defaults    0    0
[/B]
Thankyou for your help.

Chris

---

