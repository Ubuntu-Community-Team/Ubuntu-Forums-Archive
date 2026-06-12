---
title: "Install Ubuntu 18.04 with 16 GB disk space"
date: 2018-10-15
forum: Installation &amp; Upgrades
---

### Post by sygma-x64 on 2018-10-15
Hello,

I have a Windows 10 Laptop with a SSD 16 GB, currently useless for me...

I would like to make a dual boot W10/Ubuntu 18.04 by installing Ubuntu system on the SSD 16 GB and create several partitions on HDD 1 TB for /var /home /tmp and /usr. Can I install the system with only 16 GB ? Can it have performance or mounting problems ? Will I have the advantages of the SSD (speed) for my system and applications ?

I heard that it is recommended to seperate /var and /tmp because of the multiple writes on disk but in my case with 16 GB, must I also create a partition /usr on HDD ?

Thanks in advance.

---

### Post by The Cog on 2018-10-15
My desktop has a root partition that holds everything except /home, and only uses 8G (out of 20G). So unless you are using server type apps that put a lot of data in /var, /tmp or /usr I don't think it is worth separating them out.

---

### Post by sygma-x64 on 2018-10-15
Thank you for your response ;) I want to be sure I can install and use Ubuntu 18.04 on my 16 GB SSD.
Are you using a SSD ? I saw on different forums, it is not recommended for /var and /tmp to be on the SSD because there is a lot of writings and that reduces the life of SSD because a SSD will die earlier than a HDD and it is recommended to limit writings.

---

### Post by oldfred on 2018-10-15
Depends on SSD.
But now SSD life is considered to be similar to hard drive life.
Some last and some do not.
       hard drive life 
[URL="https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/"]https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/
      [/URL]
 SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead) 
    
You can change settings to use noatime setting in fstab, so just reading a file does not cause a write of a time stamp. 
You can put /tmp into RAM if you have lots of RAM.

       Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used. No installs now use swap file, but still never used, if lots of RAM.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 
    
       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022) 
    
[URL="https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/"]
[/URL]

---

### Post by sygma-x64 on 2018-10-15
Thanks ;)

So, I can install Ubuntu 18.04 on my SSD 16 GB. I think to use RAM for /tmp as you said, I have 8 GB but it should be enough, I will not use it intensively. 
Except /home, I can put everything (/var, /usr, ...) on 16 GB space ?

---

### Post by oldfred on 2018-10-15
I have multiple installs on my SSD and not all space used. But all data and some larger hidden folders normally in /home on my HDD like Firefox & Thunderbird profiles. But every thing else in /home is also in SSD. Including /home in / I show 7.2GB used. I put all data folders in a /mnt/data partition and link all the normal folders back to /home. So then my /home is tiny as it really is just configuration files. Any app like Thunderbird that may store lots of data in hidden folder in /home, get moved to my data  partition.

I do try to houseclean regular to remove old logs and other cruft.

```
fred@Bionic-Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.2M  1.6G   1% /run
[COLOR=#ff0000]/dev/sda4        25G  7.2G   17G  31% /[/COLOR]
tmpfs           7.8G   65M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1        50G   77M   50G   1% /boot/efi
tmpfs           7.8G   64K  7.8G   1% /tmp
/dev/sdb6       202G   68G  124G  36% /mnt/data
tmpfs           1.6G   16K  1.6G   1% /run/user/119
tmpfs           1.6G  200K  1.6G   1% /run/user/1000
/dev/sdb4        49G   11G   37G  22% /media/fred/backup_b
/dev/sdb3        49G  1.8G   45G   4% /media/fred/ISO_b

```

---

