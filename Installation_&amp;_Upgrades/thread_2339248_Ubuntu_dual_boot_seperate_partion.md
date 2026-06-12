---
title: "Ubuntu dual boot seperate partion"
date: 2016-10-06
forum: Installation &amp; Upgrades
---

### Post by khamadagy on 2016-10-06
Dear,

I would like to instal Ubuntu 16.04.1 on my Hp envy dv6 notebook, with a flash drive. And i would like to do this alongside windows on a seperate partion.
te installer works but i dont know how to get it on a seperate partion with a swap partion. 

I also searched for the swap partions, and saw it has to be 2 X ram, but what does that mean?. if i run Dxdiag it reads    Memory: 6144MB RAMAvailable OS Memory: 5596MB RAM. I dont know wich number i can use for the swap partion.

I already made some space to be partioned in ubuntu installer, by setting it allocated.

So how do i preform a seperate partion instal?, do in need to make a home, boot, temp and var partitons?
And how big has the swap partition to be?

Sincerely Aaron

---

### Post by yancek on 2016-10-06
You would first need to let us know which version of windows you are using as later versions (8 and 10) us UEFI to boot so you would then need to install Ubuntu using UEFI.  An explanation is at the Ubuntu site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Generally a windows install will take up the entire disk so if you want another operating system such as Ubuntu, you would first have to create unallocated space which you can do in Disk Management from windows.  Read the link above and you will probably be better off using the manual installation option, named Something Else in Ubuntu.

---

### Post by Impavidus on 2016-10-06
Making the swap 2 times ram is old advice. If you really want to hibernate your system (what most people don't do), you have to make your swap a bit larger than your ram. Pay attention to the difference between [MB]("https://en.wikipedia.org/wiki/Megabyte") and [MiB]("https://en.wikipedia.org/wiki/Mebibyte"). The reported size of your ram is labelled in MB, but probably MiB are meant. If you don't intend to use hibernation, making the swap about 2 GB, maybe 3 GB should be enough.

Separate partitions for /var, /tmp or /boot are only necessary in special cases. A separate partition for /home can be useful if allocating more than about 30 GB to Ubuntu.

---

