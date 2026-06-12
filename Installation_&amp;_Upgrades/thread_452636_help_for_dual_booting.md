---
title: "help for dual booting"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by jonkey86 on 2007-05-23
first off let me say im new to all this linux stuff, i have xp installed and only one 60gb HD
i downloaded and burned ubunto image file 7.04, rebooted and i think i was in ubunto, i clicked on install and followed the steps, it asked me for language, then location, then keyboard settings. after thatis where my problems started, i had to select a partition option. 
1. guided- use entire HD (unlike guides ive read, it did not have a scroll to select how much of the drive i wanted)
2. guided - use free continous space
3. manual

when i select manual it displays 3 drives, one with about 5gb one with 53gb and another with 8 mb, the first 2 use ntfs and when i choose to edit the first one i cant seem to know the right size, its either too small or big. i really dont know what to do as i want to dual boot with xp and not loose any data i currently have. what can i do?l

---

### Post by apunc1 on 2007-05-23
Hi,
Yes you were in the Ubuntu install. You're heading in the right direction.
Here is a guide that can help you. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Make sure to defragment your windows partition before you install Ubuntu.

the first guided option will make Ubuntu the only OS on your hard drive
the second guided option will resize windows for you and install Ubuntu on a separate partition
the manual option will allow you to partition the hard drive as you wish, making partitions for /home or shared partition to share files with windows and ubuntu

the psycocats guide will explain it further.

---

### Post by jonkey86 on 2007-05-23
thanks for your help,

will the second option leave any free space on the xp partition?

---

### Post by apunc1 on 2007-05-23
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

scroll down to the part about partitioning. there are explanations of each partitioning choice.

---

### Post by jonkey86 on 2007-05-23
thanks again, 

i have read that same guide many times but the problem arises when i get to that partition screen, non of the options i select displays the cursor that allows me to drag for a certain percentage, what version is that on the images? im still stuck in this partitioning part of the instalation

---

### Post by apunc1 on 2007-05-23
choose manual as see here
[http://img379.imageshack.us/my.php?image=feistydual08ks0.png](http://img379.imageshack.us/my.php?image=feistydual08ks0.png)


then it will show you your partitions

you should have the option to edit them as seen here
[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

i myself have never used the feisty installer so i'm only going by the psycocats tutorial.


if you're still having trouble with all that and want to dual boot windows and ubuntu, then choose as shown below
[http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)

this will give you a dual boot. you should backup your windows data just in case anytime you partition a hard drive.

---

### Post by jonkey86 on 2007-05-23
i tried installing again and selected the manual partitioning and this is what came up

[http://img369.imageshack.us/my.php?image=untitledie6.jpg](http://img369.imageshack.us/my.php?image=untitledie6.jpg)

what do i do from here?

---

### Post by apunc1 on 2007-05-23
you're almost there

select "forward" at the bottom right and you should then come to a screen that will allow you to edit partitions

---

### Post by jonkey86 on 2007-05-23
ok i picked manual and i chose the larger partition i clicked on edit, another window popped up, it showed ntfs, should i just change this to ext3 

[http://img490.imageshack.us/my.php?image=99884222yh9.jpg](http://img490.imageshack.us/my.php?image=99884222yh9.jpg)

is the mount point ok? did i choose the right partition?

---

### Post by apunc1 on 2007-05-23
> **jonkey86 said:**
> ok i picked manual and i chose the larger partition i clicked on edit, another window popped up, it showed ntfs, should i just change this to ext3 

[http://img490.imageshack.us/my.php?image=99884222yh9.jpg](http://img490.imageshack.us/my.php?image=99884222yh9.jpg)

is the mount point ok? did i choose the right partition?

that is your windows installation.choose to resize  Windows XP partition and make that smaller. That will leave  some of the disk free to create a new partition in.  install Ubuntu there. ubuntu is ext3. windows is nfts. the mount point for your ubuntu installation will be / (root). if you want to make a separate home (you should) then mount that as another partition /home (ext3)

edit: of course make sure your windows data is backed up before you apply the partitions, just in case.

---

### Post by jonkey86 on 2007-05-23
kinda confused here, can you tell me what to put in use as: and mount point?...im on the right path right?

---

### Post by apunc1 on 2007-05-23
> **jonkey86 said:**
> kinda confused here, can you tell me what to put in use as: and mount point?...im on the right path right?

mount point for windows? its fine in the screenshot you showed.

if "use as" means "type" then yes nfts is correct for windows

---

