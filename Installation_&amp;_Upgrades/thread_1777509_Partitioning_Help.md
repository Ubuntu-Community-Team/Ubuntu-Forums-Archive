---
title: "Partitioning Help?"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by c0nrad on 2011-06-07
Hey,

I haven't used linux in awhile and I just got a new computer and I'd like to install ubuntu on it. But I'm having some problems partitioning. It's probably simple but I'm not really sure what I'm doing.

Right now I have windows 7 installed and that's it. I tried to resize one of the partitions to make room for ubuntu, but it says the memory is "unusable". I checked online and I saw something about only 4 partitions or something? But I'm not sure which partitions I can delete. It came with four.

I'm trying to just have a partition or so for windows with 200gb, and the rest for linux, with a small swap partition.

Here's where I am now:
[http://img593.imageshack.us/img593/4483/screenshotinstall.png](http://img593.imageshack.us/img593/4483/screenshotinstall.png)

Any help?

Thanks,
c0nrad

---

### Post by Quackers on 2011-06-07
Please quit the installer and boot into Windows 7.
Then enter the Disk Management screen and post a screenshot, if you will.
I assume that all 4 partitions are primary partitions. I also assume that one is a boot partition (system reserved) of 100MB to 200MB, one is your C: drive, one is a recovery partition and the other is a HP TOOLS partition (or similar).
If this is correct it is very important that you don't try to create another partition at this time.

---

### Post by c0nrad on 2011-06-07
Here it is:

[http://img37.imageshack.us/img37/5738/disknew.jpg](http://img37.imageshack.us/img37/5738/disknew.jpg)

Thanks for the help,
c0nrad

---

### Post by Quackers on 2011-06-07
You're welcome.
It's good that you stopped when you did. The unallocated space in the middle will come in handy :-)
Other people in your position have deleted the HP TOOLS partition. It is, I believe, a partition which holds a few diagnostic tools. However, I am informed that  those tools are available separately on the HP website. You may (or may not) wish to confirm that first.
To delete the partition just right-click on the partition in your current window and select "delete volume" iirc.
When that's done you can boot from the Ubuntu live cd/usb and the install alongside option should then be available. You can use this option or you can manually create partitions (which should be logical partitions - NOT primary partitions) by choosing the manual option (or "something else" option in 11.04).

As you have not said which version of Ubuntu you intend to install I will say that if you are using 10.10 (Maverick Meerkat) it is NOT recommended that you use the "alongside" option, as it has a nasty habit of eating Windows systems!

---

### Post by c0nrad on 2011-06-08
Worked perfectly. Thanks a bunch.

---

### Post by Quackers on 2011-06-08
Excellent! :-)
Happy Ubuntuing!

---

