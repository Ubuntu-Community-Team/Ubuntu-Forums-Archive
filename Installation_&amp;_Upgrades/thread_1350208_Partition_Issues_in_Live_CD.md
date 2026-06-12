---
title: "Partition Issues in Live CD"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by vidyesh on 2009-12-09
Hey,

I downloaded Ubuntu 9.10 amd x64 version for my system from ubutnu.com.
So the ISO is completely fine.  Right now I am typing from the Live CD which works fine. But when I try to install it, i get weird partitions. 
While on Windows I have made proper partitions in which I had allocated 29GB drive for Linux to be installed on, but when i am about to install the Live CD shows something weird. 
Here is my Partition breakup in my windows like i had done it before.
HDD 1 (all the partitions)
/ 30 GB
/ 29 GB 
/ 29 GB 
/ 49GB
 
The other HDD is completely fine.

Here is what the Disk Utility in Live CD shows me
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139166&stc=1&d=1260346894[/IMG]

THIS IS MORE WEIRD 

[IMG]http://i49.tinypic.com/ossy83.pngd[/IMG]

Please help me out . I need to install it in the Drive named 'LINUX'.

Thank you for your help.

---

### Post by ubhi on 2009-12-09
dear, you have to delete that NTFS partition, & make unpartional space for ubuntu installation, because we cant install ubuntu on NTFS partition, so free some space in ur disk
when u install from live cd or direct insert the CD, dont run try ubuntu, directly select install ubuntu option,.. you can see the below mentioned graphical installation steps.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by darkod on 2009-12-09
First of all, do NOT create partition for linux from windows. That will create ntfs partition and linux doesn't use them, not for system partition.
Second, one partition is not enough for linux, you need to have as a minimum a / and swap partitions. That means two.
Start the LiveCD again as you did, go into Gparted like the screenshot you posted, and delete /dev/sda3. Then do NOT create any partition in that space even with Gparted. Leave it as unallocated.
Then again boot with the cd but this time select Install Ubuntu option and at step 4 tell it to use Largest Continuous Free Space. That will install ubuntu into that unallocated free space creating / and swap for you.

PS. You see the keys symbol next to /dev/sda3? That means it's mounted and you can't delete it like that. Right click on it and select Unmount. After that Delete.

---

### Post by vidyesh on 2009-12-09
@ubhi
Thanks a lot. 
I did the same way, but when i open up disk utility with unallocated space it tells me i can't make any new partition. I thought i could jst make one ext3/4 partition and try 2 install on that.. 

@darkod
Hmm so went back to windows disk management, deleted the partition i wanted to and there was the unallocated space ready.
So you sure ubuntu wud b intsalled to the unallocated space itself? i mean it won't mingle up with my other drive right? 
I have 30 gb of unallocated space. so would it create the normal n swap partition from that only? 
please help me 
Thanks.

---

### Post by darkod on 2009-12-09
> **vidyesh said:**
> @ubhi
Thanks a lot. 
I did the same way, but when i open up disk utility with unallocated space it tells me i can't make any new partition. I thought i could jst make one ext3/4 partition and try 2 install on that.. 

@darkod
Hmm so went back to windows disk management, deleted the partition i wanted to and there was the unallocated space ready.
So you sure ubuntu wud b intsalled to the unallocated space itself? i mean it won't mingle up with my other drive right? 
I have 30 gb of unallocated space. so would it create the normal n swap partition from that only? 
please help me 
Thanks.

Yes, if you select the Use Largest Available Free space option (it was called something like that) it will install in that free space because that's the only one on the hdd. Try it and see how it goes. It should show you what partition it will create. If it looks suspicious to you, you can just hit the Quit or Back button and it won't do anything to your hdd.

---

### Post by vidyesh on 2009-12-09
OKay heres the problem.. 
Is it necessary to reboot n direct install.
i tried installing now.. and i see this.. 

I dont see any option of maximum free space or something. 


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139195&stc=1&d=1260376585[/IMG]

And here is the unallocated space which is ready. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139198&stc=1&d=1260376816[/IMG]

---

### Post by dhavalbbhatt on 2009-12-09
Here is what I would recommend you do.

First off, make sure all your data, from whatever partitions you have is backed up.

Next, ensure your Windows partition is completely defragmented. Once you have done that, figure out how much free space you have and determine how much space you want to allocate to Ubuntu (make sure you allocate enough for the main Ubuntu partition as well as for swap. Generally swap is about 2 times your RAM). You don't have to do anything in Windows at this point, just make a note for youself about the partitions and their sizes.

At this point, you have two options - one is to use Windows disk management utility to resize the Windows partition, hence creating free space for your Ubuntu partition. DON'T CREATE THE UBUNTU PARTITION FROM WINDOWS - just create the free space. The other option would be to leave things as they are and use the manual partitioning method from within LiveCD. I personally recommend manual partitioning, since I am always in control, but of course, manual partitioning comes with a slightly higher degree of understanding partitioning. If you feel comfortable using the manual partitioning method, then by all means, use that.

At this point, you should either have some free space to be allocated for Ubuntu, or you should be ready to install Ubuntu without having created the free space. If you had created the free space, then during the installation process, LiveCD will show the free space as an option where it will install Ubuntu. If you did not create the free space, then choose the manual option to create partitions and from there you can select the size of the Ubuntu partition along with the swap size.

I would also recommend you read as much as you can before installing the OS - it will make the whole installation process a lot easier.

---

### Post by darkod on 2009-12-09
You showed the other disk in the first post, the 160GB one, and I was working on that case.
This is a 1TB disk which has two partitions on it with no unallocated space. Do you see that? /dev/sdb1 and /dev/sdb2, no unallocated space. In other words no free space and that's why that option is not offered to you.
Is the 160GB disk still plugged in? Why isn't it shown?

---

### Post by darkod on 2009-12-09
You see the message that no more partitions can be created? That means you've reached the maximum of 4 primary partitions. When you deleted /dev/sda2 that would have left space to create extended partition in that space.
Did you create another partition on the 160GB after that?

---

### Post by vidyesh on 2009-12-09
My both the HDDs are connected all the time. 
And yes i do want to install in the 160gb. check the screenshot it has only 3 partitions and 4th is the unallocated space. I am not sure how 2 manage 2 install on the unallocated space.. 

@dhaval 
m trying 2 get on any web yahoo messenger and chat with you if you r online right now..
But not able 2 install flash now :P trying n getting in touch with you in few mins.. 
tryin pidgin now.. 

Thanks
Thank you both of you.

---

### Post by darkod on 2009-12-09
Open the 160GBdisk in Gparted, it creates a better picture. Don't use this Palimpsest manager. Post another screenshot of the /dev/sda.

---

### Post by vidyesh on 2009-12-09
Well its gonna be more confusing. 
hey you got Y! IM id ? could chat with you would be better .. :S 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139203&stc=1&d=1260378061[/IMG]

---

### Post by darkod on 2009-12-09
You still have the same 4 partitions!!! You said you deleted the 30GB partition. How come it's there?
Do you know that after deleting in Gparted you need to click the big green tick mark button in the toolbar? If you just close Gparted it will not do the changes. You need to confirm it.
That's why it's not offering the 160GB as choice for you during install, it can't create a partition on it, you already have 4 primary.

---

### Post by vidyesh on 2009-12-09
Er no there are just 3 partitions out there. check the first one its smethng weird.. 
and u saw the unallocated space in the disk utility. which isnt listed here.. 
Also the actual partitions r nt this way . 
my partitions on 160gb are 
30GB - Windows 7 
29GB
49GB
unallocated space 32GB.. 

but here its somethng weird.. :|

---

### Post by darkod on 2009-12-09
Usually I trust Gparted. /dev/sda1 is also a primary partition, it doesn't matter whether it's small or big, or whether you can see it from windows or not. You can't see the 100MB win7 boot partition too from win7 but it exists (/dev/sda2).
And /dev/sda4 is 119GB.
Why do you think you have different partitions?

---

### Post by vidyesh on 2009-12-09
Actually the 119 is not that. it should have been 49GB by the name it goes on windows.. which i m sure of.. 
m really not sure why the unallocated space is not shown.. 
I have different partitions for my data .. so the number of partitions.

---

### Post by darkod on 2009-12-09
I don't know what to say, I haven't seen situation windows to show one partition sizes and Gparted other. Palimpsest did show different partitions but it also said you have reached the maximum of 4 partitions.
Plus, you say you have 30GB + 29GB + 49GB. That's 3 partitions. Plus the small 100MB boot partition that's not shown in win7 that's 4. You can't create any more because all 4 are primary.
And I'm not sure what is that small 1MB partition at the start of the drive, according to Gparted it exists.

---

### Post by vidyesh on 2009-12-09
Okay thanks for your help.
Gonna try doing everything again. just to see if i missed anything.
would update if i get it resolved.. 
if you get any solution do let me know.

Thanks for trying. Really appreciate..

---

### Post by darkod on 2009-12-09
I think Gparted is right.
You can also try Disk Management in windows. Press windows button + R, type in the box diskmgmt.msc, hit Enter.
Check all the partitions reported there.

---

### Post by dhavalbbhatt on 2009-12-09
I am not sure whether you have really created the free space for Ubuntu. I am trying to add up all the numbers here, based on the screen shots that you provided and it seems that everything adds up to 149GB - basically, the two big partitions that you have - 30GB and 119GB add up to 149GB HDD that you have. So where is the other 30GB that you thought you had created for Ubuntu? Either that, or I am missing something here.

I also agree with darko - you cannot create more than 4 primary partitions. You may have to remove one of the partitions. Can you figure out what you have in that 100MB partition which is showing as NTFS?

---

### Post by gadolinio on 2009-12-09
Errrmmm what's in the 30 GB partition, sda3? You still haven't deleted it. If that's the space you wanted to give linux in the first place, unmount that parition, right click it, and delete it. Then click "apply" (in the upper toolbar of gparted, the green tick on the right). It prompts for confirmation; agree. THEN you'll have the unallocated space. And then you can install ubuntu there as discussed before...

---

### Post by darkod on 2009-12-09
> **gadolinio said:**
> Errrmmm what's in the 30 GB partition, sda3? You still haven't deleted it. If that's the space you wanted to give linux in the first place, unmount that parition, right click it, and delete it. Then click "apply" (in the upper toolbar of gparted, the green tick on the right). It prompts for confirmation; agree. THEN you'll have the unallocated space. And then you can install ubuntu there as discussed before...

The problem is he claims the partitions shown in Gparted are not correct. I haven't used Gparted too much but I haven't heard to show wrongly the partitions.
According to Gparted there are 4 primary partitions, the limit, and no unallocated space.
But he claims his partitions are like in his post #14. Very different from the picture.
I don't know what to say.

---

### Post by Leppie on 2009-12-09
Have you tried running scandisk on all partitions in windoze?
ntfs is not the most reliable fs around...

gparted has always worked correctly for me, but if the filesystem tables are messed up it may get wrong results.

---

### Post by gadolinio on 2009-12-09
I'm sorry if i'm missing something, but just to make sure: have you deleted sda3 from gparted? (unmount, delete, click apply, and after the process reading a prompt saying that the partition was succesfully deleted, and then seeing in gparted the unallocated space)

---

