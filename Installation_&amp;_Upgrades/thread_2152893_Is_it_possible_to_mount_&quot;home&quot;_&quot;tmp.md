---
title: "Is it possible to mount &quot;/home&quot; &quot;/tmp&quot; and &quot;swap&quot; partitions after installing Ubuntu"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by SangeetKhatri on 2013-06-09
I have recently installed Ubuntu 12.04 but the problem is that i forgot to define the mount points for "/home" "/tmp" and "swap" and i only mounted "/" to a 60GB Partition. And now i cannot see any other partitions (ofcourse i did not mount them). And my "/home" shows about 55GB Space which leaves the rest around "250GB" unusable.

So is there in any way possible to mount atleast the "/home" folder, if not "/tmp" or "swap" from the unusable "250GB" partition.

I would have reinstalled but the Live USB made from Unetbootin gives me strange error that "Invalid or corrupt Kernel Image" . Hence i cannot reinstall Ubuntu from the same .iso .

If in any way is it possible then please help me out.

Any help is highly Appreciated.

Regards.

Here is also an image of my drive partitions (as seen in Gparted)
[IMG]http://i.imgur.com/8kZlujF.png[/IMG]

---

### Post by oldfred on 2013-06-09
You need a working live installer either flash drive or DVD as gparted will not work on mounted partitions. It may work on your unallocated since it is not mounted, but always best to use live installer.
You can install gparted to your current install.
sudo apt-get install gparted

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You can move /home with this:

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you create a swap partition you can just mount it in fstab. Search for fstab for example fstab entry:

 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

