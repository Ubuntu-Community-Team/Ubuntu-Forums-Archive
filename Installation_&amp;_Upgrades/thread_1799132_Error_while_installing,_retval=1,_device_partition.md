---
title: "Error while installing, retval=1, device partition=H:"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by samsambhav on 2011-07-07
I have a HP Pavilion dm4-1177 (640GB HDD, 6GB RAM, Windows 7 Home Premium 64 bit os, Intel core i5 2,4GHz). I tried to install Ubuntu 11.04 (both 32 bit and 64 bit) using the wubi, on a separate partition I kept exclusively for linux (10GB). During the mid-way of installation, it said: 

An error ocurred:
Error executing command 
>>command=C:\Windows\sysnative\bcdedit.exe/set{c644fa11-0e.......................} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
>>stdout=

For more info, please see the log file.....


This occurs for both 32 bit and 64 bit setup, and the same happened when I tried to install Ubuntu 9.10, 10.04 as well. 

Since I am not that good in understanding these error reports, could someone please help me out with what's the solution to this.?

I even tried to boot the laptop using pendrive with Ubuntu. During the installation, the free partition showed as 'unusable'. And if I try to install in the same directory which holds Win7 (c drive) then it installs successfully, but while booting next time, it just goes into a blank screen. 

Please please help :(

---

### Post by mörgæs on 2011-07-07
Hi, welcome to the fora.

For Wubi problems, best is to post in this thread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-07-07
That's likely a dynamic drive. You can't install Ubuntu if you are using these. Check in Windows' "Disk Management" and see if the type is "dynamic".

(You shouldn't install it on any partition if this is the case or you could damage your data - and windows).

---

### Post by samsambhav on 2011-07-08
@mörgæs : oh i didnt know. thank you anyways!

---

### Post by samsambhav on 2011-07-08
@bcbc:

hey, yes, i found the discs to be of type dynamic. The 640 GB is partitioned into 4 parts. 
1. windows 
2. recovery
3. my files
4. linux

I have kept the 4th partition for linux. But since all the above 4 partitions are dynamic, I guess I am not able to install Ubuntu. 

So what is the solution out? Can I not make them static (non-dynamic)

Please help me. :)

---

### Post by bcbc on 2011-07-08
Here is a thread that discusses this: [http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

If you're not using any special features e.g. striping/mirrors so they're basically simple partitions it might be possible to fix it on the fly. Otherwise, you might have to backup and reinstall.

---

