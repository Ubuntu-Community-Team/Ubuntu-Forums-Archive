---
title: "ubuntu upgrade"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by The musmula on 2014-04-16
Hello everyone!
I want to update my Ubuntu 12.04lts to Ubuntu 14.04 lts (which should be out tonight) but I am not one of those people who will upgrade a system with the one button click option. I want to repartition my HDD as always (I tryed both methods and found this one to be the one with the highest risk but also best results) 

But let me first tell you a story, the story of why I am using LTS and not standard versions:
I wanted to do my partition upgrade thing ( which is basically setting the old / partition to be / and later switching /home directories ) To upgrade from 13.04 to 13.10 and as I was working with the partition manager with 300% concentration and no distractions anywhere ( I first made sure of the conditions ) and finishing the install and then.... BOOM!!! Ubuntu says "go to hell, Oliver I formated your ENTIRE HDD and all of your data, and not only that but all of your whole families data... Yaaay"

Don't get me wrong, I like Ubuntu and I don't think it is evil. But my question is do I need to do the whole fstab stuff to switch home folders after install or can I just make the old /home partition the new /home and will it erase the data? 
Btw 
I had cases where Ubuntu automatically checks the format check box after me in checking it

---

### Post by ian-weisser on 2014-04-16
> **The musmula said:**
> But my question is do I need to do the whole fstab stuff to switch home folders after install or can I just make the old /home partition the new /home and will it erase the data? 

'The whole fstab stuff' consists of copying one line into your new /etc/fstab.
And you seem to have done enough formatting to know that fstab has nothing to do with formatting or erasing.

---

### Post by The musmula on 2014-04-17
Yes I know, though I don't want to risk putting the use as /home thingy on the install. I even think that in some previous versions the /home had to be formated

---

### Post by grahammechanical on 2014-04-17
I have made repeated installs of different Ubuntu versions for testing purposes. I have used the Something Else option all the time. The installer has never installed Ubuntu and formatted the entire hard disk. It has always installed into the partition that I instructed the installer to install Ubuntu into.

When we install over an existing / partition then the installer has no choice but to format it. Otherwise pre-existing code remaining in the partition will mess up the operating system. 

When we have a separate /home partition, and we set the mount point then we get the option to format it or not format it. And, in my experience, the installer has always been obedient to my instructions.

I recently installed 14.04 onto a partition that Ubuntu 12.04 was installed on and of course the installer formatted the partition. How could it not do that and still give me a working OS?

Regards.

---

### Post by The musmula on 2014-04-18
I am not an idiot, I get the purpose of partitioning and I get that the intern gparted in the installer has the purpose to write over partitions. But i am talking about a bug from 13.10, that I`ve posted to the forums. And guess what? Nobody else had that problem and nobody else cared, so neigter would I... But, as said: the hdd had some important data that is lost forever (not really, I was able to get cca. 35% back). And I am glad that the installer usually works fine. Yesterday I also installed 14.04 over a 12.04, but first I made a complete backup that took forever and then I went to partitioning... and everything worked out perfect, I am currently getting the backup back in place and everything works perfectly fine. I love the new changes to unity and that ubuntu has support for android by default.

---

