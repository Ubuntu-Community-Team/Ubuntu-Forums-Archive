---
title: "I'm slow and I dress funny"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by Zarkops on 2008-02-28
I've got an IBM T41p and I downloaded the Ubuntu ISO and burned it to a CD.  No prob.

Stick the CD in and boot.  Click Install and everything looks cool.  Ubuntu comes up, I connect to my wireless router and I'm happy.

I take the CD out and reboot, windows starts.

PLEASE understand, this is my FIRST try with Linux altogether.

How come I don't get an option to FDisk/format the hd for the new OS?
How can I do this?
Is there an easier way to install that automatically takes up the entire hd?

Z

---

### Post by oldos2er on 2008-02-28
Boot the Ubuntu CD, and when the desktop is up, double-click the Install icon. When the partitioner starts, choose 'Guided--Use entire disk.'

---

### Post by Tim0miT on 2008-02-28
aww bless, just do as above said. just follow the install instructions and all will be good

format your wanted HD to ext3 and create a swap partition, install any away you go:guitar:

---

### Post by zvacet on 2008-02-28
You didn´t install it in first place.you are just runing live Cd.my advice will be to make separate home partition,because sooner or later you will see that is good thing to  have and you will post here how to do it(which is not a problem),and you will do same job twice.Select maual way and make partitions

1. root =10GB                                           mountpoint /
2. home= rest of free space exept            mountpoint /home
3.swap =2xram

You have exelent giude [here.](http://www.psychocats.net/ubuntu/installing)

---

