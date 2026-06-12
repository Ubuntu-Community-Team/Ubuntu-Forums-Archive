---
title: "Clean Ubuntu install"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by andysdp on 2005-12-04
I have just installed Ubuntu on a machine that has Suse already installed. All went well, (except choosing the correct screen resolution), and I basically accepted all the defaults. I know have a dual booting machine, which is not what I really wanted. I would like to have over written the suse installation as it it is no longer required.  I have decided to re-install, but it appears from the "help on partitioning" that the installer doesn't allow you to install over another linux system.

Can anyone advise me on formatting the HD before installing again. I could use fdisk or a windows installer to wipe the disk first, but this doesn't seem in the right spirit of things!!  Surely there is a linux solution?

Also, I set up the suse installation as a software RAID across 2 80Gb HDD, so would like to wipe both.

Thanks 

Andy

---

### Post by bwog on 2005-12-04
You can use the install disk. At partitioning choose manual partitioning. Select a partition to delete it, or format it. 

(you can also use gparted from the live cd, but the above is really simplest method)

When you cant figure it out, come back here for more help. Good luck.

---

### Post by andysdp on 2005-12-04
Thanks - will give it a try.

---

### Post by andysdp on 2005-12-04
Thanks Bwog

New clean install - suse gone.

Cheers

Andy

---

### Post by rajan on 2005-12-04
i'm assuming this is a reliable way to clean install any system? i'm having trouble getting a clean install over my previous version of ubuntu. i'm installing the same exact OS again, but i've made a lot of mistakes on the installation i have running now and i want to start fresh. 

when i boot the system through the cdrom drive, i get to the first page of installation where it asks me to choose my OS version (server or normal). i can't type anything here, nor can i hit enter to continue on the normal installation. do you guys know how i can erase the partition from this step? i'm using the same disk and it's not damaged or anything. 

thanks in advance

raj

---

### Post by bwog on 2005-12-04
If you want to erase a partition and cant use the install disk you may try gparted on the live CD. Does this answer your question?

---

### Post by rajan on 2005-12-06
i tried this but then i realized i don't have CD burning software that i'm aware of. i hope i don't get death threats for admitting this, but i used an M$ disc to erase the install i had previously. don't worry -- i immediately reinstalled ubuntu after it erased the partitioning information. i was quite worried that i wouldn't be able to get back to linux for some odd reason. now i can go back to using my M$ disc for a coaster. 

does anyone know what a LVM drive is? there were a few options for the type of partitioning i wanted to create and i chose the one that sounded the coolest. honestly. it would be nice to know what that means now that i have to live with it. thanks in advance. 


rajan

---

### Post by Taino on 2005-12-06
Do you have the Ubuntu CD set? the live and the install CD?

If so.. you can boot the live CD and open a Terminal window,

then type, sudo su
then type, cfdisk

and you can access your partitions and make changes.

as far as formatting goes,  during the normal install process (with the install CD) when you reach the partitioner stage and have completed your partitioning and submit the final changes, the installer will automatically format any partitions it creates for Linux and Swap right after making them, But! only if (you selected them to be formatted) during that partitioner stage of the install.

While in the partitioner stage of the (install CD) select a partition and hit enter then a number of options are available, one of which is to install over an exsisting partition and its data, or reformat that partition. That is the option you want to change to reformat and it will be done when you complete your partition changes and submit them to continue the install.

hope that helps :)

---

### Post by kosmic on 2005-12-06
LVM is Logical Volume Manager, and is one of the best ways of partitionig drives for linux :)
 
Have a look at : [http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")

---

### Post by bwog on 2005-12-06
**@rajan:** Lets try something else if you havent got the live CD. You say you have trouble with a clean install over a previous installation.

Try to install again, when you arrive at partitioning, you select the partitions one at a time. You have made these partitions before, and now you have to mount them.

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.

home partition; use as ext3, mount point /home, format, etc.

This mounts and formats the partitions and the installation will start.

---

### Post by rajan on 2005-12-06
thanks for the help everyone. sorry for the confusion, but i meant to convey that i had sucessfully erased the partition and put 5.10 on once again. i'm not sure what was happening, but the install process just stopped before i could partition anything, or do anything at all. i could have run the live CD after booting from the HD, but i didn't have it (or anything else besides the install CD). i guess that'll be on my xmas list.

thanks for the info again. i haven't used it yet, but i'm sure i'll use it in the future.

---

