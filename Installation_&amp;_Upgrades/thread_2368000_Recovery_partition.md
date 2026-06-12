---
title: "Recovery partition"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by donmatas on 2017-08-05
Hello everyone,

I am installing xubuntu 16.04.3 in a laptop with Windows 10. I want to delete win$, but keeping the recovery partition. Does anyone know if is enough to leave the recovery partition to make it work or I have to keep other partitions?

[ATTACH=CONFIG]276264[/ATTACH]

---

### Post by TheFu on 2017-08-05
It is **always** best to make a full backup before doing any partition related work.  

I've never touched or seen Win10, so cannot answer that part of the question.

---

### Post by Mark Phelps on 2017-08-06
If it's an OEM PC, that is, if it came with Win10 preinstalled, then most likely the OEM has some other recovery code in one of the partitions on the drive that is needed to launch the recovery process.

If what you want is a way to restore Windows to its original state, then your best solution is to use a third-party utility in Windows:

Macrium Reflect (MR) provides a FREE version that can be used to image and restore partitions or entire drives: [http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)
 
What I recommend is the following:
1) Download and install Macrium Reflect (MR)
2) Run MR and choose the option: "Create an image of the partition(s) required to backup and restore Windows" to write a full backup to an external drive or USB stick
3) Use the option to create a boot USB stick or CD
 
My experience is that MR, when using the High Compression option, typically can compress the saved image file to about 50% of the USED space in the OS partition.  This means if you have an 80GB OS partition, and 40GB is used, MR only needs about 20GB to store the image file.
 
I use this all the time and it typically takes less than 15 minutes to do the image backup and about the same time or less to do a restore.

Once you have the MR backup, you no longer need the Recovery partition and can remove it to reuse that space.

---

