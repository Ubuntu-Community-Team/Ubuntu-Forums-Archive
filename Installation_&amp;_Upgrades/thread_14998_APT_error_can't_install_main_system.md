---
title: "APT error: can't install main system"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by J-Doe on 2005-02-11
Okay, I tried to install Ubuntu from an official cd that Ubuntu team kindly sent me a while ago.
I previously had Suse linux installed on a ext 3 partition and swap partition also existed allready. From the ubuntu installation i chose that ext3 partiton as "/" and swap as swap. Everything seemed to go fine. Next stept was to install the actuall main system. Installation goes normally to 82% when it says something like "checking apt sources" and then it gives an error that the system is not found (package linux i386 or something). I had Ubuntu installed before and installation went smoothly, what is the problem now ?? ](*,) 

It also says somewhere during the installation that the partiton has old data that could screw up the installation but I have formatted that partiton several time using the ubuntu installation's own partition editor. I could use Partition magic in windows as I used to but for some reason it claims that my whole 40g harddrive is "bad". That harddrive includes windows installation, swap partiton and the linux partition so I cant really do anything about it cause it would screw up my windows... and btw windows's own diskmanager says that every partiton in that harddrive are okay.

For some reason ubuntu's installation managed to mess up with my bootloader and now I don't have any working boatloaders...

Pleasy help the helpless :)

---

### Post by az on 2005-02-11
I am not clear on a few things.

1- If your installation only got to 82 percent, Ubuntu never installed a bootloader.  So how did you screw up your bootloader?

2-  When you chose the ext3 partition for  "/". did you tell it to format the partition, or keep existing data.  You should tell it to format the partition.

3-  Is this partition big enough?   How big is it?

---

### Post by J-Doe on 2005-02-11
[QUOTE=azz]I am not clear on a few things.

1- If your installation only got to 82 percent, Ubuntu never installed a bootloader.  So how did you screw up your bootloader?

2-  When you chose the ext3 partition for  "/". did you tell it to format the partition, or keep existing data.  You should tell it to format the partition.

3-  Is this partition big enough?   How big is it?[/QUOTE]
 okay,
> 1- If your installation only got to 82 percent, Ubuntu never installed a bootloader. So how did you screw up your bootloader?
That's a mystery for me too. I never installed the bootloader but now when i boot up the computer the bootloader doesn't work, it opens GRUB in text mode, before the where graphical bootloader (which was installed by suse)

> 2- When you chose the ext3 partition for "/". did you tell it to format the partition, or keep existing data. You should tell it to format the partition.
I chose "format" and when that didn't work I even first deleted the whole partition and then created new.

> 3- Is this partition big enough? How big is it?
The size of the partition is little over 7G so it should be plenty...

And as I meantioned before, I had Ubuntu a while ago in that very same partition and everything worked fine...

---

### Post by J-Doe on 2005-02-11
I just can't understand this error... is it trying to download something fromthe web and can't find sources? cause network was configured just fine and automatically... And why is it trying to download anything, aren't all the needed packages on the cd?

---

### Post by J-Doe on 2005-02-12
Nobody capable of helping me?  :|  ](*,)

---

### Post by J-Doe on 2005-02-12
Okay, I got a different error this time. I tried to install the system with downloaded image cd this time (which is the cd I installed the system succesfully last time). With this cd I got up to 19% and then it gave this error: Can't install base system: "the debootstrap program exited with an error (return value 1).

So anyone know what that error is about?

---

### Post by dewey on 2005-02-12
Try wiping the partitions you plan on using for ubuntu, through another linux live cd.
Then use fdisk to verify that the partition table is correct, if it is, write changes, and try to reinstall Ubuntu.

I had alot of problems with the built in Ubuntu partitioner, like it dropped empty space sometimes if I made a mistake and tried to "undo" the partition change.

Also, when it installed GRUB, it didn't find my Windows2k NTFS partition as a boot option, so I had to manually edit the menu.list file, to add it in.

---

