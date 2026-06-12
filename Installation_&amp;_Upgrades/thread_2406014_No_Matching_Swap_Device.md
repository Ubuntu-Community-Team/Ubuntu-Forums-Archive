---
title: "No Matching Swap Device ???"
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2018-11-14
Couldn't find relevant post regarding the following ... after upgrading to v18.04, received this upon minor updates after upgrade.

```

Processing triggers for linux-image-4.15.0-39-generic (4.15.0-39.42) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-39-generic
W: initramfs-tools configuration sets RESUME=UUID=62451ed9-5502-4838-b7c7-db9320a57dbd
W: but no matching swap device is available.

```

Not sure what this means or how to handle it. Any suggestions?

Thanks!

---

### Post by TheFu on 2018-11-14
Looks like there is/was an extra line in your /etc/fstab for an old swap device. 
Start by looking there and comparing the UUID with the output from **blkid** for the swap device.
If you change anything, rebuild the initramfs.

That's just a guess.

---

### Post by Rick St. George on 2018-11-15
YES ... somehow it was not correct. So corrected it, rebooted, and have not seen the error.
Thanks!

---

### Post by TheFu on 2018-11-15
Glad you figured it out.

i don't have 18.04 here, but remember seeing something about 18.04 changing from a swap partition to a swap file.
Just a guess. Haven't seen mention of this issue before, but I've been avoiding 18.04 questions.

For more generic info about swap - [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  I don't know how much it has in it.  I looked at the way they say to create a swap file and it isn't the way I'd do it. Typical.  There are 500 different ways to do anything on Linux. ;)

---

