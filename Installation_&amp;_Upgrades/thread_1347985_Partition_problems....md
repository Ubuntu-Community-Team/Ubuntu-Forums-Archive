---
title: "Partition problems..."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by warriorofchaos20 on 2009-12-06
hey guys so i have been running solely Ubuntu 9.1 since it came out now and i decided i wanted to try out Windows 7 out (mostly for my games) and when i did for some reason the boot loader (the thing that lets me choose which OS i want) didn't show up. so to this i just made a very tiny (bout 2.5GB) partition of Ubuntu so i could get this loader. well now i have a partition that i NEVER use and the Ubuntu partition i do use won't update properly...i went to install gparted but it said i needed to download some other things quick but it wouldn't tell me what and of course nothing is downloading. i try just using the partitioner on the disk but it doesn't have an option of getting rid of only Linux partitions...only the whole system...what should i do? (please speak plain english for me...not quite the programmer type yet...)

thank you in advance!

---

### Post by audiomick on 2009-12-06
Hallo.
The reason your boot loader disappeared is that windows overwrites it when it is installed. You need to re-install it. You should find how to do that in one of these:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

As far as cleaning up your partitions goes, if you boot into the live CD, you can use Gparted from there. This is better anyway, because you can't change partitions when they are mounted, i.e. you wont be able to change the partition you are booted from.

You can also get Gparted on a live CD.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
And run it from there.

I would advise you to back up anything important that you have on the computer before changing partitions.

---

### Post by raymondh on 2009-12-06
I agree with audiomick ....

1.  Have a working/tested back-up of your files
2.  Reinstall GRUB
3.  Check that both OS' are booting
4.  Boot into the liveCD and access gparted to do some clean-up

Regards,

---

