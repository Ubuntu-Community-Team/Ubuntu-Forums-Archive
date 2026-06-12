---
title: "Help!!!"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Godlikegarry on 2008-11-09
hi 

i have a problem i cleand my hard drive because a virus killed my XP i don't have a cd any more and ive only heard good things about ubuntu the cd works fine until making a partition a error comes up i zeroed the hard drive so its nice and clean 

i dont really know what to do if theres any more info you need plz tell me

thanks
         Garry:confused:

---

### Post by mjitkop on 2008-11-09
Hi, Garry.

Which option did you choose in the partition program? What is the error that you get?

---

### Post by Godlikegarry on 2008-11-09
yer hi ive tryed the all available one and custom 

swap 2000

/ 15000

/home           (left over space)

all was ext 3

my hard drive is ntfs when i go on to partition editor its say undefined? hope that helps

---

### Post by bulldog on 2008-11-09
Did you create the partitions yet?
If so,choose manual when you come to the partitioner.
Choose the 15000 and set it to format ext3,mountpoint / and set bootflag on
Choose 2000 mount it as swap format as swap
Choose the rest of the space,set it to format ext3 and mountpoint /home

Write changes to disk and proceed with the install.

If you get an error,you have to tell us what error you get,otherwise we can't help you.

HELP,isn't a good topic name,btw.
Try something like 'Partition problem' or 'Install problem'.

---

### Post by Sef on 2008-11-09
Go into the manual partition option.  Note: This will delete all of your partitions.  Then delete all the partitions.  Highlight them, then click delete.  Once they are all deleted, then do this to reformat the hard drive.

Root: Make it 8 - 10 GB,  Next, set it as / and make sure the boot option is enabled.  Ext3 is default file system. 

Swap: Make it 1 GB.  Change Ext3 to swap.

With what is remaining, set it as home.  Change / to /home.

---

### Post by Godlikegarry on 2008-11-09
thanks for the reply im going to give it another shot and i will write down 
the error message (if any)

it normal gets stuck on 5% when its reformatting so if it passes that i think im in the clear  :confused:

---

### Post by DrMelon on 2008-11-09
> **Godlikegarry said:**
> 
it normal gets stuck on 5% when its reformatting so if it passes that i think im in the clear  :confused:

It doesn't really get stuck, you know. Mine took ages at 5% too, you should just walk away and leave it to get on with it.

---

### Post by Godlikegarry on 2008-11-09
well that's the point
 when i normally get the error message 

right

dev/sda1 ext3 / 8998mb

dev/sda2 swap 1003mb

dev/sda5 ext3 /home 72314

used unknown? when ever that means?

here's the error message 

the creation of swap space in partition #2 Failed

?

---

### Post by bulldog on 2008-11-09
Did you set the swap to format as swap,not ext3?

---

### Post by Sef on 2008-11-09
> here's the error message 

the creation of swap space in partition #2 Failed

Applications > Accessories > Terminal

then paste or type in this code:

```
sudo fdisk -l
```small L   then paste the results here.

---

### Post by Godlikegarry on 2008-11-09
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad20c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1094     8787523+  83  Linux
/dev/sda2            1095        1216      979965   82  Linux swap / Solaris
/dev/sda3            1217       10011    70645837+   5  Extended
/dev/sda5            1217       10011    70645806   83  Linux
ubuntu@ubuntu:~$ 


thats from the last time i tried & failed lol

---

### Post by Godlikegarry on 2008-11-09
fixed Faulty sata2 lead sometimes it was not making a good enough connection well 1am to 4:30pm all because of a  1.99£ problem grrr cheers for you help guys :guitar:](*,)

---

