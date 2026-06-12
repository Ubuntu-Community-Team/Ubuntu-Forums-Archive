---
title: "How to reinstall after 11.04 upgrade nightmare"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by diamond_D on 2011-05-10
Hi,
 
My upgrade from 10.10 to 11.04 did not work properly as I get hung at the "Splash Screen" upon startup.
 
I used the alternate CD for installation as I have a mix of standard and LVM partitions. I want to do a reinstall but keep as many of my old partitions / mount points as possible. I am a N00bie at trying this as I have never had any upgrade issues. So basically what I would like to do would be something like reinstalling the windows C: partition but keeping all the data on my other partitions so It is available post reinstall. All suggestions and advice will be greatly appreciated.
 
**_/dev/sda contains the following partitions/mount points:_**
 
_Standard ext4 partitions_
/boot
/ (root)
 
_LVM volume 00 (ext4)_
/home
/usr
/usr/local
/opt
/tmp
/var
/swap
 
 
**_/dev/sdb contains the following partitions/mount points:_**
 
_[U]Standard ext4 partitions_[/U]
/data
/vbox1 (used to contain my VM's)
 
_LVM Volume 01 (ext4)_
 
/misc

---

### Post by diamond_D on 2011-05-10
So if I decide to use the installer CD to reinstall. I read that if I choose manual partitioning and assign the mount point but do not set the format flag I can keep the data that's on my /home partition. Basically I want to know what partitions/mount points do I need to format besides / root when doing a reinstall? Are there any issues I need to look out for because I have a mix of standard partitions and LVM volumes. My / root partition is on a standard 20GB partition but my other system partitions such as /var and /usr are on their own partitions inside and LVM volume.

---

### Post by diamond_D on 2011-05-12
At least 10 seperate reboots did not allow me to fully boot the Unity desktop. I could get to the text based installer and that's it.
 
Then I decided to boot from the live CD and was able to load everything fine. I did absolutely nothing but boot from the live CD.
 
Next I popped out the CD, rebooted and through some devine intervention Unity loaded properly and all my partitions are available. I tested rebooting a few more times and all is good.
 
 
Can somebody please explain to me on how simply booting from the live CD allowed my next reboot to be successful?......besides "devine intervention" that is.

---

