---
title: "partition problem..."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by mokkai on 2008-06-30
my os ubuntu-8.04

in my hard disk i have four partitions plus one unallocated partition(around 40GB). 

when i try to part that it is saying error is

>It is not possible to create more than 4 primary partitions

how can i make that unallocated part to store data in that.

thanks

---

### Post by logos34 on 2008-06-30
Because of the 4 primary partition limit, you're going to have to backup the contents of one of your partitions, delete it, then create a new, extended partition--a special type of primary--in it's place, which you can then subdivide into as many logical parititons as you want.  Copy data back to one of those.  You can also expand it to take up remaining unallocated space.  Gparted can do all of it.

You might want to post your fdisk output

sudo fdisk -l

indicating root and what's on the others

---

### Post by mokkai on 2008-06-30
thanks for your reply
i have a extented partition(/dev/sda4) which is also sub parted as /root ,/home/,/dev/sda5 ,/dev/sda6.

if i want to resize then i should unmount all parts
in /dev/sda4

now i am worrying to unmount only /root ,/home.
if i unmount /root ,/home ,then will it raise any problem ?

any idea ?

---

### Post by logos34 on 2008-06-30
> **mokkai said:**
> 
how to resize (increase) a extended partition  ?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by mokkai on 2008-06-30
thanks for your reply
i have a extented partition(/dev/sda4) which is also sub parted as /root ,/home/,/dev/sda5 ,/dev/sda6.

i have unallocation space available after that extended (/dev/sda4) partition .

if i want to resize then i should unmount all parts
in /dev/sda4

now i am worrying to unmount only /root ,/home.
if i unmount /root ,/home ,then will it raise any problem ?

any idea ?

---

### Post by vanadium on 2008-06-30
If you want specific advice, provide specific information: post the output of "sudo fdisk -l".

---

### Post by mokkai on 2008-06-30
sandg@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d5c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250         278      232942+  83  Linux
/dev/sda3             279        2768    20000925   83  Linux
/dev/sda4   *        2769       15759   104350207+   5  Extended
/dev/sda5            5175        8289    25021206   83  Linux
/dev/sda6            8290       15759    60002743+  83  Linux
/dev/sda7            2769        3390     4996152   83  Linux
/dev/sda8            3391        5174    14329948+  83  Linux

Partition table entries are not in disk order
sandg@ubuntu-desktop:~$

my /dev/sda8 in above list is unallocated (arround 40GB)

---

### Post by SkonesMickLoud on 2008-06-30
> **mokkai said:**
> 

<snip>

/dev/sda8            3391        5174    14329948+  83  Linux

<snip>

my /dev/sda8 in above list is unallocated (arround 40GB)

This is the partition you are trying to create?  It is already a partition, (/dev/sda8/)...

---

### Post by vanadium on 2008-06-30
From what I can infere, sd7 is a /(root), sd8 a /home, but then what are sda2 (a tiny Linux partition) and sda3, another primary linux partition?

sda8 is allocated, but perhaps you cannot access or mount it. There *is* an unallocated part on the disk, in between cilinders 15759 and 19457. The only way to reclaim that space in your current situation is to enlarge the extended partition sda4, which would then allow to increase your sda6.

Obviously, for manipulating the partitions, you must work from a live CD and unmount all partitions.

---

### Post by upchucky on 2008-06-30
knoppix and supergrub are great to have when you start the path you are on.

your live cd partimage works to do what you want. knoppix is a rescue life saver as it can fix windows drives and files too.

remember that when you make new partitions or add/remove drives, the order they are in changes and grub may not know where they are to mount them properly on a reboot

---

### Post by mokkai on 2008-07-01
> **SkonesMickLoud said:**
> This is the partition you are trying to create?  It is already a partition, (/dev/sda8/)...

here i attached my gparted image 
just see that...

thanks

---

### Post by logos34 on 2008-07-01
so what exactly are you trying to do again?  You want to make a data storage partition out of the unallocated space at the end (~28 GB)?  Or do you want to enlarge /home (sure needs it)?

---

### Post by mokkai on 2008-07-01
thanks to all your reply
here i have attached all gparted images 
see images(1,2)
now i can't store any files in unallocated (see last one) part
i want to make that to store data
when i try to make new partition
i got error (see image 3)

thanks

---

### Post by mokkai on 2008-07-01
> **logos34 said:**
> so what exactly are you trying to do again?  You want to make a data storage partition out of the unallocated space at the end (~28 GB)?  Or do you want to enlarge /home (sure needs it)?


yes ,i want to make a data storage partition out of the unallocated space at the end (~28 GB). that only i want

thanks

---

### Post by logos34 on 2008-07-01
you need to grow/enlarge sda4, the **extended partition**, first to take up the unallocated space.  Then create a new **logical** partition out of the empty space.

---

### Post by mokkai on 2008-07-01
> **logos34 said:**
> you need to grow/enlarge sda4, the **extended partition**, first to take up the unallocated space.  Then create a new **logical** partition out of the empty space.

yes thats correct

i should resize sda4 (it is a extended partition)

so first i should unmount all sub partition in /dev/sda4
then only i can resize it


just see the mount point in my first image
/dev/sda7  --> /root 
/dev/sda8  --> /home
/dev/sda5
/dev/sda6

i can unmount all of the above except /dev/sda8 (/home)

the error is "device is busy"

any help ?

---

### Post by logos34 on 2008-07-01
you must work from the live cd (*see post #9 and 10 above)

---

