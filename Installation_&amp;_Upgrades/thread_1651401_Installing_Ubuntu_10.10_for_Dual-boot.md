---
title: "Installing Ubuntu 10.10 for Dual-boot"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by rexcfnghk on 2010-12-23
Hi all,

I am installing Ubuntu today encountering some problems and hope you guys could help. My current Windows 7 x64 partitions are C, D, E and G (I have one hard disk drive only), which G is left blank for Ubuntu.

I started the Wubi installer and installed it to G and then rebooted to Ubuntu 10.10. The system asked me to set up a manual partition table for Ubuntu, what should I do? I saw some threads in the forum and said I should simply install to G, which is dev/sda5, choose ext3 and set / as mount point, but the installer prompted me that it needs swap space, is that an error?

Thanks!

---

### Post by theasprint on 2010-12-23
Hi,

About the request for swap space, its not an error. Relax.

However I think you should Try Ubuntu without installing first.
If there are no problems, then you can continue.

The Ubuntu 10.10 interface is much more different that what it used to be.
So if it tells you to set a manual partition table then you can set it.

But during setting a manual partition table, you should set 2 partitions.
That means your G drive would be further split into 2 partitions.
You would need to have a / mount point and a swap partition.

Here is a guide on how to set up a manual partition table:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Here is another guide about dual-booting. There are partition tutorials inside, so lookout.
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

In fact your installation may be similar to the second guide. Just lookout at how the user made his partitions. In the guide there are 3 partitions, one / partition, one /home partition and one swap partition.

You can also follow him to make a /home partition if you want. But not making it also doesn't matter.
The point about making a /home partition is that all the data would go there (/home), instead of the / partition, so that you can just separate data and program files easily and that they don't affect one another.

I believe there would be a user *amjjawad *posting soon to help you.
You should wait for his post, but Try Ubuntu first to ensure that Ubuntu is compatible with your PC.

---

### Post by rexcfnghk on 2010-12-23
But I cannot perform new partition operation on GParted! I have /dev/sda1,3 and 5 for my C, D, E drives but my /dev/sda2 is an extended partition which /dev/sda5 is the logical extension under it. It does not allow me to create new partitions for /swap, /home and root partitions.

What should I do?

Thanks for your help.

---

### Post by rexcfnghk on 2010-12-23
Anyone?

---

### Post by miegiel on 2010-12-23
> **rexcfnghk said:**
> But I cannot perform new partition operation on GParted! I have /dev/sda1,3 and 5 for my C, D, E drives but my /dev/sda2 is an extended partition which /dev/sda5 is the logical extension under it. It does not allow me to create new partitions for /swap, /home and root partitions.

What should I do?

Thanks for your help.

For inspiration, my partition scheme:
```
user@machine:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11b42f68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52428800    7  HPFS/NTFS            [COLOR="Blue"]windows 7[/COLOR]
/dev/sda2            6528        7833    10485760   1b  Hidden W95 FAT32     [COLOR="Blue"]windows install (I have no install CD for my laptop)[/COLOR]
/dev/sda3            7833       38911   249633793    5  Extended             [COLOR="Blue"]extended partition for all my linux partitions[/COLOR]
/dev/sda4           38911       38914       20824   ef  EFI (FAT-12/16/32)   [COLOR="Blue"]yet another windows partition, not sure what it's for[/COLOR]
/dev/sda5            7833        9922    16777216   83  Linux                [COLOR="Blue"]logical partition inside /dev/sda3: default linux installation[/COLOR]
/dev/sda6            9922       10183     2097152   82  Linux swap / Solaris [COLOR="Blue"]logical partition inside /dev/sda3: swap partition[/COLOR]
/dev/sda7           10183       12272    16777216   83  Linux                [COLOR="Blue"]logical partition inside /dev/sda3: experimental linux installation[/COLOR]
/dev/sda8           12272       38911   213979136   83  Linux                [COLOR="Blue"]logical partition inside /dev/sda3: separate home partition[/COLOR]
```
While setting up your partitions you need to keep in mind that windows can't handle more than 4 primary partitions (including the extended partition). Having more than 4 logical partitions in your extended partition also used to confuse windows, but this might have been resolved.

When you make the partitions to install ubuntu you will need to make at least 2. 1 for ubuntu and 1 for the swap partition. Make the swap partition at least as large as your RAM, or you won't be able to hibernate. You can leave the partitions you prepared for ubuntu unformated. The ubuntu installer will format them for you.

However it's even easier to make a empty unpartitioned space on your disk. During the installation you can choose to install ubuntu in the empty space on your disk.

---

### Post by rexcfnghk on 2010-12-23
OK it is getting really frustrating. Now I have a total of five partitions: C for Windows 7 x64 , D & E for my data, G (40GB) for Linux and H (10GB) for Linux swap.

I installed Ubuntu 10.10 using Wubi on G as usual, make G's (dev/sda5) mount point be the /root and H (dev/sda6) as linux swap space. All is well...until

I GOT ANOTHER ERROR:
"...the following mount points could not be unmounted: /isodevice"

There is an option for the installer to try unmount it and I clicked forward but the computer hanged...please help me...

---

### Post by miegiel on 2010-12-23
> **rexcfnghk said:**
> OK it is getting really frustrating. Now I have a total of five partitions: C for Windows 7 x64 , D & E for my data, G (40GB) for Linux and H (10GB) for Linux swap.

I installed Ubuntu 10.10 using Wubi on G as usual, make G's (dev/sda5) mount point be the /root and H (dev/sda6) as linux swap space. All is well...until

I GOT ANOTHER ERROR:
"...the following mount points could not be unmounted: /isodevice"

There is an option for the installer to try unmount it and I clicked forward but the computer hanged...please help me...

The */isodevice* is probably your CD.

Oops, I missed the part where you said you were installing wubi. If you're just test driving ubuntu wubi is fine, but if you really want to use ubuntu for a longer time you should do a normal installation. Wubi often breaks when it's updated.

10GB is very large for a swap file (unless you have 10GB memory in your machine).

Also, for your own comfort, consider what I said in my previous post:
> **miegiel said:**
> ... it's even easier to make a empty unpartitioned space on your disk. During the installation you can choose to install ubuntu in the empty space on your disk.
The ubuntu installer will figure out how to use the unpartitioned space on your disk for you.

---

### Post by rexcfnghk on 2010-12-23
> **miegiel said:**
> The */isodevice* is probably your CD.

Oops, I missed the part where you said you were installing wubi. If you're just test driving ubuntu wubi is fine, but if you really want to use ubuntu for a longer time you should do a normal installation. Wubi often breaks when it's updated.

10GB is very large for a swap file (unless you have 10GB memory in your machine).

Also, for your own comfort, consider what I said in my previous post:

The ubuntu installer will figure out how to use the unpartitioned space on your disk for you.
I used Daemon Tools to mount the Ubuntu 10.10 x64 image to a virtual disk drive. Do you mean I should unmount it before entering Ubuntu for installation?

I used Wubi because things got out of hands when I installed for the Live CD, which caused me a lot of trouble since I am new to Linux. I cannot boot into Windows when I installed Ubuntu 10.10 through USB stick just a couple of days ago and I have absolutely no idea what the others are talking about when I googled for answers...

May I ask what is your recommendation to the size of a swap file? 2GB?

Thanks again for the help.

---

### Post by kansasnoob on 2010-12-23
I think most people are not noticing that the OP is using Wubi, or so it appears:

> **rexcfnghk said:**
> Hi all,

I am installing Ubuntu today encountering some problems and hope you guys could help. My current Windows 7 x64 partitions are C, D, E and G (I have one hard disk drive only), which G is left blank for Ubuntu.

**[COLOR="Red"]I started the Wubi installer[/COLOR]** and installed it to G and then rebooted to Ubuntu 10.10. The system asked me to set up a manual partition table for Ubuntu, what should I do? I saw some threads in the forum and said I should simply install to G, which is dev/sda5, choose ext3 and set / as mount point, but the installer prompted me that it needs swap space, is that an error?

Thanks!

---

### Post by theasprint on 2010-12-23
Hi,

Sorry if I end up confusing you.
Yes, agree with miegiel about the empty unpartitioned space.
It is in fact easier to let Ubuntu decide about its partitions since you are a new user.

And since you mentioned about the problems in post #3, I think its best you cancel the installation first (if you can). Hope its not too late.

To miegiel: Can Wubi installation be installed on unallocated space?

---

### Post by kansasnoob on 2010-12-23
I don't know much about Wubi but this is beginning to sound almost scary!

I'd wait for some specific Wubi help ;)

---

### Post by theasprint on 2010-12-23
Hi,

I do not recommend mounting an OS image and trying to install it.
It is just not right. Installation of an OS should be pure contact with the PC, not a virtualized one.

If you can, cancel everything for now. 

Can you tell us what is your condition now? About partitions etc...

I think its best after you have cancelled, then you merge back the G: and H: together. Delete these 2 partitions under Disk Management in Windows and create a new partition with the empty space. 
So you should end up at the first place like in your first post.

---

### Post by rexcfnghk on 2010-12-23
> **theasprint said:**
> Hi,

Sorry if I end up confusing you.
Yes, agree with miegiel about the empty unpartitioned space.
It is in fact easier to let Ubuntu decide about its partitions since you are a new user.

And since you mentioned about the problems in post #3, I think its best you cancel the installation first (if you can). Hope its not too late.

[COLOR=Red]**To miegiel: Can Wubi installation be installed on unallocated space?**[/COLOR]
Yeah I think that's the main problem. If I unpartitioned my partitions, I don't think I can install Wubi :mad:

---

### Post by rexcfnghk on 2010-12-23
> **theasprint said:**
> Hi,

I do not recommend mounting an OS image and trying to install it.
It is just not right. Installation of an OS should be pure contact with the PC, not a virtualized one.

If you can, cancel everything for now. 

Can you tell us what is your condition now? About partitions etc...

I think its best after you have cancelled, then you merge back the G: and H: together. Delete these 2 partitions under Disk Management in Windows and create a new partition with the empty space. 
So you should end up at the first place like in your first post.
My system is perfectly normal now, considering the fact I had installed and uninstalled Unbuntu numerous times. I have now C for Windows, D & E for my data, G & H for Linux. Got really confused what to do next lol.

---

### Post by kansasnoob on 2010-12-23
I notice that bcbc is about this AM and (s)he's as knowledgable as anyone I know about Wubi.

So, I suggest going to your original post, clicking on edit, then on "go advanced". I believe that will let you change the title of your thread. so just add [Wubi] to the beginning like this:

[Wubi]Installing Ubuntu 10.10 for Dual-boot

Then if bcbc sees this you'll get some expert help :D

---

### Post by rexcfnghk on 2010-12-23
Thanks. Done.

---

### Post by rexcfnghk on 2010-12-23
Please help....

---

### Post by bcbc on 2010-12-24
Hey I arrived :) Must have missed this thread.

I'm confused too. You don't need to partition to install Wubi. Also, when you install with Wubi you don't get prompted to choose the partition for / and certainly not swap (wubi installs to files, not partitions).

My advice is - if you have separate partitions, then don't use Wubi. Wubi is more for people who don't want to or know how to partition. There've been a lot of problems lately with wubi anyway... so I'd just do a normal install.

If you really want to install with Wubi don't mount the .iso and install from it. Just take the wubi.exe from the .iso and place it and the .iso in the same folder and run it from there. That tends to work the best.

Anyway - I'll follow the thread and help where I can whatever you decide to do.

---

### Post by Quackers on 2010-12-24
Just one word of caution here. Please check how many Primary partitions you have! 4 is the maximum for any one hard drive. If you have 5 your partitions may have changed to Dynamic. This is a big problem with regard to installing another OS (without wubi).

---

