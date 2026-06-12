---
title: "Custom Install | Partition Scheme - Dell XPS 14"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by JCChristian on 2013-05-25
Hello friends, I have a XPS 14 (specs below) and I want to install Ubuntu 13.04 but as you can see, the notebook have mSATA + HDD, and it would be great if anyone could help me in the best way to manage the installation/partitioning of the OS.

Gorilla Glass 1600x900 HD+
i7 3517U
GT 630M
4GB DDR3 1333Mhz
Momentus Thin (500GB)
mSATA Samsung (32GB)
Centrino Advanced-N 6235 + BT4.0
[...]

The system will be used for programming, web, texts, videos, "light" image edit, etc.

I have in mind this scheme (Ubuntu only, I won't use Dual boot):

/ -> 8GB (mSATA)
/usr -> 6GB (mSATA)
/var -> 4GB (mSATA)
/tmp -> 100MB (mSATA)
"9917 MB free mSATA" -> What I put here? ;)

/home -> 500GB (HDD)

---

### Post by 2F4U on 2013-05-26
You should plan for a larger / partition. Is there a special reason for separating /, /usr, /var and /tmp. While this makes sense on a server with multiple hdd's, it doesn't make much sense on a laptop with just one hdd (except that it makes things more complicated). It seems that you are not planning to create a SWAP partition, which seems a bit strange to me.

---

### Post by JCChristian on 2013-05-26
I read more and ended up with:

/ -> 500GB HDD

efi -> 500MB mSATA
/boot -> 500MB mSATA
/tmp (tmpfs File System) -> 8GB mSATA
/usr -> "rest" mSATA

Is it enough to build a secure notebook for programming, image edit, web, texts, and so on?

---

