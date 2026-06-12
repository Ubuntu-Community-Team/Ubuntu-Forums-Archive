---
title: "CRASH and Recovery -- Successful because of partitioning"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by n4pgw on 2013-02-18
When I installed Ubuntu this time around, I decided to partition it in a way where I did not need to copy everything to an external drive before re-installing the OS.  It paid off!

My partition scheme is as follows: 

sda1:   ext4    /boot     2GB
sda5:  linux-swap     4GB (amount of RAM I have)
sda6:   ext4      /    20GB    
sda7:   ext4      /home    450GB (remainder of drive)

I had a problem with my Nvidia X server and somehow corrupted the video driver trying to fix it.  The result was a computer that would only boot to the command line.  I don't know enough to understand what to do when I run the repair option on the install disc so I had to do a new install. 

When I reinstalled, I chose the manual partitioning option and edited each partition setting as follows: 

sda1: format ext4  /boot
sda2: format linux-swap for swap area
sda6: format ext4 / for root area
sda7: do not format  for /home 

Then as I installed the system, I used the same user name and password as before.  

The end result is that after adding all the updates and reentering Unity, I was able to bring up Firefox -- **[COLOR=Red]with all my favorites and passwords still in tact![/COLOR]**

After seeing this successful, I installed Claws Email.  It, too, came up with all my old email, email accounts and password settings as if I had not crashed.  

The added bonus: The video settings now work and are  sticky.  My problem before the crash was that I would set the video to only use my Compaq monitor and not my TV.  However, it would always resort to using both monitors whenever I logged in or rebooted and I would have to change it back to a single monitor manually.  

I have always wondered how to set up all these partitions, so in the past, I have just set aside a small partition at the end for the swap area and used the rest of the drive for everything else.  

Here is the logic behind my thinking: 

I know the first area needs to be the boot partition, so I made it large enough I hoped I would not need to expand it.  I allocated 2GB, but it comes out as 1.91GB, probably due to sector rounding.

Then, the swap file will probably work faster if it is near the beginning of the drive instead of at the end.  So, I allocated 4GB, the maximum amount of RAM this computer can hold. (Ubuntu install reduced it to 2.81GiB.)

I have no clue what is adaquate for the root partition where all the software and tmp files are stored.  I made a WAG and chose 20GB.  I hope that is enough.

The rest of the drive was set up as the /home partition.   My theory proved to be correct: If I reinstall the system and use the same username and password, I would not lose my data!  

It worked!

My hope for this thread is that someone  else may learn a little useful information about partitioning without being overwhelmed by it.

Comments and questions are welcome. If someone can add more useful, simple information, I welcome it.

Thank you to all those who know more than me who have helped me out more recently and over the years!

Buck

---

### Post by dino99 on 2013-02-18
for info, standard install way

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by n4pgw on 2013-02-18
[LEFT]It looks like I was pretty close: 

>  here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? ,  will be asked when installing in manual mode by choosing "Something  Else" into the installer.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings
 

The only real difference between the above info and my install was that I used the installation process to create partitions the first time around and the above suggestion merged the root and the boot together.  

I think I recall trying to merge the two a long before but without luck because I probably did not make the root bootable.  If I had, I would have followed the same plan as above.

I have tried creating the partitions using a live disc and then installing into them as described above.  However, I find that creating them during the installation is a more simple approach as you don't have to do things twice.

I appreciate your input and your showing us an even simpler partition layout.

Thank you
Buck
[/LEFT]

---

### Post by presence1960 on 2013-02-18
There is no set best way to set up partitions for a linux install. There are many options and each user can decide what is the best way that suits their needs.

That being said, even with that set up fulfilling your needs to not copy files during a reinstall, it is still strongly suggested that you have a working back up of those files. The reasons are:

1. Stuff happens!
2. hard disk will fail. Not a question of if it will fail but rather the question is when it will fail.
3. During partitioning/installation operations nothing is ever guaranteed   as things occasionally do go afoul!

It is always a best practice to have a current working back up of everything you can not afford to lose.

---

### Post by presence1960 on 2013-02-18
> here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by choosing "Something Else" into the installer.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings 

Actually the swap info is not exactly correct for every installation. With machines that have more than 4GB of RAM you can get away with no swap. I recommend using a swap partition because the Live CD will utilize that when booted.

If you want to use hibernate/suspend the rule is swap = amount of RAM. This is necessary because the processes active in RAM will be written to swap on hard disk so you want to insure you have enough space to write to in case your RAM is fully utilized at suspend/hibernate time.

---

### Post by vanadium on 2013-02-18
Swap indeed typically is hardly needed if you have more than 4 GB of RAM, although there can be use cases, e.g. editing very large graphic files, where swap may be needed. In any case, swap remains a safeguard in case RAM would become critically low. I'd just keep some of it around.

In case you hibernate, swap indeed needs to equal at least the size of your RAM. Hibernate is slow anyway, and remains unreliable on several systems, to the extent that a default Ubuntu install does not include the hibernate option anymore.

More interesting is the "Suspend" mode, where all data remains in RAM, and "wake up" is fast. For that, you do not need swap.

Because one hardly uses swap on systems with sufficient memory, worriying about the location (start or end of disk) does not make much sense. Even on low memory systems, I wonder if you would feel the difference between a swap at the start of the disk or at the end - the system is already crawling anyway.

The setup with a separate home is a convenient one, which I also use since several years. It allows indeed for a very quick recovery: just reinstall the OS using the live CD, and your custom applications using Software Center as n4pgw described, and you are up again in less than one hour.

There is a caviat if you keep your root minimal like me (9.3 G). While this is plenty for an Ubuntu system (I now use 6 G after having installed gnome shell along Unity), also /tmp and /var/tmp are on that root partition. An application like the audio editor Audacity may fill that up. This is why I redirect these temporary directories. Currently, I have /var/tmp on my home partition, and /tmp on a (variable size) ram disk.

---

### Post by n4pgw on 2013-02-18
Thank you to all who have responded.  

I do need to clarify that this partitioning is for the purpose of **Fast Recovery** and not to be a substitute for a backup.  

In my experience, it is the Operating System that crashes more than the drive does.  By default, I have a backup right now as all the files were just moved to my USB drive so I could rebuild this system anyway.  

I have not prepared a regular backup method yet, but it is on the agenda. 

As for the swap partition, I set it up as 4GB, but it reduced it to 2.8 for some unknown reason, probably due to sizes of sectors.  However, I find it is faster to shut down and reboot than it is to save and restore a hibernated system. 

Having said that, I am able to leave this computer on 24/7 if I like, so I don't hibernate it.  I may decide to do so on my laptop when I set it up.  

Hmmm, that reminds me, is there a way of synchronizing Ubuntu machines so I can duplicate this on the laptop easily without running Ubuntu from a stick?

---

