---
title: "Ubuntu, XP Dual Boot Error &quot;No root directory is specified.&quot; Help Please!!!"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Drag0n42 on 2010-02-22
:confused: Can someone please help me. I keep getting this error during the XP and Linux Ubuntu 9.10 dual boot installation. I have tried many things. Here is the current status of the installation:
      
     I have used wubi.exe to install the contents onto the drive. I did not install it onto my windows C: Drive because my Dad does not want to mess with it anymore. We have accidentally blown up Windows Twice trying to dual boot already. So we have another drive in our computer that we have it installed on so we don't mess with Windows. Ok so every time I boot up the computer it goes to the dual boot menu i choose Ubuntu and it tries to finish the installation. Whenever i get to the part where it says "Setting up Partitioner"(Or something like that.), a pop-up appears that says "No root directory is specified. Please correct this from the partitioning menu." I am pretty sure that the installer is supposed to make the partitions for you. It is impossible to close out the pop-up so i had to hard boot the computer. Then i went into the Linux Ubuntu Demo Mode. I used GPartEd to create the partitions manually. I came across the problem that there were too many partitions on the drive becuase we had some other partitions that we needed on that drive so I had to create an Extended Partition to house the Linux Partitions (For more information on my partition setup, see the bottom of the post.).  While still in the Linux Demo I had clicked on the "Install Ubuntu" icon. I got through the first 3 steps (The steps where it askes for Language, location, etc.) After that it went to some setup partitions menu but nothing was on it so i clicked on "Forward" and it said "No root directory is specified. Please correct this from the  partitioning menu." That is as far as I am right now.

P.S.: Sorry for the lengthy post, I needed to explain as much as possible so that it might be figured out.

List of all partitions on my Linux drive:
Backup (A backup of a friends computer files.) This and the next one are the important ones that is was talking about.
Ghost (A Ghost image of my computer.)\
Extended Partition:  20GB
         / 10GB (Linux Root Dir)
         /swap 2GB (swap partition)
         /home 8GB (home partition)
Z: 20GB (The partition that I installed wubu.exe on)

---

### Post by darkod on 2010-02-22
OK, first of all, calm down and stop trying everything because it might get messed up. :)

1. Decide whether you want to install wubi (sort of ubuntu installed inside windows), or proper ubuntu on its own partitions. You don't need both and from your post that's exactly what you are trying to do.

IMHO having a proper ubuntu is much better than wubi. If you want to try that, boot the live desktop again, and if you have only wubi on the Z: partition and no other data, delete that partition first. Then also delete the partition for ubuntu you created manually. If swap has keys symbol do right-click, Swapoff to remove them and then you can delete it.

That will create 20GB + 20GB unallocated space approx. Click the Install icon on the live desktop and start the install process again. In step 4 use Advanced Manual partitioning and create again /, /home and swap partitions with sizes that you want.

You got the "root directory not specified" message because you only created partition and then in the installer you didn't specified the mount points. That's why it's easier to do it as single step during the installer step 4. If you never assign the / mount point to the 10GB partition how does it know what to use it for? Linux does not use existing partitions unless specifically told so, and you have to specify the mount points.

Also, if you want separate /home partition you have to go the manual partitioning way. If not, using the guided method Use Largest Available free space will make default / + swap install into the unallocated space and save you the trouble of creating partitions yourself.

---

### Post by Drag0n42 on 2010-02-22
> **darkod said:**
> OK, first of all, calm down and stop trying everything because it might get messed up. :)

1. Decide whether you want to install wubi (sort of ubuntu installed inside windows), or proper ubuntu on its own partitions. You don't need both and from your post that's exactly what you are trying to do.

IMHO having a proper ubuntu is much better than wubi. If you want to try that, boot the live desktop again, and if you have only wubi on the Z: partition and no other data, delete that partition first. Then also delete the partition for ubuntu you created manually. If swap has keys symbol do right-click, Swapoff to remove them and then you can delete it.

That will create 20GB + 20GB unallocated space approx. Click the Install icon on the live desktop and start the install process again. In step 4 use Advanced Manual partitioning and create again /, /home and swap partitions with sizes that you want.

You got the "root directory not specified" message because you only created partition and then in the installer you didn't specified the mount points. That's why it's easier to do it as single step during the installer step 4. If you never assign the / mount point to the 10GB partition how does it know what to use it for? Linux does not use existing partitions unless specifically told so, and you have to specify the mount points.

Also, if you want separate /home partition you have to go the manual partitioning way. If not, using the guided method Use Largest Available free space will make default / + swap install into the unallocated space and save you the trouble of creating partitions yourself.

How do you set the mount point of the / partition.

---

### Post by darkod on 2010-02-22
Depending...
If the partition already exists, in the installer in step 4 you need to use Manual, then in the list of partitions click each one by one, then the button Change on the bottom of the screen. You will need to change from Not Used (which is the default) into:

For /
Filesystem ext4 (or ext3, depending which you want to use)
Mount point /
Format Yes

For /home
Filesystem ext4 (or what ever it was before if you are reinstalling)
Mount point /home
Format No (if you are reinstalling you usually want to keep the data in Home so DON'T format, if this is the first install select to format)

For swap
Filesystem swap
Mount point swap
No format option for swap

After that it should allow you to proceed with the install.

If these partition don't exist, during creation of partition you specify mount point right away (during the installer, not if you're running Gparted from live desktop).

---

### Post by Drag0n42 on 2010-02-22
> **darkod said:**
> Depending...
If the partition already exists, in the installer in step 4 you need to  use Manual, then in the list of partitions click each one by one, then  the button Change on the bottom of the screen. You will need to change  from Not Used (which is the default) into:

For /
Filesystem ext4 (or ext3, depending which you want to use)
Mount point /
Format Yes

For /home
Filesystem ext4 (or what ever it was before if you are reinstalling)
Mount point /home
Format No (if you are reinstalling you usually want to keep the data in  Home so DON'T format, if this is the first install select to format)

For swap
Filesystem swap
Mount point swap
No format option for swap

After that it should allow you to proceed with the install.

If these partition don't exist, during creation of partition you specify  mount point right away (during the installer, not if you're running  Gparted from live desktop).

It doesn't even get to the 4th step. The "No Root Directory Specified" error happens right after 3rd so i cant get to it. But to make sure I am reinstalling wubi.exe

---

### Post by darkod on 2010-02-22
> **Drag0n42 said:**
> It doesn't even get to the 4th step. The "No Root Directory Specified" error happens right after 3rd so i cant get to it. But to make sure I am reinstalling wubi.exe

It can't be. It also depends which version are you talking about. In 9.10 the installer has 7 steps while there were 6 before that.
In any case, that message is displayed if you hit Forward without specifying the mount points, hence the message is no root filesystem defined.
Are you entering the manual partitioning option?

---

### Post by Drag0n42 on 2010-02-23
> **darkod said:**
> It can't be. It also depends which version are you talking about. In 9.10 the installer has 7 steps while there were 6 before that.
In any case, that message is displayed if you hit Forward without specifying the mount points, hence the message is no root filesystem defined.
Are you entering the manual partitioning option?

It will not give me any kind of option to enter manual partitioning or not it will only let me get as far as the 3rd step then the error pops up. I know it is weird. I am attempting to find an external program that can edit the mount points, but if that fails then i will see if i can find the previous version of Linux ububntu to install and see if that fixes the error.

---

### Post by darkod on 2010-02-23
Can you look here and see if this is what you are getting before the partitioning stage?
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Note: I think they've mixed up the screenshots sometimes, on some you will see a total of 6 steps mentioned, on others a total of 7. But ignore that, otherwise they are in order as they should appear.

---

### Post by Drag0n42 on 2010-02-23
> **darkod said:**
> Can you look here and see if this is what you are getting before the partitioning stage?
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Note: I think they've mixed up the screenshots sometimes, on some you will see a total of 6 steps mentioned, on others a total of 7. But ignore that, otherwise they are in order as they should appear.

Yes that is what i am getting just before the partitioning stage it gets to the Keyboard test then errors out.

---

### Post by carolineictwiki on 2010-02-25
I had a similar problem but got it fixed:

I ran partition magic which detected some errors with my partitons and offered to fix them, which I allowed it to do. After that, I re-booted and it finished the installation just fine!


Backstory:
I was dual booting with XP, and was using Wubi because the regular installation detected my whole hard drive as unallocated space (and thus would have overwritten my XP install). After booting into Ubuntu the first time, it kept complaining of 'no root directory specified' and wouldn't complete the installation.

I tried checking the partitions in gparted, but again it just saw everything as unallocated space. Disk utility, however, saw the partitions, but wouldn't allow me to delete or change them (giving me a msdos_magic error).

I found a copy of partition magic thinking to delete the partitions that way and instead it fixed whatever the problem was!

---

### Post by darkod on 2010-02-25
Gparted from the ubuntu live cd also has Check option when you right-click any partition. Not sure if it can help or repair anything, or if that is the problem at all.
But it's very strange to complain about root directory not specified and it's not even allowing you to get to step 4 in the installer where you specify where to install ubuntu.

---

