---
title: "Partition Overwrite Question"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by ahmedh on 2008-03-22
I have an HP desktop. It originally came with a single partitioned hard drive. The first partition is 7gb and has the Windows XP files and registries and all that, along with some program files. The larger, 170 gb partition has all my documents (music, movies, office files) along with some program files that wouldn't fit on the smaller drive. I have tried Xubuntu on an old laptop and I am posting this from the Ubuntu LiveCD on the computer in question. I have decided that I want Ubuntu, and I am ready to give up XP totally. 

My question is this: If I install Ubuntu permanently to the small XP partition, totally erasing it (both partitions are almost completely full), will I be able to access (and modify) all my old documents on the larger partition? Will I be able to create and save new files (I've heard of a read-only issue with partitioned drives)? Currently it says "unable to mount" when I try to open my partitions with the file manager. 

Thanks in advance.

---

### Post by banewman on 2008-03-22
Yes you will be able to access and modify those files - if you have any issues there are plenty of threads about that sort of thing.

---

### Post by mikewhatever on 2008-03-22
It's advisable to check that large partition for errors before you delete XP.

---

### Post by ahmedh on 2008-03-22
Fantastic, thanks guys. How do you check for errors?

---

### Post by mikewhatever on 2008-03-23
> **ahmedh said:**
> Fantastic, thanks guys. How do you check for errors?

Here, just googled it for you.
[http://www.pctalknet.com/winxp/errorCheck.php](http://www.pctalknet.com/winxp/errorCheck.php)
[http://pcworld.about.com/magazine/2109p160id111653.htm](http://pcworld.about.com/magazine/2109p160id111653.htm)

---

### Post by housam on 2008-03-23
> **ahmedh said:**
> 
My question is this: If I install Ubuntu permanently to the small XP partition, totally erasing it (both partitions are almost completely full), will I be able to access (and modify) all my old documents on the larger partition? Will I be able to create and save new files (I've heard of a read-only issue with partitioned drives)? Currently it says "unable to mount" when I try to open my partitions with the file manager. 


First of all you have to devide your 7.5 GB partition into two partitions ( 1 GB swap and the rest as root ( / )for ubuntu ).
after installation - in case of not automatically mounted - you have to mount the data partitions as it is a ntfs format using this guide :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/mountwindows_[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows")

---

