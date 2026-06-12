---
title: "Given up - 7.04 install does not see my partitions"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by riknos on 2007-08-14
I've not been able to install Ubunu and have given up for time being. None of the install programs - micro, alternate or full gui 7.04 for AMD downloaded in last couple of days - finds my existing partitions. 

Partitioner - even using Manual option - just shows disks /sda and /sdb and refuses to do anything but  wipe disk 1 or disk 2 which I am not too keen on! Especially as I had created partitions especially for Ubuntu. I have two sata 250gb disks which have plenty of free space. I have xp and suse on disk 1 already working fine and backups on disk2.

What next? can anyone help me avoid further frustration? Ubuntu has not got off to a good start for me!

---

### Post by heimo on 2007-08-14
> **riknos said:**
> What next? can anyone help me avoid further frustration? Ubuntu has not got off to a good start for me!

I'd try running in terminal: ```
sudo fdisk -l
```
It should list your partitions. Then consider removing the empty ones you already created for Ubuntu and running installer again.

---

### Post by aquavitae on 2007-08-14
Its highly unlikely that ubuntu can't see the partitions - more likely it doesn't show them by default for some reason.  What do you get if you boot off the live cd, open a terminal and type ```
fdisk -l
```(Thats an ell, not a one)
This should show all disks, and what partitions are on them.

---

### Post by riknos on 2007-08-14
Thanks for quick replies. 
Yes, indeed, using sudo fdik -l does show all the partitions correctly.
What next?

---

### Post by riknos on 2007-08-14
Well, I then checked out Gparted from Live CD and that shows 
/dev/sda unallocated 232.88 GiB
/dev/sdb unallocated 232.88 GiB .....

---

### Post by aquavitae on 2007-08-14
How do you want your disks to be partitioned after installing ubuntu?  The easiest would be to delete the partitions you created for ubuntu, and install ubuntu in the unallocated space (it will automatically create the necessary partitions).  But of course, first make sure its reporting the correct amount of space and in the right place.  Can you post the output of sudo fdisk -l?  It would help if we could see exacly what your setup is.

---

### Post by riknos on 2007-08-15
Sorry about delay but just managed to get the fdisk output and copy of Install Partitioning window onto usb drive so as to post them here:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3816    30651988+   7  HPFS/NTFS
/dev/sda2            3817       21049   138424072+   5  Extended
/dev/sda3           10344       12954    20972857+  83  Linux
/dev/sda4           12955       13216     2104515   82  Linux swap / Solaris
/dev/sda5            3817        6427    20972826    7  HPFS/NTFS
/dev/sda6            6428        8385    15727603+   7  HPFS/NTFS
/dev/sda7            8386       10343    15727603+   7  HPFS/NTFS
/dev/sda8           13217       21049    62918541    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3817    30660021    7  HPFS/NTFS
/dev/sdb2            3818       10344    52428127+   5  Extended
/dev/sdb5            3818        6428    20972826    7  HPFS/NTFS
/dev/sdb6            6429        8386    15727603+   7  HPFS/NTFS
/dev/sdb7            8387       10344    15727603+   7  HPFS/NTFS

Disk /dev/sdc: 1028 MB, 1028653056 bytes
16 heads, 32 sectors/track, 3924 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3924     1004528    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

I've attached .png file of Install Partitioning window.

---

### Post by riknos on 2007-08-15
I meant to say, I would like to install Ubuntu on disk 1 if possible. However, I have got 3 primary partitions of XP(1)and Suse (2 inc. swap) on disk 1 already even though lots of spare room.

---

### Post by aquavitae on 2007-08-15
Ok, there's something a bit odd (which might be the reason parted is having problems).  If you look at /dev/sdb, you'll see that the partitions are:

sdb1 (Primary)
sdb2 (Extended)
 - sdb5 (Logical)
 - sdb6 (Logical)
 - sdb7 (Logical)

This is normal, i.e. your drive can have up to four primary or extended partitions (in this case 2) which are numbered 1-4 (only sdb1 and sdb2 in this case) Numbering then starts from 5 for and logical partitions (so as not to confuse them with primary ones).  Now if you look at /dev/sda, you'll see this is not the case:

sda1 (Primary)
sda2 (Extended)
 - sda5 (Logical)
 - sda6 (Logical)
 - sda7 (Logical)
 - sda3 (Logical)
 - sda4 (Logical)
 - sda8 (Logical)
 
The order is also a bit perculiar.  I don't know how you got the numbering like this, or how you'd fix it, but I suspect its the problem.

First question - why do you need 9 NTFS partitions?  What I'd suggest is, backup all the stuff on /dev/sda, delete all the partitions on it. Create whatever NTFS partitions you need on it, leaving room for ubuntu, then install ubuntu and let it automatically partition the space you've left for it.  Btw, its also a good idea to install it on a separate drive from winXP.  What I do is unplug my xp drive, so I can be sure it will install on the right drive, then put it back in as slave.  This way I retain the windows boot loader, which otherwise might get overwritten by grub.

---

### Post by riknos on 2007-08-15
Thanks for getting back so quickly.

I agree the order of partitions does look strange. I'll spend some time working through this at my leisure following up as you suggest...

Yes, there are a lot of NTFS partitions - I use them for Apps, Video and Music plus backups of these! I should probably rationalise!

I think you have put your finger on the problem. However, looking at your suggestion of separate disks for XP and Ubuntu, I think, after all, the easiest solution for me is just to put Ubuntu on disk 2. Hopefully this will get me up and running.

Thanks again.

---

### Post by aquavitae on 2007-08-15
> **riknos said:**
> I think, after all, the easiest solution for me is just to put Ubuntu on disk 2. Hopefully this will get me up and running.
This should work, but you might still have problems reading /dev/sda from linux if you don't sort it out.
Good luck!

---

### Post by ashmew2 on 2007-08-15
Hi riknos and the others , I want to tell you that ive been having the same problem as riknos here. Gparted wasnt detecting my first 250 GB SATA HD (showing it as unallocated . Anyhow it was detecting the 2nd one flawlessly). I tried to find some solution and i did at last. There's this little program called testdisk (I read about it somewhere) which i used  , and it did everything. It made gparted see the disk partitions and stuff. What i did was , just find the setup to testdisk , here you go : [http://packages.ubuntu.com/feisty/admin/testdisk](http://packages.ubuntu.com/feisty/admin/testdisk)
Then install it (use the architecture which suits you , if you are unsure , just select i386) . Install the program using the deb file and once it is installed , open a terminal ,  maximize it  and put this in :

```
sudo testdisk
```

Then it will start and should show you both your hard drives (they showed up as /dev/sda and /dev/sdb in my case). Select the one you want and press enter (Proceed).
Select Intel. Press Enter.
Select Analyze. Press Enter.
Take a look around at whatever you see and Press enter again. 
Now at this screen , look for an option named "Write". Select it and press enter.

Do this for the second hard drive also (if u want).
Reboot your system.
Tell us if this fixed your problem !!!

I hope that helps you , or anyone else. Please let me know if this works though.

~Ashish

---

### Post by ashmew2 on 2007-08-16
It seems that this problem was being caused because of using "Partition Magic" in the past on your hard drive. Riknos , can u plz verify whether you also used this software or any other hard drive partitioning directly from windows ? 
thanks

---

### Post by jimoupas on 2007-10-15
> **ashmew2 said:**
> Hi riknos and the others , I want to tell you that ive been having the same problem as riknos here. Gparted wasnt detecting my first 250 GB SATA HD (showing it as unallocated . Anyhow it was detecting the 2nd one flawlessly). I tried to find some solution and i did at last. There's this little program called testdisk (I read about it somewhere) which i used  , and it did everything. It made gparted see the disk partitions and stuff. What i did was , just find the setup to testdisk , here you go : [http://packages.ubuntu.com/feisty/admin/testdisk](http://packages.ubuntu.com/feisty/admin/testdisk)
Then install it (use the architecture which suits you , if you are unsure , just select i386) . Install the program using the deb file and once it is installed , open a terminal ,  maximize it  and put this in :

```
sudo testdisk
```

Then it will start and should show you both your hard drives (they showed up as /dev/sda and /dev/sdb in my case). Select the one you want and press enter (Proceed).
Select Intel. Press Enter.
Select Analyze. Press Enter.
Take a look around at whatever you see and Press enter again. 
Now at this screen , look for an option named "Write". Select it and press enter.

Do this for the second hard drive also (if u want).
Reboot your system.
Tell us if this fixed your problem !!!

I hope that helps you , or anyone else. Please let me know if this works though.

~Ashish

Thanks a million !!! This one worked for me and im now able to see 2 old partitions in my windows xp installation , that stopped appearing before few weeks and i also finally installed Ubuntu 7.04 !!!




> **ashmew2 said:**
> It seems that this problem was being caused because of using "Partition Magic" in the past on your hard drive. Riknos , can u plz verify whether you also used this software or any other hard drive partitioning directly from windows ? 
thanks

I used Acronis Disk Director in the past , i dont know if its related.

---

