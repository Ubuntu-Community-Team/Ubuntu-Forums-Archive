---
title: "Problem updating grub settings automatically"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by ddtrust on 2006-11-14
Hi! 

I have bit of a problem with my ubuntu installation. When I first installed ubuntu, I didn't create separate /home-partition. After a while I decided to give ubuntu more disk space and I deleted one of my old NTFS-partitions, created new ext3-partition and moved my /home-partition there. However, as I changed my partition table, the partition numbers of my / and swap -paratitions changed from sda7(hd0,6) and sda8(hd0,7) to sda6(hd0,5) and sda7(hd0,6). So I manually changed the partition numbers from menu.lst accordingly. 

Then we get to my problem: When I do automatic kernel updates, or remove old kernel images with apt-get, it automatically modifies my menu.lst file, but the partition numbers go always as they used to be before separate /home-partition. So I always have to change them to correct values manually. How can I tell to apt-get to write the correct partition numbers to menu.lst?

- jk

---

### Post by Herman on 2006-11-15
I would edit the 'kopt' line in the Debian automagic kernels list section of my /boot/grub/menu.lst,  I think that's what you are wanting to know, for more details, click the following link, 
 kopt= (kernel options)........................................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")

If you are using 'Edgy', you might see the new 'UUID' filesystem code there in your menu.lst kopt lines too, it resembles an md5sum. Here's a link to help explain a little about that in case you need to know more about that.
About Edgy Eft's new /etc/fstab files with UUID filesystem ID added....................................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

Regards, Herman :D

---

### Post by ddtrust on 2006-11-15
> **Herman said:**
> I would edit the 'kopt' line in the Debian automagic kernels list section of my /boot/grub/menu.lst,  I think that's what you are wanting to know, for more details, click the following link, 
 kopt= (kernel options)........................................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")

If you are using 'Edgy', you might see the new 'UUID' filesystem code there in your menu.lst kopt lines too, it resembles an md5sum. Here's a link to help explain a little about that in case you need to know more about that.
About Edgy Eft's new /etc/fstab files with UUID filesystem ID added....................................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

Regards, Herman :D

Thanks for this. Helped me a lot!

---

### Post by Herman on 2006-11-16
Good to hear it, you're welcome! :D 
Regards, Herman.

---

