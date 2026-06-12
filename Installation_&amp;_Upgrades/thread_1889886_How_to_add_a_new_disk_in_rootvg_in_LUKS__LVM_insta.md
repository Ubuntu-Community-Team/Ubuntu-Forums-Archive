---
title: "How to add a new disk in rootvg in LUKS / LVM installation"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by albundy83 on 2011-12-02
Hello,

I have setup my Ubuntu 11.10 installation with the following parameters :
- LVM with a main volume group called rootvg,
- 3 logical volumes called lv_home, lv_root and lv_swap,
All this is encrypted using LUKS.
My first hard drive is called /dev/sda.
My encrypted partition is /dev/sda5.

I like to add a new physical disk called /dev/sdb to extend my volume group rootvg and create a lv_downloads (to mount a /Downloads).
I like to encrypt it also and use the same encryption....

Does someone could help me please ?

---

### Post by albundy83 on 2011-12-02
Another question.... Is it possible to decrypt 2 disks with one passphrase at boot?

---

### Post by albundy83 on 2011-12-05
Any one could help me please ?

---

### Post by awh018 on 2012-05-09
Hello,

I was wondering if you ever got any further on this. I have a similar setup and I'd like to know how to add a new drive to my encrypted LVM setup. Searching relevant terms hasn't helped me much. I've found a lot of info on adding drives to unencrypted LVM, but not encrypted. I've seen references to modifying startup files in order to decrypt the new drive, but nothing specific about what those files/modifications need to be.

Thanks.

---

