---
title: "upgrade directly from 9.04 to 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-09-05
Hi for some reason I did not upgrade my system when the 9.10 version was released but I'd like to do it now. The update manager gives me 9.10 as the only available option...this would mean I have to upgrade my system twice...is there any way to upgrade directly to 10.4 without passing through 9.10?

---

### Post by DandyDon on 2010-09-05
No. Only way to skip is a new install via a CD, on an empty partition, hard drive, or USB Flash drive. The flash drive must be at least 8 GIG.

The reason for this is an update only installs new code and removes obsolete code. The update must have old some code to work, ie, OpenOffice, etc. There is probably some base code in 9.10 that stays the same in 10.04.

---

### Post by abelito8 on 2010-09-05
ok but in that case all the additional software I have installed (from VLC to Skype) is gone and I have to spend an afternoon resetting my computer right?

Ok, I will go through 9.10 then, thank you

---

### Post by tommcd on 2010-09-05
To do a dist-upgrade from 9.04 to 10.04 you must upgrade in sequence. That is: 9.04 > 9.10 >10.04.
You can also do a dist-upgrade from one Long Term Support (LTS) version to the next. For example, you can do a dist-upgrade from 8.04 > 10.04.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
The easiest, fastest, and safest way to upgrade from 9.04 to 10.04 would be to just do a *clean install* of 10.04. A clean install is the best way to avoid problems with upgrades. This is especially true if you have any ppa repos or other 3rd party repos in your sources.list.

---

### Post by tommcd on 2010-09-05
> **abelito8 said:**
> ok but in that case all the additional software I have installed (from VLC to Skype) is gone and I have to spend an afternoon resetting my computer right?

Understand that reinstalling Ubuntu and all of your programs becomes easier the more experience you have with it. I can do a clean install of Ubuntu, get all the updates, and reinstall all of my software and settings in about 90 minutes or less.  Usually, it is less than that.
You can of course choose to go from 9.04 > 9.10 > 10.04 if you wish.

---

### Post by abelito8 on 2010-09-05
Right, I was doing it for a friend yesterday and it's taking every time less....still, because I did it yesterday I was hoping I would not have to do it again soon

but can you keep your data while doing a reinstall? (of course I have them backed up)
By simply not touching the /home partition while repartitioning the computer?

---

### Post by tommcd on 2010-09-06
> **abelito8 said:**
> 
but can you keep your data while doing a reinstall? (of course I have them backed up)
By simply not touching the /home partition while repartitioning the computer?
If you have your /home directory and all of the data within it on an *separate partition* on your hard drive, then your data will be safe when you reinstall Ubuntu. If your home directory is on the *same partition* as Ubuntu's root partition, then all of your data will need to be backed up since reinstalling Ubuntu to it's current root partition will reformat the root partition (which includes the home directory in this case).

If /home is indeed on a separate partition, then just choose manual partitioning during the install.
 Elect to format and install Ubuntu to the root partition you have now.
Then select the /home partition. Choose to mount it as what ever file system it currently uses. And choose to mount it to mount point /home.
Most importantly, choose *do not format this partition* for your home partition if you wish to retain the data.

Write back if you need more help with this.
It is always wise to have your data backed up. Kudos to you for backing up your stuff to be safe!

---

### Post by abelito8 on 2010-09-08
Thank you, this is what I ultimately did but there are two things I am not sure I understood. 
my home partition was say sda8, I had some space before and after it. I formatted everything else and I partitioned the 160 GB this way

first 12 GB /
1,2 GB swap
from Swap until my sda8 /home

I did not touch the sda8 nor ubuntu asked me to rename it

I had some bulk space (8GB) after the sda8 and I also called it /home but the system warned me I could not use the same name so I renamed it /home/usr

now I have the following things

sda8 is by default unmounted, I can access it but first I have to mount it, so in the end I moved all the information to the new /home and kept sda8 as extra space for data in case

the 8GB I formatted as /home/usr I have no idea where they are or how to access it...well to make it easier this is the result of df -h typed on a terminal

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  1.1G   10G  10% /
none                  999M  328K  998M   1% /dev
none                 1003M   13M  990M   2% /dev/shm
none                 1003M  128K 1003M   1% /var/run
none                 1003M  4.0K 1003M   1% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
none                   12G  1.1G   10G  10% /var/lib/ureadahead/debugfs
/dev/sda7              80G   13G   64G  17% /home
/dev/sda8             6.4G  2.4G  3.8G  39% /usr
/dev/sda5              49G   24G   22G  53% /media/3a4f3a6e-1c49-4a2a-b1e9-d9d7155e9f18


Did I do anything wrong (or not properly?)

---

### Post by tommcd on 2010-09-08
> **abelito8 said:**
> 
Did I do anything wrong (or not properly?)
You don't need a separate /usr partition. Just do it the simple way with 3 partitions: root, swap, and the rest for /home.

---

### Post by abelito8 on 2010-09-09
My old /home partition was in the middle of the disk

............ (120 GB empty)..............................sda8 (52 GB my old /home)..............(8GB empty)

so I did

/ ........swap ........./home .......but I still had sda8 after /home and 8GB free after sda8

the only way would have been to move sda8 to the end of the disk but I did not know what to do, otherwise I tried to name also the final 8GB as /home but I was not allowed

or I should have backed up, deleted everything and then copied back everything to the /home...is this you were suggesting?

---

