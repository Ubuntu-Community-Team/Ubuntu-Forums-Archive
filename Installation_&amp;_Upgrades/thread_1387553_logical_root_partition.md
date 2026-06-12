---
title: "logical root partition"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by bcn17 on 2010-01-22
I was wondering if I could make logical / partitions if I have a primary /boot partition. Is this a potential way to get around having only 4 bootable operating systems on a single HD?

---

### Post by kansasnoob on 2010-01-22
> **bcn17 said:**
> I was wondering if I could make logical / partitions if I have a primary /boot partition. Is this a potential way to get around having only 4 bootable operating systems on a single HD?

I've personally found having a separate /boot partition often creates more problems than it might solve. You can read a bit about that here:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

So, unless you fall into the old BIOS category there really is no need.

As far as using extended partitions to create many logical partitions here's mine:

[ATTACH]144461[/ATTACH]

They're labeled so you can see what I have. The only real reason I created a second primary for one of my *buntu's was because I plan on dumping the Win partition soon and grub is generally happier if a disc begins with a primary partition.

You'll also notice that all 5 *buntu's have their own separate /home but all share one SWAP.

---

### Post by Sef on 2010-01-22
> I was wondering if I could make logical / partitions if I have a primary /boot partition. Is this a potential way to get around having only 4 bootable operating systems on a single HD?

Just make 3 primary partitions and have the 4th one a logical partition.  Then you can have as many as you want.   Just let Ubuntu put GRUB where you want it.

---

### Post by bcn17 on 2010-01-25
Thanks guys. I think I might go ahead and put grub on a usb drive. I just want an easy way to install new operating systems (windows and linux) and quickly have grub be able to detect all operating systems. I suppose if I install grub to a usb drive. Then lets say install windows on a harddisk by booting to that HD, then restart - boot to my grub usb drive. Run grub update and it should find them all and I should be able to boot into all OS's again?

---

