---
title: "Converting from Dual boot to solely Ubuntu"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by davem2312 on 2007-05-02
Hello,

I currently have an 80 gig HD, dual booting XP and Ubuntu 7.0.4.  I am considering going to solely Ubuntu, considering that I do not use XP at all anymore.  Here is a list of my complicated HD partitions.

/dev/sda1    ext2       39.19 MB       (I'm not sure what this is)
/dev/sda2    ntfs        33.42 GB       (windows)
/dev/sda3    ext3       35.08 GB       (mounted as /)
/dev/sda4    extended
    /dev/sda8     fat32            1.78 GB      (This is where my mail is, available to both sides)
    /dev/sda5     linux-swap   1.87 GB
    /dev/sda6     ntfs              1.87 GB       (Windows swap?)
    /dev/sda7     fat32             486.31 MB     (This is just random shared files XP - Linux)


So what partitions do I need to keep other than sda3 and sda6 after I move stuff I want to keep.  Also, what is the best way to do this.  I have the GParted Boot CD, so I can do everything from the CD.

Thanks for the advice.

--Dave

---

### Post by zvacet on 2007-05-03
What you need to keep is sda3 and sda5(your swap).If you don´t want windows anymore you can delete all other partitions,but maybe you have some data you want to keep.I don´t think you need 35GB for root partition.My is 10 and it is not half full.But mybe you will install more programs then I do.Anyway 35 is too much.Shrink it to15 or 20 if you want to.What you realy need is separate home partition.That one can be large.For how to make it see 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by ssican on 2007-05-03
For to keep Windows XP and to make Ubuntu boot automatically see "Changing the default operating system to Boot" in this link [http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html](http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html)

---

