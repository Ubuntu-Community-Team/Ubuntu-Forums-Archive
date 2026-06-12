---
title: "installation of ubuntu10.04"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by alexdb2012 on 2012-05-15
Hi,

How to install Ubuntu (10.04) to my PC, already iam using windows xp.Without deleting xp i want to install.Especially i have lot of confusion at partitions.

Please explain step by step procedure with images. (By using CD only now I am going to install).

Another one: How to install ubuntu using USB?

---

### Post by Deepak J on 2012-05-15
Can you please specify your hard disk size and RAM

Also do check the website..


[https://help.ubuntu.com/10.04/installation-guide/](https://help.ubuntu.com/10.04/installation-guide/)

---

### Post by Doug11 on 2012-05-15
It should very simple. When you start the install cd, just read each options carefully, when you come to the partitions, there should be an option to install it along side your XP. Choose that and you should be good to go.
> **alexdb2012 said:**
> Hi,

How to install Ubuntu (10.04) to my PC, already iam using windows xp.Without deleting xp i want to install.Especially i have lot of confusion at partitions.

Please explain step by step procedure with images. (By using CD only now I am going to install).

Another one: How to install ubuntu using USB?

---

### Post by mörgæs on 2012-05-15
Why did you you pick 10.04 and not 12.04?

There are some good guides here:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by alexdb2012 on 2012-05-23
Hi,

My hard disk is 200GB and RAM is 2GB.

---

### Post by Deepak J on 2012-05-29
So free some space in your hard disk for installing ubuntu.
If you want to resize existing partitions then use GParted in Ubuntu by opting to try Ubuntu when booting from the CD.

Even I've got Windows XP and also Windows 7 besides my ubuntu, and its a 250GB HDD and 2 GB RAM.

So what I've done is first I freed about >14 GB of space and created a swap partition of 2048 MB(for 2 GB RAM) and then allocated the rest 12 GB for the root of Ubuntu.

What you've gotta do is while installing select manual partition and then allocate 2048 MB for the swap filesystem(it can be created by selecting the unallocated space in the HDD while installing Ubuntu and then specifying the size - 2048MB and filesystem - swap).

Then allocate the rest to a single partition with filesystem ext4 and mount point '/'.

About primary and logical partitions, if you're not sure about those then select both the swap and the other partition as logical.

And about the USB installation I don't know much of it. Also try to install the lastest 12.04 Ubuntu instead of 10.04 as it comes with the latest updates and programs.

More reference can be found at:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/10.04/installation-guide/](https://help.ubuntu.com/10.04/installation-guide/)

Hope you get your prblm solved by this.
:KS

---

