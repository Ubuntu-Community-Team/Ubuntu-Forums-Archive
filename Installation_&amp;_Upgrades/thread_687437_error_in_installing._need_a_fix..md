---
title: "error in installing. need a fix."
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by LiterateBadger on 2008-02-04
Hi, I have a feeling my question is answered somewhere in this site but I cannot find it. I've tried to install Ubuntu on my Laptop. It's an IBM Thinkpad T40. Recently Windows XP Professional died on me, I solved this problem (I thought) by getting a copy of Ubuntu, however I cannot install the OS onto my harddrive. I have a horrid feeling that this is because my hard drive is broken and that it wasn't just some software problem. I've deleted everything on the harddrive in the hope that it would fix the problem, however it hasn't. I get an error message when I reach 5% on the 'installing sytem' box which reads > The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed Please help me if you can, Thanks.

---

### Post by stooshbunutu on 2008-02-04
There are a number of things to try

1. Check the download with the [MD5sum]("http://releases.ubuntu.com/7.10/MD5SUMS") to see if it complete (use program [MD5Summer]("http://www.md5summer.org/"))
2. Burn the disk at a lower speed to reduce errors
3. If this doesn't work it could be that you need to install via the alternate CD, Tick the little box on the download page.

This is what I had to do, hope this helps. :)

---

### Post by manimal347 on 2008-02-04
It's not free software, but I'd recommend to see if you can't borrow a copy of Spinrite from a firned. checks the licensing agreement first, though.

It's easy to use, and a golden standard. Or, just boot a Windows 98 "DOS" floppy and try doing a format with "quick" disabled. It will verify that every sector on the drive can hold data. You'll need to Fdisk it first, though, to kill your EXT3 partition and make an NTFS of FAT32 partition.

---

### Post by stooshbunutu on 2008-02-05
sorry that was my mistake in my haste i imbedded the wrong link, the correct and free version is here

[MD5Sum]("http://www.nullriver.com/index/products/winmd5sum")

Again very sorry about that:(

---

