---
title: "clone copy 12.04 from external drive to internal drive?"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2012-12-22
I have a perfect working ubuntu install with a separate /home
I would like to copy this install onto another pc.

I was thinking a copy command? then install grub?

Fstab will be different.

Does anyone have any ideas on this? We have very slow internet here, so regular install would be a very very long time.

---

### Post by oldfred on 2012-12-22
With system partitions you need to preserve ownership & permissions. Similar to a move /home.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue

     
You will have to reinstall grub & edit fstab with new UUIDs.

Grub also remembers where to reinstall on updates, so you need to run this.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
Not sure what changes these, so best to review:
Check that drive has changed:
       more /var/cache/debconf/config.dat  | grep /dev/disk
            more /etc/initramfs-tools/conf.d/resume
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by sdowney717 on 2012-12-22
thanks.
would you boot the liveusb first?
Would you create the partitions then copy the contents over?

---

### Post by oldfred on 2012-12-22
If you are doing copy or rsync then you have to create partitions first. 

But I always do new installs and reuse data partitions, so I usually just have to make a new / (root) partition. But I prefer to always create partitions in advance so I have control over sizes and locations.  Old installers did not give as many create options so that is the habit I have.

---

### Post by sdowney717 on 2012-12-22
what i have done is
boot the live usb
open gparted
create 3 partitions
/ of 20gb with boot flag
swap
/home 600gb

then i found the uuid and copied the /home and / (file system)



```
ubuntu@ubuntu:~$ sudo cp -Rp /media/d2b0798d-fe04-4f9c-96f0-3f3e8546eb98/* /media/0b7fbb2a-31b8-40eb-8b55-78170cbe6c68
ubuntu@ubuntu:~$ sudo cp -Rp /media/9593dbf8-c849-4564-b467-c274d21a4a6a/* /media/31a9c983-3ed2-4f85-8729-00c1879d9b96

```

now what is next step?

---

### Post by sdowney717 on 2012-12-22
ok, next step was to edit fstab file and replace the UUID numbers for the various partitions.

The installed 'boot repair'
before running boot repair, I disconnected the external drive
That reinstalled grub.

Then reboot and it was all there perfect!

I am very happy, this was very quick to do.

---

### Post by oldfred on 2012-12-22
Glad it worked. 

You may want to check some of the others commands I posted. I am not sure what gets changed when you reinstall grub or not. All the UUIDs need to be your new one's or later something may not work.

---

### Post by sdowney717 on 2013-01-15
adding more info on boot repair, sure made it easy to fix grub on the new drive
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

