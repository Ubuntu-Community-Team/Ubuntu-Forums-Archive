---
title: "Partitioning/Home/Moving"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by wsfield99 on 2012-10-30
Hi,

I am trying to move my home folder so that I can upgrade to the new version of Ubuntu.  I do not understand the instructions regarding "Setup Fstab".  Here is my current configuration.  I've run sudo apt-get clean and still do not have enough space.  I have  been trying to follow the instructions in the above link but I am stuck  on the Setup Fstab step.  This step requires that you add the following  lines however I do not understand exactly what is required.  #  (identifier) (location, eg sda5) (format, eg ext 3 or 4) (some settings)   UUID=??????? /media/home ext 3 nodev, nosuid 0 2.  This is my  information /dev/sda1: UUID="3536ac82-a5a0-42ec-96f3-4861cc4dff44"  TYPE="ext4"  
/dev/sdb1: LABEL="KINGSTON" UUID="FE2E-8B8B" TYPE="vfat"  
/dev/sda5: UUID="7f2a3e16-6d15-452a-a1cf-7eb8e72c12c3" TYPE="ext4" , I  just don't know how to format it correctly for the Fstab.  Thanks again  in advance, Scott  I am also including a screen shot.

---

### Post by jrog on 2012-10-30
The link that you refer to in your post is missing, so it's hard to tell what instructions you're trying to follow. (You also mention Scott; did you mean for this to be a PM rather than a post?)

Anyway, if you can try again to post the link to the instructions you're trying to follow, we may be able to help you. It's not entirely clear what you're trying to do, as it is.

---

### Post by oldfred on 2012-10-30
I suggest these instructions.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But just to confuse things (but sometimes different instructions may make more sense.)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You have to format the unallocated space, probably to ext4 and then it will have a UUID you can use for mounting. Until the partition exists you cannot do much.

---

### Post by wsfield99 on 2012-10-30
Hi, thank you.  Here is the link: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by jrog on 2012-10-30
> **wsfield99 said:**
> Hi, thank you.  Here is the link: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
In your first post, the screenshot shows only two partitions, /dev/sda1 and /dev/sda2, and /dev/sda2 is an extended partition. That being so, it does not appear that you have actually set up any partitions for a separate home directory (/dev/sda1 is your root filesystem, and /dev/sda2 is an extended partition, so it cannot be formatted with any filesystem). That means you shouldn't yet be at the "Setup Fstab" step in the instructions to which you just linked, because you haven't yet succeeded at the "Setup Partitions" step. Please read the guide on partitioning to which those instructions link, available here: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by funicorn on 2012-10-30
The instructions mentioned fail to give the most convenient way to do this. They lack of simplicity and logic consistence, use too many syntaxes, and are easily confusing.

You should start with making a new ext3/4 partition on the unallocated disk space inside the extended partition sda2, with 'gparted'.

 Let's call the newly created partition **"HOME partition",** with device map file /dev/sda5, and the device map file of your "**root partition"** is /dev/sda1. Correct the NUMBERS to the realistic situation. 
What need done are simply copy data from path /home of the **root partition** to the **HOME partition** and create new mount point for it in /etc/fstab.


[LIST]
[*] **Step 1**. Mount **HOME partition** /dev/sda5 to /mnt
[/LIST]
 ```
sudo mount /dev/sda5 /mnt
```
[LIST]
[*] **Step 2**.: Copy all data from /home to /mnt, with all permission bits, links, anything preserved
[/LIST]
 ```
 sudo rsync -av /home/* /mnt
```keep an eye on it and see if there is any error during  synchronization.  If not,

[LIST]
[*] **Step 3**. Bind mount the **HOME partition** to mount point /home
[/LIST]
 ```
sudo mount -B /mnt /home
```Logout then re-login. Continue to use your desktop until you are sure  there's nothing wrong. Then

[LIST]
[*] **Step 4**. Add the **HOME partition** mount point to /etc/fstab
[/LIST]
 **Note: change "ext4" to "ext3" if the HOME partition is formatted as ext3.**
```

UUID=`sudo blkid /dev/sda5 |awk '{print $2}' |sed 's/"//g'`; echo -e "$UUID \t /home \t ext4 \t defaults \t 0 \t 2" | sudo tee -a /etc/fstab

```You may want to open /etc/fstab to make sure if everything looks right.
```
cat /etc/fstab
```
[LIST]
[*]**Step 5**. Reboot your computer
[/LIST]

[LIST]
[*]**Step 6**. Continue to run the system until your are totally sure there's nothing wrong. Then [SIZE=2]boot from Ubuntu livecd[/SIZE] and mount your **root** partition (boot into the single user mode is another option), then delete /home/*
[/LIST]
          (DO** [COLOR=Red]NOT[/COLOR] **mount the **HOME** partition)

```

# In livecd
sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/home/*

```
Reboot. Now you have extra space in the **root** partition to accomplish the distribution upgrade.

Note: Although the above work can be done without rebooting and one only needs to change the system runlevel from 2 to 1 using 'telinit' or 'halt' to complete the data transfer and mount/remount job, it's is recommended to reboot one or two times and make sure the desktop runs fine  for non experienced users. It's in this sense called an instruction.

---

