---
title: "Gparted not showing my logical drive"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by ubunt_user on 2008-08-30
Hello Everyone,

   I want to install Ubuntu 8.04 on my laptop which already has Vista.
It will be a dual boot configuration. I have gone through numerous guides which explain how to do this but I am facing one problem during the partitioning of my drive. I have a 250 gb HDD which I had partioned into 5 (logical) drives using Acronis Disk Director. The problem is during the partioning step , it shows me only 1 partion (250gb) to use or to choose the manual option. I opened GParted application using Live cd and attached is the screenshot that I get. I want to use one of my free logical partition for Ubuntu but I don's see any in the option.
Any help would be appreciated.
Thankyou.

---

### Post by gatenby_jp on 2008-08-30
Firstly Does Windows see the Partition Table created with Acronis? 

Generally you would be better off using gparted to create new partitions ... from within Windows you could have security software preventing a change to the partition table

---

### Post by ubunt_user on 2008-08-30
I am able to see and use all the partitions when I login through Vista.
Any idea how can I check this if Vista is preventing this or that data has been written to the partition table?

---

### Post by caljohnsmith on 2008-08-30
Because Windows Vista maintains its own partition table outside of the master boot record (MBR, it is best to use Vista's own partition editor to do any repartitioning. If you use anything else, including gparted, you often won't be able to boot back into Vista until you fix Vista's partition table from a recovery CD. So if you can, I would recommend booting into Vista and doing your partition changes in there. Then if you still have problems installing Ubuntu, we can go from there.

---

### Post by ubunt_user on 2008-08-30
So, isn't it possible to snych this 2 diff. partition table?
Also (sorry for asking this question), I am not clear when you say > booting into Vista and doing your partition changes in there.

Does it mean that I will have to reformat my existing partitions (created with Acronis) and apply changes with Vista's disk management because this would mean losing my existing data.

---

### Post by caljohnsmith on 2008-08-30
> **ubunt_user said:**
> So, isn't it possible to snych this 2 diff. partition table?
Also (sorry for asking this question), I am not clear when you say .

Does it mean that I will have to reformat my existing partitions (created with Acronis) and apply changes with Vista's disk management because this would mean losing my existing data.
If you can boot into Vista just fine and Vista sees all your new partitions, then no you don't need to use Vista's partitioner. :) Please boot back into the Ubuntu Live CD, and run the following in a terminal (Applications > Accessories > Terminal):
```
sudo testdisk

```
It will ask you to create a log, say yes, and then proceed through the prompts. It's reasonably easy to use, and have it do its analysis on your HDD partition table to see if it comes up with any errors. If it does, you can use it to correct them most of the time. If you have trouble with it, feel free to post back. Let us know what it says.

---

### Post by ubunt_user on 2008-08-30
caljohnsmith..I really appreciate your guidance.
I am unable to create a log file when I run testdisk. I guess because the system is running from CD its not allowing me to do so. But I have attached an initial screenshot that may help us to decide how do we have to proceed further as I am quiet new to this.
Thanks.

---

### Post by caljohnsmith on 2008-08-30
Unfortunately, just as I suspected, testdisk shows the error "Space conflict between the following two partitions"; it looks like sda2 and sda3 conflict because sda2 is within sda3, and yet sda2 is a primary partition. But that's why gparted doesn't show anything for your HDD. And unfortunately, I can't tell for sure just from that screen shot what exactly is going on, so please post the output of the following command:
```
sudo fdisk -l
```
That will also list your partitions, and if you can tell me which partition belongs to what OS (or what else the partition is used for), I might be able to help you figure out how to resolve your partition conflict.

---

### Post by ubunt_user on 2008-08-31
Here is the output of command :

The last 4 partions(sda5,6,7,8 ) were created by me (guesssing them from the size) If /sda1 is c: then its the main active primary partition. One more primary partition (not active primary) was already present (D drive) which has the recovery disk data. 
I have only Vista installed on the laptop and no other OS. The other primary parition is used by recovery disc software of HP.
I too can see the command showing me for table entries not in order. Looking head to solve this with everyone's help here.
Thankyou.

---

### Post by caljohnsmith on 2008-08-31
Ubunt_user, it looks like what happened is you had sda1 and sda2 originally on your HDD, where sda1 was the recovery partition and sda2 is your Vista partition. But somehow that Acronis software allowed you to create an extended partition that also used the space of sda2. So the bottom line is, you'll need to use Testdisk to rebuild your partition table so it just has sda1 and sda2, and not any of the new partitions you created.

Before you proceed, just as a safeguard, make a backup of your current master boot record (MBR), which contains your HDD's partition table. That way if you accidentally make things worse with testdisk, you can always get back to where you first started and start over. :)

Boot your Ubuntu Live CD, and do the following from a terminal (Applications > Accessories > Terminal):
```
cd ~/Desktop
sudo dd if=/dev/sda of=MBR.bin bs=512 count=1
```
That will save your MBR to a file "MBR.bin" on the desktop. Be sure to copy and save that file some place safe, like a USB flash drive or even a floppy.

Now when you run testdisk:```

sudo testdisk
```
Choose "create log", select HDD and then "proceed", "intel", "analyze", "proceed", yes to search for Vista partitions; once it lists your partitions, use arrow keys to select the partitions to delete sda3,4,5,6,7 and 8 ), hit "D" to mark them for deletion, then "enter" to proceed. I think you can take it from there. Let me know how it goes or if you need more details/info. :)

---

### Post by ubunt_user on 2008-08-31
I was thinking it as the last option for deleting all my partitions and redoing the work but since there was no other option , I went ahead with the procedure but from Windows as I am quite new to Linux hence didn't take any chances. Anyways I fired up Acronis, deleted all logical partitions , moved my Recovery partition and then re-created all.
Attached file contains output of 'testdisk' and 'fdisk -l'
Do you see any problem in fdisk because I guess testdisk o/p is fine.
I am able to boot into Vista as well. Should we still correct the problem with partitions?

---

### Post by caljohnsmith on 2008-08-31
That's great that testdisk isn't complaining any more about your partitions, ubunt_user. Looks like the problem is fixed now, so you should be able to go ahead and install Ubuntu. :)

---

