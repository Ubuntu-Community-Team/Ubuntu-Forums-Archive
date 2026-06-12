---
title: "Seeking advice on partiton sizes for dual boot"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by asarkar on 2011-01-23
Hi,
I have come back to using Linux after about 5 years. I wish to keep a Win7 64 bit and Ubuntu 10.04 64 bit on my Lenovo T61 laptop. It has a single 250 GiB HDD and 4 GiB memory. I have cooked up the following partitioning scheme and would like to get some advice on it.
I am a computer programmer by profession and will be mainly using Ubuntu for work. Win7 will mostly be for proprietary softwares and my hobby of photography. I expect Ubuntu to be used less than Win7.
Thanks in advance.

```
Partition	File System	Mount Point	Size (MiB)	Usage
------------------------------------------------------------------------
/dev/sda1	NTFS		                40000	        Win7 pri
/dev/sda2	ext2	         /boot	          500	        boot
/dev/sda3	ext4	         /	         6000	
/dev/sda4	linux-swap		         8000	        swap
/dev/sda4	extended		       195500	
  /dev/sda5	ext4	         /usr	        12000	
  /dev/sda6	ext4	         /usr/local	 5000	
  /dev/sda7	ext4	         /var	         5000	
  /dev/sda8	ext4	         /tmp	         3500	
  /dev/sda9	ext4	         /home	        40000	
  /dev/sda10	NTFS	         /media/storage	130000	        Common
```

---

### Post by asarkar on 2011-01-23
47 views and not a single reply! Did I ask something too obvious or too complex?

---

### Post by presence1960 on 2011-01-23
Keep it simple- there is no reason for all those separate partitions nor is there any advantage gained from having all those separate partitions except maybe for /home.

My personal experience has led me away from a separate /home due to the fact I multi-boot. Not a good idea to have a shared /home between distros or even different versions of same distro because lots of settings and configurations are contained in /home. If you have different version #'s of software in each distro you may run into problems. I have opted instead for a partition for all my data and let each distro have it's home in the default created in the installation this way software uses the settings for it's proper version.

---

### Post by oldfred on 2011-01-24
Herman posted some more reasons for standard desktops to not have all the system partitions.

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by asarkar on 2011-01-24
From the suggestions and links provided so far, would it look like the following? 3 primary, 1 extended, big /home.
```

Partition	File System	Mount Point	Size (MiB)	Usage
------------------------------------------------------------------------
/dev/sda1	NTFS		                40000	        Win7 pri
/dev/sda2	ext2	        /boot	          500	        boot
/dev/sda3	ext4	        /	         6000	
/dev/sda4	linux-swap		         8000	        swap
/dev/sda4	extended		       195500	
/dev/sda5	ext4	        /home	        65500	
/dev/sda6	NTFS	        /media/storage 130000	        Common


```

---

### Post by oldfred on 2011-01-24
I still would not create the /boot unless your system is old and has the 137GB boot limit. I might make / 10 to 20GB since everything system wise goes into root. I find with lots of programs I have used about 6GB, but if you write a DVD, you may use 4GB in tmp. So I assume I use about half of the total I allocate.

---

### Post by asarkar on 2011-01-24
@oldfred: how big is your /home?

---

### Post by oldfred on 2011-01-24
My /home is less than 1GB, but I aggressively move anything that has much data into my /data  or /shared partitions. So it is hidden files and folders that are mostly configurations. I have not moved wine yet so that is most of what /home is now.

I had upgraded in place for several years and only had root & swap. But wanted a clean install.  I decided I needed the separate /home so I created a 100GB partition (new drive - lots of room). But then decided I still wanted a /data. After I got done moving all the data out of /home my /home was only about 1GB. I have since let /home remain in root.

---

### Post by presence1960 on 2011-01-24
> **asarkar said:**
> From the suggestions and links provided so far, would it look like the following? 3 primary, 1 extended, big /home.
```

Partition	File System	Mount Point	Size (MiB)	Usage
------------------------------------------------------------------------
/dev/sda1	NTFS		                40000	        Win7 pri
/dev/sda2	ext2	        /boot	          500	        boot
/dev/sda3	ext4	        /	         6000	
[COLOR="Red"]/dev/sda4	linux-swap		         8000	        swap[/COLOR]
/dev/sda4	extended		       195500	
/dev/sda5	ext4	        /home	        65500	
/dev/sda6	NTFS	        /media/storage 130000	        Common


```
You can't have two sda4s. I would put swap inside the extended partition!

---

### Post by asarkar on 2011-01-24
> **presence1960 said:**
> You can't have two sda4s.
It was a typo - thanks for pointing it out though. Someone has eagle eyes!

---

### Post by asarkar on 2011-01-24
Last question: in which of the following partitions should I install GRUB2?```

Partition    File System    Mount Point    Size (MiB)    Usage
------------------------------------------------------------------------
/dev/sda1    NTFS                        50000            Win7 pri
/dev/sda2    ext2           /boot          500            boot
/dev/sda3    ext4           /            15000            root
/dev/sda4    linux-swap                   8000            swap
/dev/sda5    extended                       -    
/dev/sda6    ext4           /home        25000    
/dev/sda7    NTFS           /media/storage remaining      Common

```

---

### Post by oldfred on 2011-01-25
The install of grub is to the MBR as that is how computers boot.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

While it primarily discusses Vista (Linux at end) it applies to all MBR (msdos) systems and how they boot. If too much detail at least review pictures.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by asarkar on 2011-01-30
Thanks for all the suggestions. Installed Ubuntu 10.10 successfully and running for 5 days now w/o problems. Had to install totally in extended partition though because of Win7 primary partitions.

---

