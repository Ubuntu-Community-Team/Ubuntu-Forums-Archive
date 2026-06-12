---
title: "Cant Install 10.04"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nexoncore on 2010-03-23
I am trying to install 10.04 to a USB pen drive ( 128GB ). For some strange reason the normal installer keeps hanging at 5% at formatting. Theres nothing wrong with the USB pen drive as its brand new, I even used Gparted to test it by making a partition then formatting it which worked perfect.

Any idea's, also is there an alternative way to use a Live CD to install to USB?

I am running the installer now and its been hanging in 5% for about 20 mins now.

EDIT

Just got the following error message 
"The attempt to mount a file system with type ext3 in /dev/sda1 at / failed.

You may resume partitioning from the partitioning menu."

---

### Post by Mark Phelps on 2010-03-23
10.04 is still in Testing.

Please post your 10.04 questions and issues to the correct subforum, in this case, Development & Programming, Lucid Lynx Testing.

---

### Post by 2hot6ft2 on 2010-03-23
> **nexoncore said:**
> I am trying to install 10.04 to a USB pen drive ( 128GB ). For some strange reason the normal installer keeps hanging at 5% at formatting. Theres nothing wrong with the USB pen drive as its brand new, I even used Gparted to test it by making a partition then formatting it which worked perfect.

Any idea's, also is there an alternative way to use a Live CD to install to USB?

I am running the installer now and its been hanging in 5% for about 20 mins now.

EDIT

Just got the following error message 
"The attempt to mount a file system with type ext3 in /dev/sda1 at / failed.

You may resume partitioning from the partitioning menu."
Try FAT32 or ext2 for the file system type.

---

### Post by Elfy on 2010-03-23
moved to lucid

---

### Post by garvinrick4 on 2010-03-24
> **nexoncore said:**
> I am trying to install 10.04 to a USB pen drive ( 128GB ). For some strange reason the normal installer keeps hanging at 5% at formatting. Theres nothing wrong with the USB pen drive as its brand new, I even used Gparted to test it by making a partition then formatting it which worked perfect.

Any idea's, also is there an alternative way to use a Live CD to install to USB?

I am running the installer now and its been hanging in 5% for about 20 mins now.

EDIT

Just got the following error message 
"The attempt to mount a file system with type ext3 in /dev/sda1 at / failed.

You may resume partitioning from the partitioning menu."
I have made USB drives with many different types of drives and all sizes.
With persistence in Fat32 up to 4 gig. I use 8 gig drives with 2- 4 gig partitions so
I can make my own Home space.
2 gig without persistence. 4 gig with persistence. 16 gig formatted ext4 with a /boot a / and
a swap. Just making a system to carry in pocket.
The one thing I have found is some drives just do not want to boot. Centon always seems to work, Kingston hit and miss, HP never seems to want to boot.
 Of course they all hold info but some just do not want to be a bootable USB drive.
If you see crap at some store on add for $2.99 that is what you get crap.
I have wasted many an hour on bad flash drives. I have seen some that will work using
Unetbootin without persistence but will not boot using the Ubuntu USB installer with persistence. Just the way it is. But have found to always use gparted to format and Label. Believe me you can screw these things up pretty easy.

---

### Post by VMC on 2010-03-24
Have you tried the pendrive site. Here is a [**link**]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").Even though it says 9.10, I believe it will install any ubuntu iso. 

A 128 GB pen drive is very large.

---

### Post by nexoncore on 2010-03-24
The pen drive is a sony Vaio 128GB. But USB Startup Disc Creator currupted it and I am having issues formatting it correctly now ( thats another issue ).

I am going to try different versions to get them working, but I am having formatting issues, normally relating to wrongly located checksums.

What would you say is the best format to go with by default to restore it to a usable usb storage on both windows and ubuntu?

---

### Post by garvinrick4 on 2010-03-24
> **nexoncore said:**
> The pen drive is a sony Vaio 128GB. But USB Startup Disc Creator currupted it and I am having issues formatting it correctly now ( thats another issue ).

I am going to try different versions to get them working, but I am having formatting issues, normally relating to wrongly located checksums.

What would you say is the best format to go with by default to restore it to a usable usb storage on both windows and ubuntu?

That is one huge flash drive. 128 gig. Wow.
Use fat32 and if you are going to use startup disc creator format make the first partition 4 gig (all usb startup has in persistence.)Label it like maybe live and will have 124 gig left you label also. Label what you want. When you go to use it as a Live USB and boot off of it you got 2 seperate partitions and when you want just to store on it use the second partition. That way you can use the whole 4 gig for /root buy DO NOT upgrade the 
Linux version it screws the Live USB up. Once you get it like you like it go to software sources and turn off all the updates. Will be a nice Live USB and faster than CD by far. You can also have partners, medibuntu and other repositories so you can download ubuntu-restricted-extras all your sound card necessitys and such.
Go to synaptic and install alsa backports for your version. Not the server that is a screw up also. Enjoy even sounds like 124 gig left over can back-up whole image of drive using clonezilla. Oh yea Fat32 good for everything.

---

