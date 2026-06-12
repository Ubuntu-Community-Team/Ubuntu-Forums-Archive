---
title: "Re-install Ubuntu 14.04"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-07-22
Is it possible to re-install the same version of Ubuntu (14.04) on a PC without erasing /Home? The home directory is on a separate partition by itself. If I choose automatic option, will the installer program only erase and format the / (root) partition where the OS lives?

Or should I choose the something else option, and select the / partition as root? If I do this, will the installer leave the /Home partition alone?

Thanks for your help. I should know this by now, but I only have to install every once in a blue moon, and the last time was a couple of years ago, so just think of this as victims of your own success ;<)

---

### Post by kc1di on 2014-07-22
Hi mayagrafix,

if you want to ensure your /home partition is left alone you should pick other at the partition page and only select the /root partition for formatting. 
You also will need to lable the other partition as /home but without formatting it.  so it will be mounted at boot time.
and yes since your installing the same version you should be ok with your old /home directory.
good luck :)

---

### Post by Mark Phelps on 2014-07-22
I would be very careful about selecting any "Replace" option when reinstalling Ubuntu.  There have been lots of posts from folks who did this only to find their whole drive had been reformatted in the process.  Mint has rewritten the warning message for their installer to tell folks that the entire drive will be erased; in (typical?) Canonical fashion, they do not see this as a "problem" that needs to be "fixed".

---

### Post by yancek on 2014-07-22
> Or should I choose the something else option, 

Definitely do that as it gives you the control you need.

---

### Post by mayagrafix on 2014-07-27
Me thinks better safe than sorry. I will create a vbox test HDD like mine (with separate /Home partition) and try installing on it first.

---

### Post by yancek on 2014-07-27
> Or should I choose the something else option, and select the / partition  as root? If I do this, will the installer leave the /Home partition  alone?

As long as you don't select to format the /home partition using the Something Else option, I would think this would work.  I've never done it myself and in fact prefer to use separate data partitions rather than /home partitions because of the user configuration file in the /home directory.  I think your solution to try it on a Virtual install is a much better and safer way to test.

---

