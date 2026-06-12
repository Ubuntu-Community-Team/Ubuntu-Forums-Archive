---
title: "Just a general question about Karmic and Ext4?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-10-24
OK.... So since Karmic uses Ext 4 does that mean that I won't be able to upgrade with a dist-upgrade and the whole HDD would need to be formatted in ext4 for it to be useable?

---

### Post by flipper9 on 2009-10-24
You could have formatted with EXT4 back in Jaunty, but that wasn't the default unless you partitioned manually.

You CAN convert your EXT3 to EXT4, but the data already on the drive won't benefit as much from the speed improvements.  It's better to just reformat and start over to get the best performance IMHO.  Note that the distribution upgrade will not do the conversion from EXT3 to EXT4 for you, you'll need to lookup how to do that.  There are HOWTO documents for that.

Thread with more info on this exact question: [http://ubuntuforums.org/showthread.php?t=1282478](http://ubuntuforums.org/showthread.php?t=1282478)

---

### Post by maartendr on 2009-10-24
No, with an upgrade, you will continue tu use ext3 (and grub 1). Only with a clean install you can choose to use ext4

---

### Post by philinux on 2009-10-24
> **cptrohn said:**
> OK.... So since Karmic uses Ext 4 does that mean that I won't be able to upgrade with a dist-upgrade and the whole HDD would need to be formatted in ext4 for it to be useable?

Upgrading from jaunty will still leave ext3 and legacy grub. You can upgrade to ext4 but you will not get the full performance gains.
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

Scroll to the top for full explanation.

---

### Post by cptrohn on 2009-10-24
Thanks for the replies and all the great information folks!

Lots to look at!

---

