---
title: "What is the best partitioning for Linux/MS desktop"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by bigbird on 2008-06-20
What number of partitions  do I need for best set-up moving files between Linux/MS OS's

I'm Guessing
2 primary with 3 logical each.

First Primary with C D and E (NTSF + FAT)

My main question is
1 logical and 3 EXT3 partitions.?

What are my best options for 250gig single drive so I easily back up my Data files only not OS's onto USB external drive.
What size should my EXT3 partitions be for HH.

---

### Post by logos34 on 2008-06-20
> **bigbird said:**
> I'm Guessing
2 primary with 3 logical each.

Logical partitions are contained within an extended partition, a special type of primary partition that allows one to skirt the 4 partition hard disk limit.  There can only be one extended partition per disk.  

[This howto ]("http://tldp.org/HOWTO/Partition/partition-types.html")explains linux partitions in detail.

Forget fat32--linux can access ntfs read+write. Hardy comes with ntfs-3g driver out of the box.  

The best plan I think is to make a /, /swap AND separate /home (put em all on logical partitions if you have to).  Make / ~6-8 GB, and rest to /home.  Then backup home to the usb.

---

### Post by bigbird on 2008-06-21
so I will need 2 NTSF partitions and 3 EXT3 partitions.
Yore saying that I can access my NTSF files but how do I access my Linux files from BGwindows, Is there a way to read/write to EXT3 from windows or what is the best go between format that s the only reason for a FAT.
Thank you for your time. Chauvin.

---

### Post by logos34 on 2008-06-21
> **bigbird said:**
> so I will need 2 NTSF partitions and 3 EXT3 partitions.
Yore saying that I can access my NTSF files but how do I access my Linux files from BGwindows,

You need [fs-driver]("http://www.fs-driver.org/").

---

### Post by bigbird on 2008-06-21
How do you feel about running Windows inside of Linux or running Linux inside of Windows possibly this will let me use built in Flash memory readers I cant find drivers for.
A better idea is most welcome,,, I have a huge drive so I am wanting to play around a bit possibly see what works best.
I realy need  both running flawlessly on a single desktop.
Can I run a 64 bit HH version on Win XP?
Thank you for all help and advise. Chauvin.:)

---

### Post by Habbit on 2008-06-21
> **logos34 said:**
> You need [fs-driver]("http://www.fs-driver.org/").
I personally prefer [ext2FSD]("http://ext2fsd.sourceforge.net/"), since it has already implemented some ext3 functionality (i.e. it will replay the journal on a dirty ext3 volume) _and_ it has sources available.

---

### Post by logos34 on 2008-06-21
> **Habbit said:**
> I personally prefer [ext2FSD]("http://ext2fsd.sourceforge.net/"), since it has already implemented some ext3 functionality (i.e. it will replay the journal on a dirty ext3 volume) _and_ it has sources available.

I see the changelog, but where is the documentation for this driver?

---

### Post by Habbit on 2008-06-21
> **logos34 said:**
> I see the changelog, but where is the documentation for this driver?
Docuwhat? xD
Nah, just joking. AFAIK, the binary zip comes with some .TXT files :lolflag:

---

