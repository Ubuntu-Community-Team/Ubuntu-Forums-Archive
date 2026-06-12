---
title: "specific assistance with partitioning"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by adam76 on 2014-09-02
[COLOR=#000000]Now I have read through the forums and found some good information (here in fact) on how to setup partition and proper drives etc however I have not seen anything with TWO hard drives also the information I have found is not extremely detailed for a new user such as myself.  
 
With that said I attempted to follow the information I found and I am having an issue...  
 
My setup: I have a Toshiba satellite u840w 64bit quad core with 6gb of memory, 32gb SSD, 500gb drive (not SSD). 
  
I was attempting to partition in a manner that my 32gb was used to boot the system and run the ONLY linux, then set my Applications to all be installed on my 500gb hdd, even the liberalities if possible as I don't want any files to max out my 32gb, I want to keep it clean for booting and the core Linux os files. 
  
just as an example, 
  
/dev/sdb = 32gb ssd 
 /dev/sda = 500gb hdd 
  
So I set the partition as such: 
  
(logical)       /dev/sdb       ext4         /                   (25120 MB)          beginning 
 (logical)      /dev/swap      swap                               (6880 MB)            beginning 
 (primary)   /dev/sda         ext4       /home      (500000 MB)        beginning 
  
When I boot, I set my 32gb SSD to boot first in the BIOS, (second device in line) so I move it up to #1 in front of the 500gb hdd in the boot sequence so it boots first.... The problem is when the system boots up, I get a black screen with a blinking cursor and it never does anything, HOWEVER when I set the boot devices sequence to boot my 500gb hdd first, it boots, but feels like it runs a bit clunky when pulling up applications and just general moving inside the x server.  
 
Please help Thanks in advance!!![/COLOR]

---

### Post by sotiris2 on 2014-09-02
Well probably grub is installed in sda. It doesn't really have any problem to look in the ssd to find the os though. So that is not really a problem.
The feel you say is in just general moving inside the x server so I suppose it has more to do with graphics. It appears to have intel graphics via a quick google. They are supposed to work well with the open drivers (I don't even know if there are non-open drivers for intel) so if they don't work well I 'm not sure what you can do. Maybe try updating the system? 

Also something more general. Applications in ubuntu are not usually installed in /home folder. So any program you will install will be in the ssd. To do otherwise would require a more complex partition scheme and also you have to note that using a pc is not just using the os, so why would you want your applications to be on a slower drive?

---

### Post by adam76 on 2014-09-02
I updated the bios and made sure I was using the proper graphics drivers as well. 
In regards to the performance comments I made when using X server, I should have mentioned that prior to this partition setup, I did not have the 500gb hdd formatted or partition. It was not mounted however Ubuntu recognized it as 'unknown' inside gnome disk utility. After formatting, and mounting it is when I attempted to reinstall Ubuntu and that's what lead me to the above issues.
 Also, the first time when performance was amazing, I selected "Install Ubuntu 14.04 LTS" and did not try to advance partition anything. Again, this was with the 32gb SSD only.

---

### Post by adam76 on 2014-09-02
I think I figured it out... upon installation, at the bottom of the Ubuntu install, it says "device for bootloader install"..... I think I had it set to the 500gb hdd, which would make sense as to why I am having issues when trying to boot from the 32gb SSD... I'll test and post back, thanks for the reply sotiris2!

---

### Post by grahammechanical on 2014-09-02
The installer defaults to installing the boot loader (Grub) into sda. Which, in your case, is the 500GB hard disk. If you are confident that Ubuntu is installed on the 32GB SSD, then load into Ubuntu and open a terminal and run

```
sudo grub-install /dev/sdb
```

That should put Grub in the 32GB SSD (sdb).

Regards.

---

### Post by adam76 on 2014-09-02
Thanks very much grahammechanical! After the install is complete, are you saying I just run this command in the console and set the BIOS boot sequence to my 32gb ssd?

I allocated 2gb to /boot  and the rest to /  for my 32gb drive so it has no free space.... hmmm wonder if it will still install.

I will keep you posted thanks!

---

### Post by adam76 on 2014-09-02
seems to be working now but does throw an error, I'll try to catch it and report back, thanks!

---

### Post by Bucky Ball on 2014-09-02
> **adam76 said:**
> seems to be working now but does throw an error, I'll try to catch it and report back, thanks!

Yep, chuck us that error, verbatim if possible ... ;)

---

