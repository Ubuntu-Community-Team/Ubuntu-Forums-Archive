---
title: "need partitioning help - defining root file system"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by lori.ann on 2006-11-15
I can't get Ubuntu 6.10 installed from the live CD. It runs just fine off the CD (I'm using it now) and I decided I definitely want to use it. However, when I open the install, it goes through all the options, and then gives me an error message: **"No root file system is defined. Please correct this from the partitioning menu."**
 I don't know anything about partitions other than I want to be able to dual boot Windows XP & ubuntu at least for now; I'd rather just use Ubuntu but I want to run them both for awhile to make sure I'm not losing any of my Windows stuff (documents, programs).
Let me know what more info I can share... I don't know much about all this.
Thanks! I'm looking forward to being part of the Ubuntu community!

---

### Post by bulldog on 2006-11-15
You should first defragment your windows several times.

Then when you come to the partitioner you have to make room for Ubuntu.

Or you can let Ubuntu make the decisions for you and let it use the space it want. [not the whole disk]
You have three options there.
1 Let Ubuntu decide or something like that.[yes]
2 Use the whole disk [no]
3 Manually partitioning [no]

Try this and post back if you have more questions.

---

### Post by lori.ann on 2006-11-16
I ran defragment twice. I was warned that Ubuntu may try to take too much space from Windows, and I won't be able to run it also. I am using 12.88 GB of my hard drive and have free 21.58 GB. Will Ubuntu leave enough room or do I need to just give it part of the free space?
Thanks for the tips - I'll try it out once I know this.

---

### Post by bulldog on 2006-11-16
Well if you want to get into this,download the gparted live cd.[aprox 25MB]
Burn this on a cd-r and boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

When you boot this you get a graphical disk partitioner,this one is more easy to use than the one on the Ubuntu cd.

Now you can resize your windows partition and make room for Ubuntu.

I recommend to make about 10GB--15GB total free for Ubuntu,that's enough to explore and install some extra software to try out.

From this free space you created use about 1GB to create a swap.
This is done by right clicking on your free space and select new partition.
The rest of the free space you make the /  [root] at the same way as you created your swap and make it bootable by setting the option boot flag.

Now exit gparted and start the ubuntu cd.
When you come to the partitioner you see your created partitions.
Now mount swap as swap and / as your root and format only these two partitions,look very carefully you don't want to format your windows!!

The let Ubuntu install and enjoy.

---

### Post by lori.ann on 2006-11-16
Do you suggest that I do this, or do you think letting Ubuntu decide will be just fine? 
I want to primarily use Ubuntu, probably move all my documents there, and I don't understand how to do all of the stuff (mainly about creating a swap) so I'm wondering if Ubuntu would do a better job of partitioning than I would.
Also, once I install Ubuntu, can I go back into Windows and defrag again (since I'll be moving most of my documents to Ubuntu), or will that mess with whatever partition I end up setting?
Thanks! You're really helpful; sorry I don't understand all the computer stuff to implement it.

---

### Post by bulldog on 2006-11-16
I can't tell you how much space ubuntu will use,I only do it manually to have all the control.
But you can try and see how it goes.

If it uses to much of your space you can always use the gparted live cd to resize ubuntu and add space to your windwos.

If Ubuntu is installed it will install a so called boot loader in your MBR.
This will allow you to choose which OS you want to use at start up,windows or Ubuntu.
So you will be able to boot windows again.

You can read your windows partition if it's formatted as NTFS and copy file from it,but you can't write to it.

---

### Post by lori.ann on 2006-11-16
This sounds great -- I just store anything I'm working on on a jump drive, anyway, so I don't think I need to worry about switching data back and forth. I think I'll only use windows for a few games I have, and use only once every few months (and could certainly do without, anyway).
I'll do this now and let you know how it goes! 
I'm excited to use Ubuntu!

---

### Post by lori.ann on 2006-11-16
I tried again (after deleting unnecessary programs & files from Windows, restarting, and defragmenting Windows 3x. I got the same error message 15% into the install: **"No root file system is defined. Please correct this from the partitioning menu."**
Ideas?

---

### Post by bulldog on 2006-11-16
Yes I have.

You need to have two partitions,a /  =root and a swap.
If you let Ubuntu do the work it should be done without interfering from user.

If you do it manually you have to create those two partitions **and** mount them on /  and swap and the format these two.

---

### Post by lori.ann on 2006-11-16
Thanks... could you walk me through this... what you're saying to do:

[I]
"You need to have two partitions,a / =root and a swap."[/I]
How do I make those?
[I]
"If you let Ubuntu do the work it should be done without interfering from user."[/I]
I told it to do it itself, and it still gave me that error message.

Thanks!
Lori Ann

---

### Post by bulldog on 2006-11-16
Do you have enough free space available?

I really should download the gparted live cd [25MB] and burn it on a disk.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then boot from this cd and follow the steps.
You will see you hard disk listed and see how its partitioned.

You can only have four primary partitions and I don't know how your disk is partitioned,maybe you can tell me?

You do have a C:\ but are there more partitions in your windows listed?
If yes tell me [not the cd-rom drives though]

If you have a C:\  a  D:\ or even more I like to know.

EDIT:
It's almost midnight here in Holland and I have to get up at six so I go for a bit of sleep.
I'll be back tomorrow just post your findings or give me a PM.
Should be back in about 17 hours.

---

### Post by lori.ann on 2006-11-17
Thanks for all your help. Here are the partitions listed in GParted:

partition name - type - size - space used
/dev/hdc1 - fat16 - 39.19 MiB - 7.28 MiB
/dev/hdc2 - ntfs - 34.46 GiB - 13.12 GiB
unallocated - unallocated - 7.84 MiB - none
/dev/hdc3 - fat32 - 2.75 GiB - 2.23 GiB
unallocated - unallocated - 7.84 MiB - none

---

### Post by bulldog on 2006-11-17
Hmmm strange disk partitions.

Where is hda and hdb?

Do you have more than one hard disk?

I presume you have windows on the NTFS partition,what is on the hdc3?

How did you create the unallocated space twice and why?

---

### Post by lori.ann on 2006-11-17
I thought it was strange, too.
How do I find where hda and hdb are? I only have one hard disk. It's a laptop, and I've never partitioned anything before or created unallocated space, but it's a refurb so maybe someone did before I got ahold of it?
I'm pretty sure you're right about Windows being on the NTFS partition, but I don't have a clue what the others are there for; I don't even know what they are. Or what hdc3 means.
Strange, I know... thanks again for so patiently helping me!

---

### Post by bulldog on 2006-11-17
Well some basic's.
The first hard disk is usually called hda,the second hdb and the third,yes you guest it,hdc.
Partitions on a hard disk are referred to by a number,so the first partition on a hard disk would be hda1 the second hda2 and so on.

Do you have a recovery cd or partitions on the hard disk which are relevant to know about?

Because if we repartition and delete the FAT32 [hdc3] it's fairly possible you can't restore your Windows install.
I ask this because there's a FAT16 [hdc1] at the beginning of the disk which also could be activated by a floppy disk.

Other thing is your disk is about 40GB total space and if the recovery should be there,you don't have much space left to install Ubuntu.

Maybe you should concider a bigger disk [expensive] or keep your Windows.

Ubuntu is a great OS but it's totally different from Windows.

But if you're up to it,remove your windows and install only Ubuntu and start to explore.

Before you should decide to this option,ask yourself if you can do without windows.
Do you use special applications which only run in Windows,do you have a wireless internet connection which can be a pain in the *ss.

And not in the least are you the kind of person who want's to learn a complete new OS and go through the trouble to learn it.

Think about it and let me know.

---

### Post by lori.ann on 2006-11-17
I've never messed with my partitions, but maybe someone did before I owned it. I have a physical reinstall CD of Windows XP (which is why I don't object to playing around; I can just reinstall Windows if I mess it up), but I haven't put anything on the hard drive like a recovery CD or partitions.
I have a laptop and there's no floppy disk drive, and I can't easily explain my disk space and don't want to get more hard drive memory; I use so little of it to begin with. I don't install many programs on my computer, I just use basic stuff it comes with. I am willing to learn a new operating system (actually, when I lived at home before college, my dad used linux), the main thing is compatability stuff while I'm in school. As in, I have to use educational software for one of my classes. Also, I don't pay for internet so I use free wireless internet. I don't know if mine will work or not (I can't find that list). 
Anyway, for right now my computer is frozen on a black screen with some white text on it... before that happened, a paper I was working on was there. [http://www.ubuntuforums.org/showthread.php?t=301622](http://www.ubuntuforums.org/showthread.php?t=301622)

Alrighty, let me know what else I can tell you.

---

### Post by bulldog on 2006-11-17
Nothing,all I need to know is said already.

Okay work to do.
I hope you have downloaded the gparted live cd and burnt it to a disk?
We gonna need it now.

Boot from the gparted live cd and follow the steps.
You will end with all your partitions on screen.
```
partition name - type - size - space used
/dev/hdc1 - fat16 - 39.19 MiB - 7.28 MiB
/dev/hdc2 - ntfs - 34.46 GiB - 13.12 GiB
unallocated - unallocated - 7.84 MiB - none
/dev/hdc3 - fat32 - 2.75 GiB - 2.23 GiB
unallocated - unallocated - 7.84 MiB - none
```

We let hdc1 remain because I'm not sure what's on it.
Now delete hdc3 so you get more unallocated space.
The two 7.84MB is unallocated and should come together with the space from hdc3.Check this.You have to end up with one large unallocated space.
Notice there's nothing done really,you have to apply your changes and then it's taken place.
If done go the next step.

Now resize your windows to 20GB,this could take a while don't interrupt this proces please.Make the free space **behind** your windows not in front.
Notice it counts in MB, 1 GB is 1024MB.
You have to apply the changes again.
Now you should have enough space to install Ubuntu.

The next thing you do is create a swap,right click the unallocated space and choose new partition and choose swap 1GB.
The rest of the unallocated space is your root,right click the unallocated space and choose new partition and select / rest of the space.
If there is given the option make it bootable,select yes.
Format it as ext3 file system.
Again apply and check if the partitions are created.
If so exit the gparted cd and go to the next step.

Now we gonna boot the live Ubuntu cd.
You see the install button on your desktop.
Answer the questions and go to the partitioner.
Here choose manual partitioning.
Mount your swap as swap and your ext3 partition as / [root]
Now these two will be formatted,**be sure your windows partition is un-ticked**
Now if things go well Ubuntu will install on your disk.

You get a menu at startup called GRUB,here you choose which OS you want to boot,default is Ubuntu,but can easily be changed to windows.

That's all I can tell you.
You just have to try to accomplish this on your own,read carefully and be sure your windows partition is never ticked to format.

Wish you luck,and if there are more questions,let me know.

EDIT:
Have read this and we gonna look for a solution when you installed Ubuntu.

[http://www.ubuntuforums.org/showthread.php?t=301622](http://www.ubuntuforums.org/showthread.php?t=301622)

---

### Post by lori.ann on 2006-11-18
Alright, I understand partitions a lot better now.
Here's where I am.

I walked through all of Gparted, and it went fine. I now have fat16, ntfs, linux-swap, and ext3. I went through install of Ubuntu manually setting linux-swap as swap and ext3 as root. It is now at a point with this message:

"Go back to the menu and correct errors?
The test of the file system with type fat16 in partition #1 of IDE2 master (hdc) found uncorrected errors. 
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

I don't need to use my computer right now, so I'm just leaving it with this error message until further word.

I can't wait to figure this all out and pass it on to some younger Ubuntu user someday :-)

---

### Post by bulldog on 2006-11-18
If you have a little time to spare and don't mind installing,I have the following suggestion.
Your disk is a little strange with this partitions,but I thought it could work.
It can but there are errors on it.

I should boot gparted,erase all partitions till you have one large unallocated space without partitions.
Then create a 20GB NTFS just like discribed before,a swap 1GB and make the rest ext3 voor your / .

Then install windows first,and then Ubuntu.
It takes some extra time but you're sure the disk is what it should be.
This time is everything new and the install of both should be a peace of cake.

And you learn to use gparted and get familiar with it which is a good thing to start with.
Have to say you do fine so far.

---

### Post by Enroth on 2006-11-18
Just wanted to clear up something (If this hasn&#8217;t been solved)

partition name - type - size - space used
/dev/hdc1 - fat16 - 39.19 MiB - 7.28 MiB
/dev/hdc2 - ntfs - 34.46 GiB - 13.12 GiB
unallocated - unallocated - 7.84 MiB - none
/dev/hdc3 - fat32 - 2.75 GiB - 2.23 GiB
unallocated - unallocated - 7.84 MiB - none

The two unallocated part ions (from my experience) occur when you delete a part ion from earlier, which is not located near the free space. (In the last few days I have done this multiple times)

---

### Post by lori.ann on 2006-11-18
What are part ions? 
I have that unallocated space deleted now, and it's allocated as ext3 to go to running Ubuntu.
Thanks!

---

### Post by lori.ann on 2006-11-20
I want to finish my paper right now (it got lost in the freeze-up last week) and then I'll have free time to redo all the partitions. I guess Ubuntu was installed on my computer even when I hit "cancel" on the error message, so I'm running it and it is fast and going well. But I'd still like to have a fresh start with Windows and everything, and I have no classes on Wednesday for Thanksgiving so I will have spare time then.
Can't wait!
And thanks for the encouragement. You're helping a lot.

---

### Post by bulldog on 2006-11-20
If you need help with anything,just PM me please.
This topic is hard to find back for me and I'm answering others too.

So I've get lost in all the topic's:D 

If you need assistance,PM please.

---

