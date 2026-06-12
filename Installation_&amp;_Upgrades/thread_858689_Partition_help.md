---
title: "Partition help????"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by neilevan814 on 2008-07-13
Here attached is a screenshot of gparted:  As you can tell I didn't know what i was doing when I did this....I would like to be able to use all of my harddrive space effectively and I know I cannot with it set like this.  can someone help me debunk this mess??? I would so greatly appreciate some assistance.

Also I have included the filesystem set up as ubuntu sees it.  I have 2 media/disk partitions which I am not sure which partitions they match up to in gparted and all they contain is an empty  lost&Found folder.  

When I installed this I set my swap partiton to the 2gb partition /dev/sda6
but Ubuntu install wouldn't accept it so i followed their option to repartiton in guided mode.  I set dev/sda3 to mount at /boot but during install I believe boot got planted in windows mbr.  

I am overwhelmed with this messiness..so I'll stop and see if someone can help me dig out

Thanks, Neil

---

### Post by VMC on 2008-07-13
I'm assuming Windows is in there in the mix as well, what with the NTFS partitions.
How do you want to to look like, and why were you using gparted and not let ubuntu install it for you. Or was this an after thought?

At any rate type this from a Terminal (Applications > Accessories > Terminal"):

```
sudo fdisk -l
```

Tell us a little bit on how you want this to end - Dual boot with Windows.

---

### Post by Victormd on 2008-07-13
How many linux distros do you have installed?
First of all, you'll need to organize the files on your partitions. Organize it so you have all the files on "/" and most likely, your "media/disk" partition.

Once you've done that, delete all the other partitions and use gparted to resize your main partitions. Note that to resize your partitions, you'll need to boot from the Live CD or the Gparted Live CD because you can't use Gparted to resize a partition that's mounted.

Also, you should only need 1 swap partition so pick one and delete the other (you will need to update your fstab file)

---

