---
title: "resizing swap after install?"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by mendoza on 2005-06-03
Hi
I've noticed that my swap partition might be too small (=my ram size, while it should be twice its size I think). I've tried to resize it with qtparted but it was not possible because I couldn't resize my other partitions to make some free space. 
On a 10Gb Hd I have 1st: 256 Mb swap (primary), 2nd: 5 Gb / (primary), and then 5 Gb /home (logical).

Any idea?

---

### Post by mingus on 2005-06-03
A few thoughts . . .

First, the old rule about 2x RAM is not as strict as it was in the early days.  When machines only had 16-32MB of RAM, there was a desperate need for that much swap.  With the RAM typical in machines now, 2x can be overkill.  Furthermore, swap is a very poor substitute for RAM, just because you have it doesn't mean you will get the extra performance you desire; this depends heavily upon your particular usage profile.  To get an idea how close you are to needing more swap, run the applications as you usually will and then use the system monitor to see how much swap is being used.  If it shows that most of the swap is taken, you probably need more.  Having said that. . .

Second, take a look at gparted rather than qtparted (it's in Universe).  Compare
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)        with
[http://qtparted.sourceforge.net/features.en.html](http://qtparted.sourceforge.net/features.en.html)
both programs are based on the same libparted library, as is the partitioner used in the Ubuntu install - this is important, because mixing partitioners can be dangerous.  (Gparted uses a gnome interface while qtparted uses KDE).  GParted claims it can shrink or grow partitions while qtparted does not; that may because it is better integrated with other filesystem utilities.  The documentation provides examples that sound similar to what you want to do.

Third, unless you can risk a reinstall, make sure your system or data is backed up before ever touching the partitions.

---

### Post by az on 2005-06-03
You cannot resize a partition that has a mounted partition on it.

Basically, you need to run from a live cd, like the installer.

[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

You can use the installer cd to resize your partition and make more room.

One thing about resizing a partition.  You cannot resize a partition from the beginning.  You must shrink it  from the end.  The fact that your swap comes first is problematic.

I would say that your swap is big enough.  You do not want to be swapping all that much anyway...

If you want to use hibernation, you will need to grow your swap a little.

If you really insist on more swap space, there is nothing wrong with having two swao spaces....  Just add another entry in your fstab after creating another swap after one of your partitions...

---

### Post by mingus on 2005-06-03
azz is absolutely right . . . I forgot about the shrink limitation.  And again, I agree that there is probably not much value in more swap.

Should you decide you must have more swap, in addition to shrinking /home to allow room for another swap partition, there is yet another option, creating a swap file.  There has been some debate on whether this is a good idea, but Red Hat and other distros permit it.  You can easily find more info on this alternative with google.

---

### Post by mendoza on 2005-06-04
Thanks to both of you; Very helpfull information!
Since it is my second install on the same computer, it seemed to me that the system was slightly slower. But I will keep it like this I think.

---

### Post by mingus on 2005-06-04
You are very welcome.  Happy to be of some help.

---

