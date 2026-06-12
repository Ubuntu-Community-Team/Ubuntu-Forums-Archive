---
title: "No Vista Boot Option"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by joseduddy on 2008-12-02
Hello all
     Just performed an install of Ubunto. Used Acronis Disk Director first and set up a partition E. drive next to my Windows Vista Ultimate drive c. Everything went smooth except now when I boot my computer there is no option to boot vista. I think when I did the install I may have click "Guided Use entire disk"   and not   "Guided use the largest continuos free space"  There is no option on boot to select Vista. Can some one share some help please.

Thanks Jose;)

---

### Post by Pumalite on 2008-12-02
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by joseduddy on 2008-12-02
Ok i'am back running on the live CD

---

### Post by nvance on 2008-12-02
Good, now go to the terminal and enter 'sudo fdisk -lu' (without the quote),as Pumalite stated above, then post the results here for assistance.

---

### Post by joseduddy on 2008-12-02
Ok Iam stupid .......where the teminal

sorry found it

---

### Post by Pumalite on 2008-12-02
Applications>Accessories>Terminal

---

### Post by joseduddy on 2008-12-02
I don't think it looks good but here it is

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3148618a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476311184   238155561   83  Linux
/dev/sda2       476311185   488392064     6040440    5  Extended
/dev/sda5       476311248   488392064     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Titan8990 on 2008-12-02
Looks like you completely deleted Windows...

---

### Post by joseduddy on 2008-12-02
I partitioned 80 gigs before I did the install.

---

### Post by Titan8990 on 2008-12-02
Are you sure you didn't select the automatic partitioning to use the whole drive? That is what appears to have happened.

---

### Post by joseduddy on 2008-12-02
Just performed an install of Ubunto. Used Acronis Disk Director first and set up a partition E. drive next to my Windows Vista Ultimate drive c. Everything went smooth except now when I boot my computer there is no option to boot vista. I think when I did the install I may have click "Guided Use entire disk" and not "Guided use the largest continuos free space" There is no option on boot to select Vista. Can some one share some help please.



Looks like the option I took erased the hd and did a new install?

---

### Post by nvance on 2008-12-02
> **joseduddy said:**
>  I think when I did the install I may have click "Guided Use entire disk"   and not   "Guided use the largest continuos free space"  

It appears that you did accidently select the "Use entire disk" option therefore wiping out Windows and any data.

Sorry about that, but hopefully you have a Windows install disk if you want to re-install it.

---

### Post by joseduddy on 2008-12-02
yes i do. Can I perform the same operation ..Partition and add vista back on???

---

### Post by Titan8990 on 2008-12-02
Or a backup from Acronis.

IMO, the automatic partitioning should be removed. If people can't partition a drive then they need to learn prior to installing an OS. It's removal would prevent users like the OP from accidentally deleting their entire drive...


Edit: Always, just do you partitions from inside the installer. Start fresh. Install Windows, only using the space that you need. Then when you install Ubuntu, select "manual". Use your remaining space for a 2GB swap and EXT3 for your main filesystem.

---

### Post by nvance on 2008-12-02
Yes, you can re-partition and re-install windows, but I am not sure if Grub will pick up the Windows install.  You might have to add the command into the menu.lst for Grub to pick up the Windows boot option.  You might be able to search the forum for "windows reinstall" or something like that.

Does anyone else have an idea of reinstalling Windows after installing Ubuntu?

---

### Post by joseduddy on 2008-12-02
I'am trying to learn, and the loss od the Vista Install is not a big deal to me. I will simply reformat the drive and re-install Vista. No big deal. Thanks for all the help guys.It looks like you need to have a full vista install before you can run a ubuntu install. No prob Thanks again. 

P.S. Life is learning:KS:KS:KS

---

### Post by Pumalite on 2008-12-02
Next time you install Vista; allocate space for Ubuntu with the Vista partitioner first. Do not use other partitioners.

---

### Post by joseduddy on 2008-12-02
so you mean during setup insted of normal install create a partition of 80 gigs or so for Ubunto ?

---

### Post by Titan8990 on 2008-12-02
Yes, he is saying when you install Vista leave some unpartitioned space. Manually use the unpartitioned space during the ubuntu installation. Thinking again you may have to remove the partitions via gparted from the Ubuntu live CD. This is because Vista usually won't even display a EXT3 partition as existing (they are mad that it is superior to NTFS, but then again we should all be using XFS...)

---

### Post by joseduddy on 2008-12-02
Off I go
Hehe having fun

---

