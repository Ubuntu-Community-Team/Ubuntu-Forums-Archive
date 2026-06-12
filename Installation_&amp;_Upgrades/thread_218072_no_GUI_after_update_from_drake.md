---
title: "no GUI after update from drake"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by shadess7 on 2006-07-18
Okay so the day after the L6.06 came out I did the update following the procedure carefully but somewhere in the middle of the instilation something went very wrong and it didnt install propoerlly and now I have no GUI and have not been able to fix it in these past weeks by trying every sound piece of advice I can find on the threads mostly because the computer cant find files which were not downloaded correctly and is unable to retrieve them either!!! 

So I give up, I want to reinstall from a CD directly that I can burn of the internet however I was sloppy and didnt save my stuff to CD first thinking it would be another simple update like the updates within the old release. SO I DONT WANT TO LOOSE that info which I know is still in the computer because I can see the files names in text mode which is all I have and working wong, but cant save to CD because nothing works properly, its all in the disk partion with my stuff as recommended, 

SO my QUESTION IS: if I install from a CD will I loose or keep my files? Im a extreme begginer and have no one else to turn to, please help I need to be able to use my computer again? also I only have ubuntu on my computer no other Operating systems

---

### Post by adam.tropics on 2006-07-18
Do you have a seperate /home partition? If so, you can reinstall, and tell the installer not to format the existing /home partition, thereby protecting all the data in your home directories, which is good as this includes most of your settings too. If you don't have a seperate /home partition, it would be a good idea to create one on your next install. It will save many of these potential headaches. [This is a nice guide]("http://www.psychocats.net/ubuntu/partitioning.html") to partitioning.

---

### Post by Herman on 2006-07-18
Another way to do it would be to just install Ubuntu again from a new Ubuntu Dapper Drake 'Desktop' CD that has the GParted partitioner in it. GParted can shrink other Linux (Ubuntu) partitions. Go into 'manual partioning', and resize (shrink) the existing Ubuntu partition to make room for a new Ubuntu system you are going to install. Install the new Ubuntu operating system beside the old one on the disk. (So you will have two Ubuntus on the same disk, the new one and the old one.
Then boot into the new Ubuntu system and mount the old Ubuntu's filesystem and just copy the files right into the new system. [***Click Here***]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu") to see how to mount it.
You can delete the old partition later, or install another new system on or use it for a data partition. Another idea is to copy your operting system to it without any data in it, just the software and all your settings and use it for a system and software backup partition. If your system ever gets destroyed again you can just copy the one from the backup. It only takes about ten minutes.
:D  I like aysiu's partitioning help page too. I prefer single partition installs myself though. No offence meant to anyone, it's just that I like to keep pointing out that there are lots of other ways to do things. :D
Regards, Herman :D

---

