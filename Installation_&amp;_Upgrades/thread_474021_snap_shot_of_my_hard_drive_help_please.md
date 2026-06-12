---
title: "snap shot of my hard drive help please"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-14
[http://ubuntuforums.org/showthread.php?t=474001](http://ubuntuforums.org/showthread.php?t=474001)

---

### Post by Ek0nomik on 2007-06-14
What do you want help with?  What are you *trying* to do?

Can you handle reformatting the whole hard drive?

You can change anything you want by using the Live CD, or by running this command:

```
gksudo gparted
```

You can change any partitions you want.  Or don't you understand what partitions you need?

---

### Post by swoll1980 on 2007-06-14
when i try to use gparted it tells me i have to to it manualy i want to use my entire hard drive for ubutu, i tried to use the guided use entire hard drive option during install but it told me ext3 was busy. i no nothing about cpu just want to be able to use entire hard drive right now i can only use half

---

### Post by Ek0nomik on 2007-06-14
During the installation process I would do the "Manual" option.

You could create an EXT3 drive, and a Swap drive.

First, calculate how much Swap you will want.  (Usually 2x or 1.5x the amount of RAM you have)  But don't create the partition yet, just make note of it.

Now, create your first partition as EXT3.  Make it X-Swap ("X Minus Swap").  (Where X is your total hard drive space).

Finally, create your Swap partition.

As an example, if I had 1GB of RAM and a 300GB hard drive, I would first create a 298GB EXT3 partition, and then a 2GB Swap partition.

That's all you need for Ubuntu!

---

### Post by swoll1980 on 2007-06-14
thank you

---

### Post by Ek0nomik on 2007-06-14
> **swoll1980 said:**
> thank you

Did you get it working properly?

After you boot into Ubuntu you can check your partitions by typing:

```
df -h
```

and

```
fdisk -l
```

---

