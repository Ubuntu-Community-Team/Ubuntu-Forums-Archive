---
title: "Unable to mount any partition"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by najim on 2011-08-29
Hello 

I have a problem booting ubuntu 10.10 it suddenly gave me an error No init. Try passing init= bootarg three days ago, i have tried out many options with Live CD but have failed, boot_script_info, none of the partitions mounts even with Live CD, i can't access my data. am kindly seeking for assistance on this.

Thanks

---

### Post by saeed42 on 2011-08-29
This might be due to installing Natty on btrfs filesystem.
I have the same problem.
I installed Natty on btrfs without major problems and used it for more than a week.

---

### Post by najim on 2011-08-29
Thanks saeed42
My file system is Ext and then other partitions simply show Linux, have you been able to solve this, or else a way to accessing and removing all my data and do refresh install, i sometime back tried to upgrade to 11.04 but failed due to internet connection and the process was rollback, I have also tried installing ubuntu 10.10 again but move past the prerequisite check point
:confused:

---

### Post by ajgreeny on 2011-08-29
> **najim said:**
> I sometime back tried to upgrade to 11.04 but failed due to internet connection and the process was rollback, I have also tried installing ubuntu 10.10 again but move past the prerequisite check point
Has the machine been working OK since this update failure, or is that when things started to go wrong?

I suggest boot to a live CD/USB and run ```
sudo e2fsck /dev/sdx#
``` on each partition which may help sort the problem, changing the sd**x#**, obviously to your own partition setup.  Let's see if there are any clues or error messages from that.

---

### Post by najim on 2011-08-29
> **ajgreeny said:**
> Has the machine been working OK since this update failure, or is that when things started to go wrong?

I suggest boot to a live CD/USB and run ```
sudo e2fsck /dev/sdx#
``` on each partition which may help sort the problem, changing the sd**x#**, obviously to your own partition setup.  Let's see if there are any clues or error messages from that.

Well the machine worked well for some days after the upgrade to 11.04 failed, the blackout happened as i was using the machine and then suddenly it throwed an error.

I have tried the your commaned sudo e2fck /dev/sda1 this my swap partition and i have a warning:: This filesystem is mounted. if you continue you will cause severe filesystem damage Y/N to continue, what should i do??? 

What the implication??

---

### Post by dino99 on 2011-08-29
uou need to do it from a livecd, not on a partition running (so the warning)

---

### Post by ajgreeny on 2011-08-29
> **dino99 said:**
> uou need to do it from a livecd, not on a partition running (so the warning)
Even using a live CD the swap may be mounted and in use, (live CDs are clever enough to find swap and use it), so use command ```
sudo swapoff -a
``` in terminal to turn swap off and try again, though there is no point in fsck'ing a swap partition; do it on your OS root partition, and /home if that is separate.

---

### Post by najim on 2011-08-30
Hello Once again, up to now i have not found a straight answer to my problem, am trying to troubleshoot a boot problem, every time i turn on my machine it gives me 

```
No init, Try passing int= bootarg 
```
I searched a couple threads and i need to either post the output of boot_info_scrip.sh here so i can find help but still am unable to get the result.txt after running boot_info_script  the command runs into any error and hangs at some point this the all i end at when i execute the script

```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
```

please see attached screen-shot and kindly advise me i really need to have this machine boot again and get my data off or find  away of getting all my data off and then do a fresh install 

Thanks in advance

---

