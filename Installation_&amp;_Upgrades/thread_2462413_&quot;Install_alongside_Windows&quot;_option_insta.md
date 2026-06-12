---
title: "&quot;Install alongside Windows&quot; option installed system on wrong drive."
date: 2021-05-20
forum: Installation &amp; Upgrades
---

### Post by ezbie on 2021-05-20
Long story short, I wanted to avoid manual partitioning and there are 50GB of unallocated space in my SSD (Windows Drive). I set the installer to "Install Alongside Windows". The installation took too long and I noticed the system was super slow afterwards.


Well, guess what. My Windows drive is untouched: [https://i.imgur.com/aVDp3Lb.png](https://i.imgur.com/aVDp3Lb.png)

Ubuntu installed itself to drive 2: [https://imgur.com/a/4xGQU0C](https://imgur.com/a/4xGQU0C)

Two problems derive from this:

1. This option is broken. How comes that "Install alongside Windows" actually means: "Install in the next physical disk where there's free space"
2. I want to move the OS back to the 1st drive so as not to have to reinstall and configure everything again.

---

### Post by oldfred on 2021-05-20
We do not know the specific logic that the Install along side uses. But it was intended for single drive, shrink Windows or use space on Windows drive.
I once tried it on my multiple drive system and it seemed to choose the largest unused or available partition to shrink.

If you really want Ubuntu installed to a specific place, you have to use Something Else install option. And it really is required if you have multiple drives.

I suggest new install & restore from your normal backup.
That also confirms your backup includes everything you need.

---

