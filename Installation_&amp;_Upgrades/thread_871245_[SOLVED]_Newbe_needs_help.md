---
title: "[SOLVED] Newbe needs help"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by greenco on 2008-07-26
I have removed Windows XP and I have been trying to run Ubuntu 8.04 for several days now and I am pleased with it, until I screw something up. I have removed and installed it more times than I care to think about. I have spent a lot of time reading the posts on this forum and it seems that it is best to partition your hard drive into 2 or 3 partitions. They talk about using one partition as a backup. Being a "NEWBE" to the Linux world, I am not sure just how this works. 

In hopes that I can get away from doing so many "reinstalls", I have partitioned my hard drive into two partitions and installed Ubuntu 8.04.
 
1.. Looking at them, they both seem to contain the same files and folders. Is this normal? 

2.. From this point, what is the best way to proceed with adding programs? Should I keep the primary partition just the way it is and put any add ons onto the second partition? 

3.. Should I need to reinstall Ubuntu 8 again, how would I do it with this setup? 

4.. How do I protect my bookmarks and address book? I think that I could export them and store them on the second partition. Is this the correct way to do it?

I want to do this the correct way this time. I can't bear the thought of installing windows again

---

### Post by Pumalite on 2008-07-26
Post:
sudo fdisk -lu
(boot your Live CD if need be)

---

### Post by greenco on 2008-07-26
Pumalite, that might make sense to someone with a lot of Linux knowledge, but to me it means nothing. I can enter and run sudo strings, but how do I protect my personal data, if I have to reinstall Ubuntu. 
Thanks

---

### Post by lisati on 2008-07-26
> **Pumalite said:**
> Post:
sudo fdisk -lu
(boot your Live CD if need be)

> **greenco said:**
> Pumalite, that might make sense to someone with a lot of Linux knowledge, but to me it means nothing. I can enter and run sudo strings, but how do I protect my personal data, if I have to reinstall Ubuntu. 
Thanks
Greenco:What pullamite's suggestion of entering ```
 sudo fdisk -lu
``` does is show something about how the data on your hard disk (specifically the "partitions") is organized. This will be helpful for us when working out an answer to question 3 in your original post. It might also provide us with a clue on what to recommend for keeping a backup of your valuable data.

---

### Post by greenco on 2008-07-26
Here is the results of that query. It is about as clear as muddy water to me. Thanks

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   235769939   117884938+  83  Linux
/dev/sda2       235769940   488279609   126254835    5  Extended
/dev/sda5       476134533   488279609     6072538+  82  Linux swap / Solaris
/dev/sda6       235770066   466286624   115258279+  83  Linux
/dev/sda7       466286688   476134469     4923891   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Pumalite on 2008-07-26
You have two OS installed. I suspect you installed the same twice. Get Gparted Live CD and delete everything in your hard drive. The make a 'new' partition of 10 GB for '/'; 1 GB for /swap and the rest divided between /home and backup. The backup you can format ext3 as well.
Then install; go Manual and use the already prepared partitions.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by greenco on 2008-07-26
Pumalite
 I just made a live CD and am ready to delete what is on my disk. Before I do that would you please explain what this all means (in layman's terms) <GRIN>

The make a 'new' partition of 10 GB for '/'; 1 GB for /swap and the rest divided between /home and backup

Thanks

Also, assume that I accomplish this, how do I then reinstall Ubuntu 8? Do I do it from the Ubuntu Live CD?

---

### Post by Pumalite on 2008-07-26
One you delete everything, you'll have the whole drive as unallocated space; then click on Partitions 'New'; make one at the beginning of the drive 10 GB, mount point '/' ( you just plant a / where it says 'mount point'). You repeat the process for the rest.

/-------/home-------/data-----------/swap--------

---

### Post by greenco on 2008-07-26
Ok, remember I am new to this process, so now tell me what gets installed on each of these four partitions. Next question is what do I need to use or how do I install a new copy of Ubuntu? Once the drive is empty, I have no other means of getting on the internet.
Thanks

---

### Post by Pumalite on 2008-07-26
I thought you had a Live CD. You boot from it, get to the Desktop, double click on 'Install' ( top left), at the Partitioner: go Manual. You know the rest.

---

### Post by greenco on 2008-07-26
I do have a Live CD, but I have never tried to install it in the manual mode. I will give it a go and if it fails I will use the assisted way to get back on line. 

Will be off line for a while.

---

### Post by greenco on 2008-07-26
Sorry but I could never get the partition program to fully load. It gets to a spot and then it hangs. The message says that it can not use the video mode. I tried it in safe video and failsafe modes an neither would get past it. Could I not use the Ubuntu Live Cd "Manual" option to partition the drive?

I just added the "Gnome Partition Editor" to my system. From what I read on their web page it should do about the same thing as what you want me to do.Do you think it will it work?

Could I not use the Gnome partitioner program to delete the "sda6" and "sda7" partitions and then resize the others as needed?

---

### Post by Pumalite on 2008-07-26
The advantage of Gparted Live CD is that it works with unmounted drives/partitions.
For installation; I'd burn a new CD and if it doesn't work: try the Alternate CD.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by greenco on 2008-07-26
I had the same problem when I used the Ubuntu 8 Live CD, but if I selected "safe Video" it would finish loading in VGA mode. I have tried to correct the partitions on my own and it now looks like this:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   235769939   117884938+  83  Linux
/dev/sda2       235769940   488279609   126254835    5  Extended
/dev/sda5       476134533   488279609     6072538+  82  Linux swap / Solaris
/dev/sda6       235770066   476134469   120182202   83  Linux

Partition table entries are not in disk order

I don't know if it is better or not.

---

### Post by Pumalite on 2008-07-26
Much better.

---

### Post by greenco on 2008-07-26
Thanks and if you would be so kind to help me a little more, how do I mount the second partition and what should it be used for? I still don't understand how it is used to store a backup, of the primary system.

---

### Post by Pumalite on 2008-07-26
Format it ext3 and forget about it. You can later mounted in /media
sudo mkdir /media/???
sudo mount -t ext3 /dev/??? /media/???

---

### Post by greenco on 2008-07-26
It was already formated as ext3 and I managed to get the sudo strings to work, but the only "/Media" that I can find seems to be protected. It is a folder located in the "Filesystem" and I can't do anything with it but look.

Is there any sudo string that I can run to verify it?

Here is what I entered to mount it.

coleman@coleman-desktop:~$ sudo mkdir /media/sda2
coleman@coleman-desktop:~$ sudo mount -t ext3/dev/sda2/media/sda2

---

### Post by Pumalite on 2008-07-26
Try this:
sudo chmod 777 /media/sda2

---

### Post by greenco on 2008-07-26
That worked, now is there a way to rename the sda2 folder to another name? I thought I had to use the partition's name.

---

### Post by Pumalite on 2008-07-26
You can use any name you want.

---

### Post by greenco on 2008-07-26
Thanks, for your help !!
I am ready to go to bed, so I will resume with this tomorrow. How do I get rid of the sda2 folder? Or should I leave it there and just make a new one?

---

