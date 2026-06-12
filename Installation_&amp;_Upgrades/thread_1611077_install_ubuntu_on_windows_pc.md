---
title: "install ubuntu on windows pc"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Chelidze on 2010-11-01
I have windows installed on my pc and i have my hdd partition into C and D
 Windows is installed on partition C and have important  data stored on D
Here what i want : I want to delete windows and install ubuntu on c Drive but keep D partition and use  its files in future and is there a way to do so  8-[

---

### Post by mörgæs on 2010-11-02
I would do the following: 

Defragment Windows a couple of times.
Shrink the Windows partitions to make room for Ubuntu.
Install Ubuntu in the free space
While booting from Ubuntu, copy the files you need to /home
If you want, now you can delete the Windows partitions.

---

### Post by coffeecat on 2010-11-02
> **Chelidze said:**
> I want to delete windows and install ubuntu on c Drive but keep D partition and use  its files in future and is there a way to do so

Yes, there is a way to do that, but it is very inadvisable. Why? Because your 'D:' partition is probably formatted NTFS which is a Microsoft filesystem. Ubuntu can read and write to a NTFS filesystem very reliably but if you were to suffer filesystem corruption you would need the Windows utility chkdsk to repair it. There is no Linux utility that can do everything that chkdsk can do. NTFS is a perfectly reasonable choice for a data partition, but only when you are dual-booting with Windows. Otherwise use a Linux filesystem.

If you are sure you want to erase Windows in that machine, it would be better to backup your files onto another medium and reformat the whole drive for use by Ubuntu. You could create a separate /home partition as the previous poster suggests if you wish, but copy the files back onto the internal drive only once you have finished installing Ubuntu and you have a working system.

---

