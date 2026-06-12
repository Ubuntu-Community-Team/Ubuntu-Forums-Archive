---
title: "Does Grub2 overwrite Grub on Upgrade from 8.04 to 10.4"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by DocEsq on 2010-06-21
I have been running a dual boot XP and Ubuntu 8.04 on two separate hard drives for a while now without any problems.  I used the method posted [http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I will be upgrading to 10.4 soon (probably after the re-spin in July) and was wondering if I will have problems after upgrading dual booting.

I do not know if while upgrading Grub remains or if Grub2 tries to overwrite.  I have read that Grub2 will try to install onto all partitions and hard drives in a fresh install but do not know about upgrading.  If it does try I think I need to put it in hda,1 which is the primary drive where Ubuntu is located.

This is not something I have been able to find the answer to with google.

I also have Kubuntu on the system which I can change with session manager and am not sure what will happen to that once I upgrade Ubuntu.

Any thought will be appreciated.

Thanks.

DocEsq

---

### Post by garvinrick4 on 2010-06-21
> **DocEsq said:**
> I have been running a dual boot XP and Ubuntu 8.04 on two separate hard drives for a while now without any problems.  I used the method posted [http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I will be upgrading to 10.4 soon (probably after the re-spin in July) and was wondering if I will have problems after upgrading dual booting.

I do not know if while upgrading Grub remains or if Grub2 tries to overwrite.  I have read that Grub2 will try to install onto all partitions and hard drives in a fresh install but do not know about upgrading.  If it does try I think I need to put it in hda,1 which is the primary drive where Ubuntu is located.

This is not something I have been able to find the answer to with google.

I also have Kubuntu on the system which I can change with session manager and am not sure what will happen to that once I upgrade Ubuntu.

Any thought will be appreciated.

Thanks.

DocEsq
I do believe you will be prompted to ask what you want to do with grub, leave what you have or what comes with 10.04 on upgrade. On fresh install of course you get grub2. On fresh install you need to put into sda in advanced tab on page 8 or last page in lower right hand corner. Not sda1 or sda5 but sda. If you decide you want grub2 it will overwrite on install if you put in sda on install. Ubuntu makes it pretty much of a no brainer really. I will leave you a link that I like on grub. There are some good users in this forum on grub usage so do not let that hold you back when
time comes. Have a nice day.

[GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")

---

