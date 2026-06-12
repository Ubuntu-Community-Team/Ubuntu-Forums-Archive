---
title: "About checking the MD5 of Ubuntu iso"
date: 2016-06-30
forum: Installation &amp; Upgrades
---

### Post by helm10101 on 2016-06-30
Is it possible that my iso file is not 100% matching the download, but Ubuntu will still let me install, and I will actually have a working Ubuntu but that is working with lower performance than expected? 
(Assuming I didn't check Md5 before installation), Or it can't be, and if I managed to install it, it means it installed as it should?

I always have a thought that I might install something with some broken files in it, but they're not seen so I won't be able to tell 

Thanks!

---

### Post by Liam_Murphy on 2016-06-30
It kind of depends.

If someone actually tampered with the ISO, like in the case of the Linux Mint hack some time ago, everything looked normal but it was tampered with.

Otherwise, an ISO will either really work, or really mess up, overall you shouldn't have to worry about what you've stated. 

Case in point, always check before installing a new OS.

---

### Post by sudodus on 2016-06-30
There are two ways to check the md5sum.

***1. Check the whole iso file with md5sum versus the listed value*** at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

```
ubuntu-16.04-desktop-amd64.iso
```

***2. The packages in the install drive with the menu option***

'Check the disk for defects'

-o-

If there is a checksum error, it depends very much *where* it is. Some program package might be damaged, that you are not using (at least not during the first few days). But if the checksum is bad, there is often a big damage, and you will not be able to create a working boot drive from the iso file.

Most bad iso files are caused by bad internet connections. The quality of internet connections is improving over time, and bad downloads are less common nowadays compared to a few years ago. One failure is that the connection failed before the whole file was downloaded. So the file is too small. Using a torrent is reliable because it checks the md5sum automatically. The same holds for zsync which is available at the [Ubuntu QA testing tracker](http://iso.qa.ubuntu.com).

I think most failures at 'Check the disk for defects' (when the iso file was good) are caused by bad burning, for example a failing optical drive or too high burning speed. It is a good idea to burn at the lowest possible speed.

Flashing the iso file to a USB pendrive is very reliable with cloning tools, but can fail with tools that depend on interpreting the internal structure of the iso file, if the tool is not up to date with the particular linux system in the iso file. If a USB pendrive is bad (physically bad with damaged sectors of memory cells), it will usually be read-only or dead, rather than accept writing but not store the data correctly.

---

