---
title: "Partition Ubuntu 16 on SSD alongside with HDD"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by 9dor on 2016-08-22
Currently the system has 8GB RAM.

I plan to partition as follows:

In SSD (128 GB):
    * '/' 117GB
    * '/boot' 1GB
    * unallocated: 10GB
In HDD (500 GB): 
    * '/home' (Size is whatever's left)
    * swap 10GB

Usage will be only office & internet.
But I will be installing many softwares.

I could use your advice whether my scheme is right.

---

### Post by yancek on 2016-08-22
Generally 15-25GB is satisfactory for a root filesystem partition so even if you install a lot of software, your 117GB should be more than enough.

Is the machine EFI capable?  If so and you choose an EFI install you will need a FAT32 EFI partition  at the beginning of the disk.  
Having a separate boot partition usually isn't necessary for a standard install, more of a choice but if you do that, 1GB should be good.  You need to keep an eye on kernel updates so you don't fill the boot partition.

---

### Post by sudodus on 2016-08-22
Your plan should work. But I have a few questions.

1. Why are you leaving 10 GB unallocated in the SSD? Is it for testing various linux distros? Or for swapping, if you find swapping to the HDD too slow, or something else?

2. If you intend to hibernate you need at least as much swap as RAM (in the same units, say Gibibytes), so 10 GB swap is suitable for 8 GiB RAM. Otherwise, it will probably be enough to have 1 GB swap. You will notice, when the computer starts swapping (it gets slow), and can turn off some tabs or programs to make it work within the RAM again.

3. How much is left for /home on the HDD (a round figure: {3, 10, 30, 100. 300} GB)?

4. Have you considered a separate ***data*** partition for your personal files (documents, music, multimedia files)? A data partition makes it easy to have a separate and simple backup method for your personal files.

---

### Post by 9dor on 2016-08-22
> **yancek said:**
> Generally 15-25GB is satisfactory for a root filesystem partition so even if you install a lot of software, your 117GB should be more than enough.

Is the machine EFI capable?  If so and you choose an EFI install you will need a FAT32 EFI partition  at the beginning of the disk.  
Having a separate boot partition usually isn't necessary for a standard install, more of a choice but if you do that, 1GB should be good.  You need to keep an eye on kernel updates so you don't fill the boot partition.
Yes I know, 120 GB is a lot. But that is the minimal capacity in today's SSDs.
Yes, the machine supports UEFI.
I can have the boot partition with 2GB because that I have lots of space..

> **sudodus said:**
> Your plan should work. But I have a few questions.

1. Why are you leaving 10 GB unallocated in the SSD? Is it for testing various linux distros? Or for swapping, if you find swapping to the HDD too slow, or something else?

2. If you intend to hibernate you need at least as much swap as RAM (in the same units, say Gibibytes), so 10 GB swap is suitable for 8 GiB RAM. Otherwise, it will probably be enough to have 1 GB swap. You will notice, when the computer starts swapping (it gets slow), and can turn off some tabs or programs to make it work within the RAM again.

3. How much is left for /home on the HDD (a round figure: {3, 10, 30, 100. 300} GB)?

4. Have you considered a separate ***data*** partition for your personal files (documents, music, multimedia files)? A data partition makes it easy to have a separate and simple backup method for your personal files.

_My answers:_
1. I read the it is recommended to leave 10% of unallocated space on the SSD, for a longer "life".

2. Indeed I intend to hibernate, therefore the 10 GB of swap.

3. Almost the entire disk :) that is 490 GB

4. data partition seems right. I suppose it will be alongside with '/home' ?

---

### Post by sudodus on 2016-08-22
> **9dor said:**
> Yes I know, 120 GB is a lot. But that is the minimal capacity in today's SSDs.
Yes, the machine supports UEFI.
I can have the boot partition with 2GB because that I have lots of space..



_My answers:_
1. I read the it is recommended to leave 10% of unallocated space on the SSD, for a longer "life".

2. Indeed I intend to hibernate, therefore the 10 GB of swap.

3. Almost the entire disk :) that is 490 GB

OK
> 
4. data partition seems right. I suppose it will be alongside with '/home' ?

Yes :-)

See also this link: [Oldfred's tips about a data partition](https://ubuntuforums.org/showthread.php?t=2334739&p=13534546#post13534546)

I suggest that you use much more drive space for **data** than for **home**.

---

### Post by 9dor on 2016-08-22
@sudodus:
Thanks! Now I feel comfortable with this scheme.
Also I will link the media directories to the HDD, [as written here]("http://askubuntu.com/questions/355190/media-content-on-seperate-hard-drive").

I was thinking to replace the 120 GB SSD with the following:
"Transcend SSD370 64GB"
which is smaller and cheaper.
Do you know whether it is reliable?

---

### Post by sudodus on 2016-08-23
I have some Transcend USB pendrives and SD cards, and they work well, but I have no Transcend SSD. So I don't know, but I *think* it should work well.

---

