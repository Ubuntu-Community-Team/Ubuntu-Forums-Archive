---
title: "Choosing a FS"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by chrisrx on 2008-09-12
I've got a new hard drive for my laptop so I'm going to transfer everything over.  But what I want is a data partition that is readable/writable under linux/windows/OSX.  I know that ext3 can be read under windows and osx with some additional downloads, and NTFS with OSX and linux(although not sure how stable it is on linux)
So what would be my best option, be it one of the above or other?

---

### Post by Sef on 2008-09-12
Most people go with an NTFS partition.  NTFS-3g is stable now.

---

### Post by SunnyRabbiera on 2008-09-12
ext3, no constant defragging.

---

### Post by chrisrx on 2008-09-12
What is the performance like for ext3 under windows?  I read that it runs without journalling so I don't know if that makes a difference.

---

### Post by Vivaldi Gloria on 2008-09-12
> **chrisrx said:**
> What is the performance like for ext3 under windows?  I read that it runs without journalling so I don't know if that makes a difference.

You need to install [http://www.fs-driver.org/](http://www.fs-driver.org/). It reads it as ext2 so yes, no journal. I am happy with the speed and stability. But some people said that it's not stable enough though I don't know why.

---

