---
title: "ldlinux.sys hash checksum md5sum sha256 etc?"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by veiokej on 2014-05-16
I would like to know the hash (ideally SHA256 or harder) of this file for 14.04, 32-bit and 64-bit. Context:

[http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image](http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image)

Similar problem in another Linux distro:

[https://www.mail-archive.com/tails-support@boum.org/msg00331.html](https://www.mail-archive.com/tails-support@boum.org/msg00331.html)

---

### Post by papibe on 2014-05-16
Hi veiokej. Welcome to the forums ):P

This has all the information you need: [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

Hope it helps. Come here often and have fun.
Regards.

---

### Post by veiokej on 2014-05-16
Yes that page has some hashes of the ISOs, but how does one determine whether the hash of ldlinux.sys is correct? As explained in both links above, it seems that Startup Disk Creator actually installs diverse versions of this file, even when creating a boot image for the same ISO.

---

### Post by papibe on 2014-05-16
One of the links you provided was updated with a checksum example.

Using 'dd' would avoid any tampering with the creating of the bootable media.

Let us know how it goes.
Regards.

---

