---
title: "Installing Ubuntu 10.04 on an external hard disk."
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by comp_007 on 2010-05-03
Hi all,

Sorry if this topic has been asked before.

But I would like to know how to install ubuntu on external HDD.?

I have created a separate partition on my external HDD(40GB) and I want to install ubuntu inside that.

I don't want to install GRUB as external HDD is not connected to computer all the time and without it I won't be able to use windows(Windows 7 ultimate 32 bit).

Please guide me :)

---

### Post by oldfred on 2010-05-03
When you install you want to install grub to the external drive and set in BIOS to boot from the external first. If  external is plugged in, it will boot grub and give you a choice to boot anything. If not plugged in your internal has not changed and will boot windows.

You have to use the advanced button on screen #8 where it says ready to install to select which drive to install grub to. Choose external drive.

If you have created partitions for / (root), swap and possibly /home you can do manual install.

---

### Post by efflandt on 2010-05-03
As mentioned you want to manually select the partition(s) you set up for it, and should install grub2 to the mbr of the external drive (not default to your internal drive).  So in the **summary** screen after you select your user and anything to migrate from an existing system, watch carefully for that **Advanced** button before actual installation proceeds.

However, I am having an issue with an external hd with 10.04 LTS installed.  It boots fine on 2 laptops, but fails to boot on my desktop, even though 9.10 on another external drive can boot fine on any of those computers.  10.04 LTS CD works fine live on the PC that cannot boot that from the USB hd.  So I am still trying to figure that out.

---

### Post by comp_007 on 2010-05-04
Thanks for the replies.

Will try it after sometime and tell about further doubts.

---

### Post by comp_007 on 2010-05-04
While installing ubuntu when I go to advanced tab there is an option whether i need to install grub boot loader or not.


[IMG]http://members.iinet.net.au/~herman546/p24/022g.png[/IMG]

[B][U]
[COLOR="Red"]Will I be able to boot into ubuntu if don't install GRUB ?[/COLOR][/U][/B]

---

### Post by oldfred on 2010-05-04
You need a boot loader. Not unless you have another boot loader. Windows boot loaders only boot windows. A few try third party boot loaders.

Just install grub to sdb or what ever the external is defined as.

---

### Post by comp_007 on 2010-05-05
So I cannot boot ubuntu without GRUB.

Hey I need some help with step 4

[IMG]http://members.iinet.net.au/~herman546/p24/012_40f7_24-a.png[/IMG]

Should I use install them side by side option.
or specify partitions manually options ?

---

### Post by oldfred on 2010-05-05
I thought you already created some partitions, then you do manual install so you can select them. You have to select / (root) and should have swap, and many suggest a separate /home. 

Any of the automatic schemes will only give you root & swap and automatically adjust the size of other partitions to make room.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Shows some info on manual partitions:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by comp_007 on 2010-05-07
Hey ,

Thanks for help oldfred..

Installed ubuntu successfully ! :)

---

### Post by oldfred on 2010-05-07
Glad you got it working. Happy Ubuntuing (is that a word?).;)

---

### Post by Pikachuu on 2010-12-03
I used the "Erase and use the whole disk" option for my external HDD. GRUB takes forever to load (well around 5 minutes), and once I get to GRUB choosing the option to boot normally from the external hard drive causes the screen to stall at GRUB indefinitely.

Am I doing something wrong?

---

