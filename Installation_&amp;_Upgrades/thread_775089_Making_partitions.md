---
title: "Making partitions"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by eperrone on 2008-04-29
Hello all,

New to linux so I was going to try and install dual boot with Windows on my laptop. I started to go through the install process and when I tried to make partitions using the installer it never completed.  Reading the instructions on the web site I was sucessful in creating a new partition using the rescue cd and gparted.  

So now I am wondering which install option do I need to use to install into the new empty partition.

I set aside 30GB and was going to use the manual method to create the partition and so I wondered what settings I need to make.  Any recommendations would be appreciated.  Which file system sizes etc?

Thanks all!!!

Eric

---

### Post by CAsurfer on 2008-04-29
You will need to create at least 2 partitions for Ubuntu. The first is the main partition which contains your system files, the other is the "swap" partition, which is used as "swap space" - basically just a means of extending your system memory (RAM) to disk.

A rule of thumb: your swap partition should be about as big as the size of your RAM. So if you have 2 GBs of ram, set aside a 2 GB swap partition. The rest of your available space will go to the main partition.

The swap partition should be formatted "swap". The standard thing is to format the main partition as "ext3".

At some point, the installer will ask you to set mountpoints. You want your main partition to be mounted as root ("/"). I think the installer is smart enough to use your swap partition as swap.

---

### Post by zvacet on 2008-04-30
[Here]("http://psychocats.s465.sureserver.com/ubuntu/installing") is good guide.

---

### Post by eperrone on 2008-04-30
Thank you guys I hope to be logging in from ubuntu next to tell you how it went!!!

---

