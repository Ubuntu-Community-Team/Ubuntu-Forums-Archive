---
title: "Problem with hard disk space"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2008-08-02
Hi there,

When it came out, I have installed Hardy on a 5.11Gb extended partition, my home folder is on another partition. There is 4.53Gb for the file system and 588Mb for the swap.

The file system partition is totally full. I am a bit surprised as I understood that over 4Gb should be plenty to run ubuntu...

There is no documents on that partition and I haven't installed major software that were not on the initial distribution...

How can I work out what is taking me so much space and how to clean it up... I am not used to go in the file system folder on linux...

Thank you for your help

---

### Post by iaculallad on 2008-08-02
> **gwu777 said:**
> Hi there,

When it came out, I have installed Hardy on a 5.11Gb extended partition, my home folder is on another partition. There is 4.53Gb for the file system and 588Mb for the swap.

The file system partition is totally full. I am a bit surprised as I understood that over 4Gb should be plenty to run ubuntu...

There is no documents on that partition and I haven't installed major software that were not on the initial distribution...

How can I work out what is taking me so much space and how to clean it up... I am not used to go in the file system folder on linux...

Thank you for your help

Drop to your terminal and try cleaning your cache file:

```

sudo apt-get clean
sudo apt-get autoclean
```

---

