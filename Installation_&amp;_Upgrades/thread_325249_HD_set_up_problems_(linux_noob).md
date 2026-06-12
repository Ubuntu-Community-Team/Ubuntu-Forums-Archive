---
title: "HD set up problems (linux noob)"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by cloneofme on 2006-12-25
Hi im New to linux, here are my system specs just in case you need them:

Toshibe satilite A30 laptop
p4 2.4 , 512 ram, 30 gig HD, 32 meg intel graphics, cd rw/dvd rom drive, tvout card. 

Im trying to install Ubuntu over a broken windows xp pro partition ( infact the reason im moving to linux is because of the broken xp install) . I decided to use the alt install of ubuntu 6.10 ( due to the live cd hanging when i choose install).

I put the disk in and got into the install program and got as far as partition screen, I have chosen to install over xp, then the problem orrurs:  
when the installer starts i am on the 'confirm your partition changes' screen.

1)i begin the installer by choosing ' finish partitioning and write changes to disk'
i get an error message saying 'INPUT OUTPUT ERROR DURING READ ON /DEV/HDA'

2)after choosing ignore the installer starts working away and gets 61% through the action before i get another error message reading 'THE EXT3 FILE SYSTEM CREATION IN PARTITION #1 OF IDE1 MASTER (HDA) FAILED'

3)after choosing continue the installer again begins to work untill it gets to 61% then the  installer goes back to the partition confirmation screen.

It seems in caught in a loop. I think it may be due to bad sectors on my hard drive preventing the installer from installing ubuntu.

im sorry i couldn't provide screens for all this, but the computer seems to be a complete mess at the moment.

does anyone know what i should do to fix this? is there a program that i can run from boot to erase the entire hard drive and start from scratch?

Help anyone?!](*,)

---

### Post by bulldog on 2006-12-25
Yes there is,it's called gparted live cd , download and burn the ISO to a disk and boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by cloneofme on 2006-12-25
im downloading as we speak. so ill tell you how it goes. thanks for the help.

---

### Post by cloneofme on 2006-12-25
I loaded the disk but i dont know how to use it. how do i reformat the hard drive ?

---

### Post by bulldog on 2006-12-25
Boot from the cd you burned from it,ISO -->to Image so you get a boot able cd,follow the screen and you'll end up staring at your hard disk and the partitions on it.

Now you can wipe the whole disk if you want and create new partitions.
To format the whole disk you have to delete the partitions first,so you'll get a load of unallocated space.
Then right click the space and choose make new partition.
Partition it as you like to have it for use with ubuntu and what ever.

**EDIT**
You have a 30GB disk and no windows to install.
Create a 10GB partition and format it as ext3 [this will be the / root partition]
Create a 19GB partition and format it as ext3 [this will be your /home partition]
There should be some space left to make a 1G swap file if not make the 19GB smaller to achieve the 1Gb swap and format it as swap.
Exit the gparted cd and boot the ubuntu cd.

If you come to partitioning during install,choose manual partitioning [already done that] and mount the 10GB as /  (root) the 19GB as /home and the swap as swap
Set them to reformat with ext3 file format and the swap as swap and continue the install.

---

### Post by cloneofme on 2006-12-26
Alright, after a false start or two ive got the disks all partitioned as you mentioned, all left to do is to install ubuntu.

---

### Post by cloneofme on 2006-12-26
Past the partitioning stage, lets see if it takes.  fingers crossed

---

### Post by bulldog on 2006-12-26
And??

Should be working by now :D

---

### Post by cloneofme on 2006-12-27
unfortunatly ......no, im using g parted to scan and fix my hard drive. for some reason the install keeps hanging . i switched to the status screen ( alt + f4) and i saw it saying 'error , attempted to write' messages appearing multiple times. so im having Gparted check and fix all sectors. hopefully it will work.

---

