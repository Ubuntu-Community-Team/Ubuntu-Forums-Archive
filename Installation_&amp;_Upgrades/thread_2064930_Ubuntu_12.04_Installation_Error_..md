---
title: "Ubuntu 12.04 Installation Error ."
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by Irishboy24 on 2012-09-30
Hi All,

I'm new to Ubuntu and installed my very first distro 12.04 on a dual boot Windows XP. 
Although, i can log in without any issues and it works well, i have everything set up and ready to go. Only annoying thing is when i boot up my machine i get the following error:

"Serious errors were found while checking the disk drive for /", i press i for ignore and it works well after that. how do i get rid of this error ? 

--Second question:

I want to be able to create a shortcut to my windows drive. I only have C drive and although it shows up on the home folder, i have to click on it after boot to get it to mount. Is there a way to auto-mount so after reboot i can see the drive on my desktop ?  

Note that /dev/sda5 is where ubuntu is installed. technically that too is a windows partition with abt 40Gb and i can get to it via /host. 

Please ignore my windows heavy accent!! i'm still trying to learn Linux. 

```

@ubuntu:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G  3.3G   14G  20% /
udev            1.4G  4.0K  1.4G   1% /dev
tmpfs           549M  848K  548M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G  152K  1.4G   1% /run/shm
/dev/sda5        42G  4.9G   37G  12% /host
/dev/sda3       419G   91G  328G  22% /media/669427A7942778A7


```

---

