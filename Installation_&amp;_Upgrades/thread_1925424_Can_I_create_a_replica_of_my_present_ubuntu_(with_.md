---
title: "Can I create a replica of my present ubuntu (with installed packages)?"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2012-02-14
Is it possible to create a replica of the entire ubuntu 10.04 operating system that I am using along with the extra installed packages and personal files etc. so that if my hard-disk crashes I can install the replica in another computer and get everything back?

---

### Post by Paddy Landau on 2012-02-14
Yes, you can.

Although I found doing this with Windows was very useful (every time my children installed viruses, I could just restore the hard drive), I have found it less useful for Ubuntu because it installs so fast -- unless, as you say, you wish to clone the entire system.

Look at [CloneZilla]("http://www.clonezilla.org/"). It is not the most user-friendly system in the world, but once you get your head around it, it is easy to use. You can back up individual partitions, or the entire drive (including the MBR). The best way is to create a Live CD (or USB) with CloneZilla, and an external hard drive on which to save the backup (CloneZilla saves each backup into a folder).

---

### Post by spcwingo on 2012-02-14
You can also check out Remastersys.  From it you can do a backup of your system to an ISO.  If trouble arises, just pop in the burned CD/DVD, install and you're right back in business.  :popcorn:

---

### Post by Rodney9 on 2012-02-14
Clone your full hard drive with Clonezilla or Redo Backup.

[http://redobackup.org/](http://redobackup.org/)
Redo Backup and Recovery is so simple that anyone can use it. It is the easiest, most complete disaster recovery solution available. It allows bare-metal restore. Bare metal restore means that even if your hard drive melts or gets completely erased by a virus, you can have a completely-functional system back up and running in as little as 10 minutes.


[http://www.clonezilla.org/](http://www.clonezilla.org/)

Clonezilla Tutorial showing you both how to backup and restore an operating system

[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Rodney

---

### Post by Paddy Landau on 2012-02-15
> **Rodney9 said:**
> [http://redobackup.org/](http://redobackup.org/)
Thanks for the recommendation of Redo Backup -- it looks fantastic (and it's based on Ubuntu!). I am busy downloading it to test it.

---

### Post by darkod on 2012-02-15
One question about redobackup. Can it restore on a smaller partition than the source (as long as it is bigger than the data), or the same as clonezilla, it needs a partition of the same or bigger size to restore?

---

### Post by Paddy Landau on 2012-02-15
> **darkod said:**
> One question about redobackup. Can it restore on a smaller partition than the source (as long as it is bigger than the data), or the same as clonezilla, it needs a partition of the same or bigger size to restore?
According to the documentation, no. The same applies to CloneZilla.

You can try, but I would not be hopeful. Even though the data size is smaller than the partition, it is not stored contiguously at the start of the partition, but rather parts of the data could be at the end of the partition.

---

### Post by darkod on 2012-02-15
In that case FSArchiver remains a favorite for backup (not that I know many programs). It only cares about the actual amount of data and can restore to any partition as long as it is big enough.
It doesn't have a boot version but the program is included on the System Rescue CD which is a boot cd with many useful programs.

---

### Post by ottosykora on 2012-02-15
I made the experience, that with some of such tools I have been using in tha past, windows partitions could be often well copied to partition which was  no exactly the same size, let say somehow smaller.

Those tools I used, mostly refused to work properly with linux paritions, ext2 and ext3, probably because of the reason that data was there rather scattered and could not be properly moved to one corner.
So acronis simply refused to restore the partition for example.

---

### Post by Paddy Landau on 2012-02-15
> **darkod said:**
> In that case FSArchiver remains a favorite for backup...
It looks like an OK program if you're happy to live with the limitations.

---

