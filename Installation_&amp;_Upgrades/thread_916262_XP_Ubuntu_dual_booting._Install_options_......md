---
title: "XP Ubuntu dual booting. Install options ....."
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Daniel Baker on 2008-09-10
I am about to install Ubuntu.

I have a sony vaio laptop. I have it presently dual booting xp and debian. I have a Lilo bootloader.


On going thorugh the installation process for Ubuntu I am not sure on a couple of things.


After  deleting  the debain partition and replacing  it with a partition for ubuntu.  
I get  warning saying I need to create a swap partition . How do I do this.


Where do I install the bootloader. I have these options
 /dev/sad ATA Fujitsu .....
/dev/sda1 windows NT 2000 Xp
/dev/sda2 windows xp media edition
Note sony laptops have a seperate partiotion for a windows restore feature. One of the above is the resore partition. 
Ive been told I want to creat the bootloader in the MBR 

For the advanced bootloader options  do  I want to creat  a "primary type"
does the loacation want to be at the "beginning" or "End"
should I use   "ext3"
does the mount point want to be mount /


Thanks for you help.

Im looking forward to using Ubuntu.

---

### Post by Sef on 2008-09-11
How much ram do you have?  If you have 2 GB or more, you really don't need a swap partition, but if you want to make one, then make it 1 GB.

---

### Post by Daniel Baker on 2008-09-11
> **Sef said:**
> How much ram do you have?  If you have 2 GB or more, you really don't need a swap partition, but if you want to make one, then make it 1 GB.

Thanks for this. I have 2 GB and didnt bother with a partition. 


I watched a youtube video on triple booting which seemed to fit my requirements. 


I went ahead with the install an it worked perfectly. So far Im thrilled with Ubunu. :-)   


Thanx 

Dan

---

