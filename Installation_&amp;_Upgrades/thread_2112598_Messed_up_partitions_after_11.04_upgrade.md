---
title: "Messed up partitions after 11.04 upgrade"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by Zaraf on 2013-02-05
Hello 
 
I got an issue after upgrading a 10.10 ubuntu to 11.04 with an alternate CD
 
After installation and boot to ubuntu, I ran into the following error :
 
```
"the disk drive for /boot is not yet ready or not present"
```
 
.. with options to either ignore the error or manually repair. 
 
Ignoring the error led to the same message with "/home" and them prompted the ubuntu log-in screen. Once logged, several errors messages popped up and no GUI was displayed, leaving no other option than to reboot.
 
Solutions for similar problems were given [[COLOR="DarkRed"]here[/COLOR]](http://ubuntuforums.org/showthread.php?t=1724209) and [[COLOR="DarkRed"]there[/COLOR]](http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation/) (remount the root partition, then launch an update) but in my case that didn't fixed the issue. 
 

 
My pc is configured as a dualboot windows7/ubuntu 64 bits on a Raid0, using two HD. My /etc/fstab is as follow :
```
/dev/mapper/isw_djibifgbhd_Volume06 /     ext4 errors = remount-ro 0
/dev/mapper/isw_djibifgbhd_Volume03 /boot ext4 defaults 0
/dev/mapper/isw_djibifgbhd_Volume07 /home ext4 defaults 0
/dev/mapper/isw_djibifgbhd_Volume05 none  swap defaults 0
```
 
Using fsck -a and mount -a lead me to the following messages :
 
fsck -a :
```
fsck.ext4: No such file or directory while trying to open dev/mapper/isw_djibifgbhd_Volume06
```mount -a :```
mount: special device /dev/mapper/isw_djibifgbhd_Volume03 does not exist
mount: special device /dev/mapper/isw_djibifgbhd_Volume07 does not exist
``` 

When booting on a live CD, gparted could not recognized my partitions (just the two hard disks) while disk utility still detect how the different drives were configured. 

I assume I just have to make the system recognize the volumes somehow. The solution may be trivial, but I am not used to deal with this kind of problems and I don't know how to resolve this issue. 
If someone can give me some hints about how to proceed, thanks in advance !

---

### Post by snowpine on 2013-02-05
Welcome to the forums!

The "good news" is that 11.04 is obsolete and completely unsupported. So you can do a fresh reinstall of 12.04 or 12.10 and then restore your files/documents from your backup. :)

---

### Post by Zaraf on 2013-02-05
Thank for your answer !
 
Well, reinstalling a new fresh version of 12.04 was my first thought (in fact I aimed to upgrade to this version, but I needed to upgrade to 11.04 first), but I will have a lot of softwares/libraries to reconfigure and reinstall, so I was looking for a way to bypass this problem and keep my system configured as before.
 
But if I can't find a solution quickly, that will be the best thing to do indeed.

---

### Post by darkod on 2013-02-05
In live mode, if you try to activate the fakeraid, what does it say:
sudo dmraid -ay

That should activate the fakeraid array and the partitions on the raid device should show up. From there on you can try restoring grub2 to the MBR of the raid device, but that might not work if the upgrade was interrupted.

The question is whether it was interrupted, or simply grub2 didn't install correctly to the MBR of the array after the upgrade.

If it was interrupted, you might need to enter the installation with chroot and try to fix the interrupted upgrade.

Note that when using separate /boot partition you need to take that into account when reinstalling grub2 to the MBR of the array. And make sure you install it onto the array device, not a partition on it.

---

### Post by Zaraf on 2013-02-05
Thanks for answering

sudo dmraid -ay told me that all the volumes, literally.. :

isw_djibifgbhd_Volume0
isw_djibifgbhd_Volume0p1
isw_djibifgbhd_Volume0p2
isw_djibifgbhd_Volume0p3
isw_djibifgbhd_Volume0p4
isw_djibifgbhd_Volume0p5
isw_djibifgbhd_Volume0p6
isw_djibifgbhd_Volume0p7

...are already actives

In fact I tried several live cd, and gparted could recognize my partitions when using the 12.04, 11.04 and even 9.10 live cd. In fact just the the first live cd I used (10.10) couldn't recognize them for some reasons..


About the upgrading, maybe something happened during the first attemps as it froze (upgrade window didn't display anything), maybe due to the fact the proxy didn't allow it to connect while I let the upgrade software the possibility to download packages. I didn't think the installation have already begun before the freeze though.

I didn't allow downloading for the second attempt, and it seemed it worked fine, until I rebooted and got this problem.


By the way, a noob question, I noticed the names of the volumes displayed with dmraid **XXX_Volume0pX** are not the same than the names of /etc/fstab **XXX_Volume0X**. Could this cause the problem somehow ?

---

### Post by darkod on 2013-02-05
Yeah, it could. I was just about to point that out. Don't forget, in linux everything is as you see it, including capiral letters vs small letters.

The fakeraid partitions are /dev/mapper/blahblah_Volume0pX and the whole raid device is only ...Volume0 without the pX at the end. When you install grub2, it should go there.

When you specify partitions for any commands, including in /etc/fstab, they should be ...Volume0pX.

---

### Post by Zaraf on 2013-02-05
Editing the names in /etc/fstab did the trick ! 

Apparently this was a rather common problem for people using raid and upgrading to the Natty version. Don't know why the names got changed though.

Now I just hope the upgrade to 12.04 will not bring more surprises..


Thanks for your help !

---

