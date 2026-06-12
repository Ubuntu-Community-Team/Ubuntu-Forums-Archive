---
title: "Alternative Installation CD? / Partitioning Error"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Wangsta on 2010-06-08
So I'm trying LUbuntu on my really old laptop, (around 256 MB ram) and it's really not working. It literally takes hours and hours to get ANYWHERE it's going so slow. I would love a text-only installation CD, but I can't find any online. 

Does anyone know where I could get a alternative installation CD?

also, when I try to partition it, I keep getting errors. It keeps on saying one of them is in use. Right now, I have two partitions, an old Xubuntu and a swap, which i need to make bigger. 

Does that mean it's using the swap during the installation? It's not letting me completely format the hard drive or anything and it won't complete now...

Please help, bitte!

---

### Post by Wangsta on 2010-06-09
It says something about sending modifications to the kernel and that the partitions are in use and can't be changed until after reboot, if that helps.

(EDIT: it also says something about ubi-setting-somethign error 141)

---

### Post by Mark Phelps on 2010-06-09
If you're trying to change the partitioning from inside Ubuntu, you can't do that because the partitions are mounted.

You would do better downloading and burning a GParted LiveCD -- which you can get from distrowatch.com.

Then, boot from that and use it to do the partitioning.  It doesn't mount any partitions by default.

---

### Post by snowpine on 2010-06-09
Open a terminal (Applications, Accessories, Terminal) and:

```
sudo swapoff -a
```

This should turn off your swap so you can resize the partition.

ps It is normal for the system to be very slow while running from the Live CD. You should see better performance once you have installed to the hard drive.

---

