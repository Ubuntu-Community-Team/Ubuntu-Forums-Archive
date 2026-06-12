---
title: "Xubuntu 7.04 on decTOP"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by jgidi on 2007-09-20
Hello,

I wrote up a HOWTO on installing Xubuntu 7.04 to the [decTOP mini-PC]("http://www.dataevolution.com/dectop%20info%202.htm") and figured it might be useful to some forum members.

I'm not posting the whole thing due to its length, but you can read it [here]("http://www.entropicblur.com/dectop/guide.html"). I hope it's helpful.

---

### Post by Qwertinsky on 2007-09-22
Thank you, a group from the local LUG and I are going to be ordering decTOP's today.

BTW: The summer special is still running, order 3 you get one free. 

If you can get three other people then it's only $88 each including shipping!

---

### Post by /etc/init.d/ on 2007-09-25
I've got one.  I found that the bootable flash drive I was using needed to be formatted with FAT16 rather than FAT32, though in /etc/mtab Linux will show both as the vague "vfat".

It's a nice device though.  Since it doesn't have any fans the HDD gets a little hot (mine fluctuates between 44 and 47 deg. C.), but it was good to see that the HDD had not been used before I got it (I was expecting some refurb.)  I've kept the 10GB drive since it's more than enough for my needs and I'm more comfortable with lower density drives reliability-wise.

If you want to know the temperature of yours (the HDD), install the smartmontools package and run

```
smartctl -a /dev/hda
```

It will be listed somewhere in the SMART parameters.  Since it's a Seagate drive, don't be alarmed if you see a high read/sense error rate.

---

### Post by jgidi on 2007-11-06
I updated my guide to cover the new 7.10 release. It's available at the same address:

[http://entropicblur.com/dectop/guide.html](http://entropicblur.com/dectop/guide.html)

---

### Post by Qwertinsky on 2007-11-10
I have Ubuntu 6.06 running on my decTOP and would like to use  your method to upgrade.

But I can not get Ubuntu to mount my flash drive and gives me the error:

Unable to  mount the selected volume. The volume is probably in a format that cannot be mounted.

I know it is good as I can read it in Windows and the decTOP will boot from it as it is the one I used to install 6.06.

I have reformatted the flash in fat16 and fat32 but it still wont mount it.

---

