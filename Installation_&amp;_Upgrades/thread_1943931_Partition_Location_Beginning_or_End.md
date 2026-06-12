---
title: "Partition Location: Beginning or End?"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2012-03-20
I'm currently triple booting Ubuntu 11.04, Windows 7, and Xubuntu 11.10 (the last one is my "play" partition, where I check out new OS's).  I'm using an  Ubuntu 12.04 Beta 1 bootable USB drive and trying to install it over my Xubuntu 11.10 partition (under the "Something Else" category on the installation program, of course).

For the new partition's location, I've always put "beginning" because that's what everyone says to do.  :biggrin: I'm just wondering what putting it at the "end" would do.  Does anyone know?  I don't want to try it myself; I've learned to ask other people before playing around with Linux. :shock:

---

### Post by darkod on 2012-03-20
First of all, if you are installing over your Xubuntu then you don't need to be creating any partitions. The Beginning/End question is related to creating a partition smaller than the unpartitioned space where you are creating it. So it is asking you whether to create it at the beginning or the end of your unpartitioned space.

But in your case you can simply select the Xubuntu root partition (make sure it's the correct one), then click the Change button below, and select the options you want to use, for example ext4 as filesystem, the mount point / (because it will be the root of your 12.04), tick the format box, and that's it.

That is how you use an existing partition, by selecting it and using the Change button.

---

### Post by GreenRaccoon on 2012-03-20
> **darkod said:**
> First of all, if you are installing over your Xubuntu then you don't need to be creating any partitions. The Beginning/End question is related to creating a partition smaller than the unpartitioned space where you are creating it. So it is asking you whether to create it at the beginning or the end of your unpartitioned space.

But in your case you can simply select the Xubuntu root partition (make sure it's the correct one), then click the Change button below, and select the options you want to use, for example ext4 as filesystem, the mount point / (because it will be the root of your 12.04), tick the format box, and that's it.

That is how you use an existing partition, by selecting it and using the Change button.

Thanks!  That's exactly what I wanted to know!

I didn't realize you could just Change the partition too.  I was going to delete the partition and then recreate it, but your way makes it a little easier.

---

