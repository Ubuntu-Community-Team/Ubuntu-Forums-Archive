---
title: "Wiping Ubuntu partition"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by davidreid on 2013-02-03
Hi,

I currently have 12.10 installed but I am getting an issue where the screen will turn black with an error message and then take me back to the login screen. This can happen at any point so I lose everything that I was doing which is a nightmare, so I am thinking about reverting back to 12.04 as it is the stable release.

My question is, is it safe to just wipe the Ubuntu partition and install cleanly over the top of it? I am dual booting next to Windows 8 and I have 4 partitions:

Ubuntu
Windows
Swap
Empty HDD space

Would it be okay for me to just boot into Ubuntu using a live CD, wipe the data off of that partition and then install Ubuntu 12.04 back over the top or is this going to cause issues?

Thanks for any help

Dave

---

### Post by Bucky Ball on 2013-02-03
> **davidreid said:**
> Hi,

... is it safe to just wipe the Ubuntu partition and install cleanly over the top of it?

Would it be okay for me to just boot into Ubuntu using a live CD, wipe the data off of that partition and then install Ubuntu 12.04 back over the top or is this ... ?



Welcome to the forums.

Yes and yes. I always choose 'Something Else' when I get to the partitioning section of the install so I can manually partition. You can kill the partition completely from the LiveCD (or during the install when you choose 'Something Else') rather than wiping the info on it, which will leave free space where the partition was. Just create the new partition using the free space. You can also do as you suggest but easier to just kill the lot. 

You may need to run:

```
sudo update-grub

```
... to pick up the Windows install after installation but probably not. Should be found during install.

One thing I will add; in most situations four primary partitions is the maximum. Therefore that 'Empty HDD space' you mention only has the option of becoming one primary partition. But, if it is free space then make an extended partition (possibly during install) with all of the free space there which will allow you to put, theoretically, as many logical drives in there as your machine can handle. Can be handy.

Extended partitions are basically containers for holding logical partitions. They are not partitions that hold data themselves, if you know what I mean. The data they contain is contained in the logical partitions they hold.

Hope that helps.

---

### Post by ibjsb4 on 2013-02-03
I do not use the live CD, but isn't there a option to install on top of the existing install?

---

### Post by davidreid on 2013-02-03
Thanks very much for the help!

Dave

---

