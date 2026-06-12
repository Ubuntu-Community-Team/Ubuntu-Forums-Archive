---
title: "Low Disk Space ~650mb"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by PaperProjects on 2012-11-20
An error message saying "low disk space" and a notification of about 650 mb left will pop up every startup. This is strange because on checking GParted, the "D:" disk (I'm a windows user too) sdb1, which is the host and only sdb partition, has about 13gb unused. I attached a screenshot below.

I checked some other threads, and it says to allocate more disk space to ubuntu, which is strange because ubuntu isn't actually a partition. Everything is pretty much the same in GParted LiveCD.

If it helps, I installed ubuntu from windows XP. I don't really want to reinstall ubuntu, just give it more space.

---

### Post by JKyleOKC on 2012-11-20
Since you installed from XP, you may have done so with the "wubi" package that creates a large Windows file, then installs Ubuntu inside that file. If so, then the "disk" that Ubuntu sees is only the size of that large Windows file.

However, your D: drive in Windows may well NOT be the /dev/sdb drive in Ubuntu. Take a look, with gparted, at /dev/sda also; if it shows more than one NTFW partition, the one nearest the end of the drive is probably your D: since Windows mis-labels partitions as "drives." If this is the case, you can make note of the number (such as /dev/sda2) for that second partition, then use Ubuntu's file manager to look inside that partition. If you find, there, a large file named "ubuntu" or possibly "root.disk" then you do have a "wubi" installation and someone else will have to guide you through the technique of increasing its "disk size" since I don't know the details. However, you might find Ubuntu partitions on /dev/sda also, and in that case you probably have a "normal" side-by-side installation.

Let us know how these tests come out and one of us will be able to give you more detail on how to make use of your space!

---

### Post by PaperProjects on 2012-11-21
Right, so I've used Wubi to install ubuntu alongside Windows XP. I've attached 3 screenshots below showing you the layout of the "D:\ubuntu" folder. I'm absolutely sure ubuntu is installed in the D: folder.

I think that all my files are locked within the "root.disk" file, which explains why I'm running out of space. Is there a way to expand that filesize so I can have more space. Perhaps it would just be better for me to not use Wubi, but I would still like to use Windows XP.

---

### Post by darkod on 2012-11-21
Not using wubi, in other word using a normal ubuntu installation on its own partition, does not mean getting rid of XP.

You can have a proper dual boot with both system on its own partitions.

I don't use wubi, and I'm not sure if you can expand a wubi root disk. You can try googling it.

To see the used and free space from inside wubi, when you boot it don't rely on Gparted. Open terminal and execute:
df -h

That should show you the size and usage of the root partition as wubi sees it.

In any case, I would really consider a proper dual boot. Wubi is just for a quick try, and don't rely too much on it. Most things are more complicated compared to dedicated install, like expanding partitions for example.

How to expand it now when it's only a file in windows, like a virtual machine?

---

### Post by JKyleOKC on 2012-11-21
I believe there's information in the forums on increasing the size of root.disk but I don't remember just where. Search for "wubi" and "size" and it should turn up.

I ran a wubi install on the D: drive of an XP Pro system for quite a while but never needed to increase its size. Just before giving that box to my son's family, I blew away the wubi installation and all of the private files, repartitioned that second drive (which in my case actually was a second 50-GB drive) to free half its space, and installed Xubuntu 12.04.1 64-bit on it. That worked much better than did wubi, although I doubt that the new owners of the box will ever boot into it...

---

### Post by PaperProjects on 2012-11-21
Yes, that should be a better idea, to use custom partitions. Thanks for helping me; I think I'll try the hard way and redo the partitions. I don't think Ill ever use wubi again.

---

