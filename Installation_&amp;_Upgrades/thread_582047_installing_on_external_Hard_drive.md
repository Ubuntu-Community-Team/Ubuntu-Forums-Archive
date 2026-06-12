---
title: "installing on external Hard drive"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by keeler1 on 2007-10-19
After searching through the numerous posts on this I have not found exactly what I am looking for.

After getting all of the partitions set up the way I want and everything ready to go i need to tell it what drive to put grub in.  It says hd0.  However I dont really know which drive hd0 is.  Is it my internal drive sda or my external sdb?  

How can I find this out?

---

### Post by confused57 on 2007-10-19
> **keeler1 said:**
> After searching through the numerous posts on this I have not found exactly what I am looking for.

After getting all of the partitions set up the way I want and everything ready to go i need to tell it what drive to put grub in.  It says hd0.  However I dont really know which drive hd0 is.  Is it my internal drive sda or my external sdb?  

How can I find this out?

I believe there is an "Advanced" button that you can select when you're prompted to install grub...type in:
```
/dev/sdb
```
this should ensure that grub is installed to the external hard drive's mbr

You should have your external hard drive selected to boot before your internal hard drive, before you boot the live cd to install Ubuntu...

---

