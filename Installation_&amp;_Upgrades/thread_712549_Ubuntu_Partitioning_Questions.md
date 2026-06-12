---
title: "Ubuntu Partitioning Questions"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Jon0415 on 2008-03-01
Hey everyone, I recently made teh switch over to Linux from Windows XP a couple days ago on my desktop. While installing Ubuntu 7.10 off of the live CD I have, I am of course brought to the partitioning window. With Windows XP I have a 60gb hard drive for storage adn what not, with another 28gb already partitioned off for backup reasons.

I want to change this backup partition to the partition where Ubuntu will be installed, removing my backed up information as I also have a 250gb external HD I use as a backup now. I changed the partition type to ext3, waht do I set for the Mount Point Option? I'm really not too familiar with partitioning and would rather ask before making a mistake on my own.

Thanks for the help guys, I already love the community here jsut from my lurking the past few days

---

### Post by Sam Lars on 2008-03-01
So do you want to install on the whole hard drive?  You can just choose the option to wipe it and use the whole disk if that's the case.
Basically, Ubuntu will install to the / mount point.

---

### Post by Shazaam on 2008-03-01
Before you partition your drive(s) you need to figure out the partition names. With the Ubuntu livecd in and running open System>Administration>Gnome Partition Editor (gparted). This will give you a gui view of all of your drives and partitions. Write them down so you don't accidently overwrite critical partitions (Windows).

Some people (me too) like to set up their partitions before installing distributions. The best way IMHO is to use the gParted LiveCD. You can get it from here.......

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

If you are going to shrink (resize) any Windows partitions make sure you defrag them first.

---

### Post by Jon0415 on 2008-03-01
> **Sam Lars said:**
> So do you want to install on the whole hard drive?  You can just choose the option to wipe it and use the whole disk if that's the case.
Basically, Ubuntu will install to the / mount point.

No Basically I want to install Ubuntu over the backup partition thats already in place. I just didnt know if this would effect my seperate windows partition.

---

### Post by TennTux on 2008-03-01
I'm not quite sure that is what Jon0415 was saying. If I read him correctly he has an internal hard disk with 60Gb + 28Gb space. He has Win XP on the first partition and Backup Data on the second. He now wants to wipe out the Backup Data and install Linux in that space.

If that is the case then it is my limited understanding of Linux that he would want to replace the single Backup partition with two partions. One an ext3 partiion into which Linux would be installed and a second as a swap partion. This would allow dual boot if your not quite ready to give up Windows yet. Dual boot being the option to bring up a menu at boot time to choose either Windows or Linux. If this option is chosen it may just work. However if it doesn't then there are are a number of posts on how to fix the minor problems that could occur.

Though if I am mistaken and the whole disk is to be used then yes SamLars has it right wipe out the existing partitions and have an ext3 partion for Linux and a small swap partion. I believe there may be an option to use a swap file in stead of a partition. However, the simplest way I have always found is to use the partition.

---

### Post by Jon0415 on 2008-03-01
> **TennTux said:**
> I'm not quite sure that is what Jon0415 was saying. If I read him correctly he has an internal hard disk with 60Gb + 28Gb space. He has Win XP on the first partition and Backup Data on the second. He now wants to wipe out the Backup Data and install Linux in that space.

If that is the case then it is my limited understanding of Linux that he would want to replace the single Backup partition with two partions. One an ext3 partiion into which Linux would be installed and a second as a swap partion. This would allow dual boot if your not quite ready to give up Windows yet. Dual boot being the option to bring up a menu at boot time to choose either Windows or Linux. If this option is chosen it may just work. However if it doesn't then there are are a number of posts on how to fix the minor problems that could occur.

Though if I am mistaken and the whole disk is to be used then yes SamLars has it right wipe out the existing partitions and have an ext3 partion for Linux and a small swap partion. I believe there may be an option to use a swap file in stead of a partition. However, the simplest way I have always found is to use the partition.

You are correct in the firs thing you said. Leaving Windows on its 60gb portion and changing the 28gb backup portion into Linux + Linux Swap. I was just unsure of the type of partitions to change it into to. I'm sorry for any confusion my posts have brought

Also, what do I put under the Mount Point option? Some choices are /, /boot, /home,... etc

---

### Post by sushi416 on 2008-03-01
You should select / to be the Mount Point. Took me a while to figure that out too when I switched to Linux. =)

---

### Post by TennTux on 2008-03-01
> **Jon0415 said:**
> Also, what do I put under the Mount Point option? Some choices are /, /boot, /home,... etc

This request for a mount point. Do you see it during the installation? or are you running some utility like the "disk manager" or "parted" from the Live CD? It is my understanding that in the install process it won't ask for a mount point. However, if this is one of the utilities I'm not quite sure. I would guess / since all Unix and Linux systems need a root partition with all other partitions being mounded (mapped or attached) to sub directories.

---

### Post by Jon0415 on 2008-03-01
> **sushi416 said:**
> You should select / to be the Mount Point. Took me a while to figure that out too when I switched to Linux. =)

Do I select that for the Linux Swap partition as well?

---

### Post by Sam Lars on 2008-03-01
The swap should not have a mount point... it's just swap.

---

### Post by Omnios on 2008-03-01
> **Sam Lars said:**
> The swap should not have a mount point... it's just swap.n qparted you can right click the swap partition and activate the swap partition as swap.

 I

---

### Post by Omnios on 2008-03-01
Umm forgot to mention the mount point for root is " / " where all the linux files are installed into. Also there is the "/home directory where all your personal files will be installed into. Most system files go into / which is owned by root. The/home directory is where your files will go into and can have a different entry with different users. /home is also mountable where you can have /home partition. I have heard this recommended for a long time now and finally make a /home mount for my personal files on my fileserver. 

 The  / partition can be fairly small 30G or under which is more than you will use. On the other hand the /home may be very large as this is where your personal files may go.

---

### Post by Jon0415 on 2008-03-03
> **Omnios said:**
> Umm forgot to mention the mount point for root is " / " where all the linux files are installed into. Also there is the "/home directory where all your personal files will be installed into. Most system files go into / which is owned by root. The/home directory is where your files will go into and can have a different entry with different users. /home is also mountable where you can have /home partition. I have heard this recommended for a long time now and finally make a /home mount for my personal files on my fileserver. 

 The  / partition can be fairly small 30G or under which is more than you will use. On the other hand the /home may be very large as this is where your personal files may go.

Thanks you a lot for all of the help. I already love the community around here

---

