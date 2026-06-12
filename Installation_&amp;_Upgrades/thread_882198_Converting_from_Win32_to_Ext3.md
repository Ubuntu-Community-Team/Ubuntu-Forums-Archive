---
title: "Converting from Win32 to Ext3"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Sir Cabbage on 2008-08-06
Hi,

I recently installed Unbuntu for the first time, and managed to install it onto a Win32 file system.  (using Wubi, and Partition Magic... and being unable to select Ext3 in my version of PM.)

Question I have now, is wether I am stuck using the Win32 filesystem or if there is some "safe" method to convert the drive to Ext3 without corrupting my install in the process.

Or am I stuck to having to reformat the drive to Ext3, and then reinstalling.

I noticed in Gparted that I can convert from Win32 to Ext3.  Would this be a safe method?

Thanks!

---

### Post by SarahKH on 2008-08-06
Generally speaking moving from one file system to another is... risky.  In essence what the program will do is resize the existing partition as small as it can, copy X amount of data, resize, copy, resize and so on until the old partition is gone. 

It can work and work quite well.  It can also go apex over base.

If possible backup and go with ext3 from the get go.  If you can't... backup anyway ;)

---

### Post by logos34 on 2008-08-06
[LVPM]("http://lubi.sourceforge.net/lvpm.html") is a safe way to convert your Wubi install to a dedicated ext3 partition without having to reinstall

---

