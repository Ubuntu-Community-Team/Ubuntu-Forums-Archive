---
title: "Partitioning help and some questions"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by DarthDie on 2007-05-22
Hello all,
          I am trying to install Ubuntu (Fiesty Fawn) on this desktop and am having some problems with partitioning...Ubuntu partitoner just sits there at 0%...i left it there for 10+ minutes and it was still at 0%, am i just being impatient?So then i tried GParted which gives me the error "Extended record needed (xxxx > 1024) not yet supported"  so i dont know what todo. I think livecd has ntfs partitioning?(Oh yes, i am trying to shrink my windows partition)Or try livecd with ntfstools? And i have a couple other questions...
1.  A friend said to update,reset,and reconfig BIOS before installing ubuntu...why the heck would i want todo this??First its updated...second i havent messed with my BIOS.
2. That same friend said to install GRUB not to MBR (because it would mess up windows if i uninstalled ubuntu) and to install it to /dev/hda[numberhere]...should I?
3. That same friend said to have a seperate /home...what are the cons and pros of this?

Thanks in advance ;),
DarthDie

---

### Post by DarthDie on 2007-06-01
Sorry if bumping is not allowed....but can anybody help me? I have tried posting in GParted forums...but nobody that can help goes there.

---

### Post by Wim Sturkenboom on 2007-06-01
Not sure about the resizing, but
- make sure that you first run defrag in windows so all files are nicely in the beginning.

With regards to the other questions:

1)
Install grub in the MBR. If you ever remove Linux, GRUB will indeed bail out and you can not boot windows. However, if you boot from the windows CD, you can run the command **fixmbr** or **fdisk / fixmbr** to recover. Thereafter you can boot windows the normal way.

2)
The disadvantage of a separate home partition is that you must divide your space. Guaranteed that one of your partitions will get full and the other one still have plenty pf space left.
The advantage is that if you ever have to reinstall Ubuntu, that data on the home partition will not be lost.
The above is not specific for Linux or Ubuntu but also applies to partitioning for windows

---

### Post by DarthDie on 2007-06-01
Ok thanks, can anybody help with resizing?

---

### Post by palintheus on 2007-06-07
I would recommend the following:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by darren1270 on 2007-06-07
> **Wim Sturkenboom said:**
> Not sure about the resizing, but
- make sure that you first run defrag in windows so all files are nicely in the beginning

I suggest you defrag more that once...!  But it's only my 2 cents worth....

Good Luck
Darren

---

