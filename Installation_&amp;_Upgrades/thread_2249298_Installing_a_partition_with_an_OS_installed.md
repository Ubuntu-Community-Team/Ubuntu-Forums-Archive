---
title: "Installing a partition with an OS installed?"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by exodus3 on 2014-10-21
this would be my 2nd thread here  and i really need help wit this one ,,as in put on your "im dealing with a full retard" hat :)

finally got the ubuntu iso file and am ready to install ,i thought about doing an alongside install but since i already know i will be dumping windows  for  forever and 3 days ,,a partition makes more sense eh !!

i have a 250gb  HDD and approx 45-50 of that is in use by windows 

i want to install a partition of around 150gb to put the ubuntu on  and in time erase windows and use that section for storage or whatever 

i have only done a partition once before and that was on a new HDD and it took me a few attempts to get it right ,since i really don't wanna screw up my vista program just yet .i really need something that is pretty much  idiot [me] proof 

my HDD is ntfs  of course 

the bottom icons are for other types of jumps (please see attached screenshot).

---

### Post by Bucky Ball on 2014-10-21
Please attach large pics rather than inserting them into the body of your posts by clicking 'Go Advanced' or 'Adv Reply' and using the paperclip icon. I have done the one in the first post for you.

You are going to need 150Gb of free space if you want 150Gb partition for Ubuntu (and you will also need a 2Gb /swap partition unless you intend to hibernate in which case best to make it the same size or larger than your installed RAM). This means you may need to shrink or delete partitions. The screenshot doesn't tell us much. For NTFS, do all partition resizing of the Windows OS partition with the Windows software.

Best course of action is to select 'Something Else' when you get to the partitioning section of the install and partitioning manually. You'll see your Windows partition(s) clearly. They will be NTFS. Just don't touch them and make sure they are marked as 'Do not use' and Do not format'. 

Goes without saying, but backup anything you don't want to lose prior to commencing your quest in case things go pear-shaped. ;)

[THIS]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") might be of interest. Basic but you'll get the idea.

---

### Post by davit2 on 2014-10-21
Hi, 
while installing you can manage your HDD, also you can use GParted magic which will give you more abilities

---

### Post by Bucky Ball on 2014-10-21
PS: [THIS]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343370#343370") link is probably more appropriate to your situation.

---

### Post by exodus3 on 2014-10-21
>  For NTFS, do all partition resizing of the Windows OS partition with the Windows software.


i am totally in the dark about these programs 

i  have 205gb of free space ,and as far as i know there are no partitions anywhere on my HDD 



> Goes without saying, but backup anything you don't want to lose prior to commencing your quest in case things go pear-shaped.

CMA  this morning

---

### Post by Mark Phelps on 2014-10-21
From your screenshot, it looks like 232GB is in use by Windows, not the amount you claimed.  You will need to shrink that down to make room for Ubuntu.

Do NOT, repeat NOT, use the Ubuntu installer or GParted to do that shrinkage.  Doing so risks corrupting the Windows OS filesystem and rendering it unbootable.

If the Windows is Seven, you can use the Disk Management tool to do the shrinkage.  If it's XP, GParted might work OK, but you could also download and burn a CD from the Minitool Partition Wizard Boot CD, boot from that, and use that to shrink the Windows OS partition.

Either way, do NOT create a new partition with the Windows tool, instead, use the Ubuntu installer to create the partitions in the new unallocated space.

---

### Post by Bucky Ball on 2014-10-21
Gparted works fine with XP. Nothing after that. ;)

---

### Post by exodus3 on 2014-10-21
> From your screenshot, it looks like 232GB is in use by Windows, not the  amount you claimed.  You will need to shrink that down to make room for  Ubuntu.

HDD started out as a 250gb drive,,after installation i had 232gb  with windows using 27gb of space leaving me with 205g free space 

my os is vista ,,what options do i have for creating the partition ??


EDIT:  no idea how much if any this matters,but i will be installing 14.xx LTS desktop

---

### Post by Bucky Ball on 2014-10-21
> **exodus3 said:**
> 

EDIT:  no idea how much if any this matters,but i will be installing 14.xx LTS desktop

Make it 14.04 LTS. 14.** doesn't tell us much. 14.04 LTS is stable and supported.

---

### Post by exodus3 on 2014-10-22
> **Bucky Ball said:**
> Make it 14.04 LTS. 14.** doesn't tell us much. 14.04 LTS is stable and supported.


honestly,i forgot what numbers came after the "."  and was more concerned with getting coffee in me  when i typed that xx  :D

adding additional info,, vista  home premium 32 bit ,, with 3gb ram..

---

### Post by Impavidus on 2014-10-22
> **exodus3 said:**
> HDD started out as a 250gb drive,,after installation i had 232gb  with windows using 27gb of space leaving me with 205g free space 

my os is vista ,,what options do i have for creating the partition ??
The Ubuntu installer doesn't care about the amount of free space on the C partition (that's what it is, the C "drive" is not really a drive but only a partition. Windows always confuses the terms), but it cares about the amount of unallocated disk space. That is the amount of space on the physical disk in your computer that has not been allocated to your C partition or any other partition. Your C partition is 232GB large according to Vista, on a hard drive that is supposed to be 250GB. As it happens, 232GiB=250GB, so I think your drive is really 250GB large and your C partition occupies all of it, with Vista confusing GB and GiB.

You have to find the Windows disk utilities and defragment your C partition (maybe twice). Then use the Windows tool to resize the C partition to make unallocated space after it. Make sure you don't already have 4 primary partitions. Reboot a couple of times to let Windows run its checks. Then you'll have the unallocated space ready for Ubuntu to create its own partitions. You can't use Windows tools to create Ubuntu partitions and using Linux tools to modify Windows partitions is unreliable.

Think about the amount of disk space you need for Windows and Ubuntu. Also consider a shared data partition. Shrink the C partition accordingly.

---

### Post by exodus3 on 2014-10-22
oh boy ^^  that is really greek to me 

i mostly self taught on windows  an have no real education on pc's ..so just about everything you said leaves me in the dust

---

### Post by Bucky Ball on 2014-10-22
Boot Windows>Go to Disk Management (or whatever that is called now)>Shrink the C: partition.

---

### Post by yancek on 2014-10-22
The method on windows 7 and it should be the same on vista is:  
[h=5]Control Panel, Selecting Administrative Tools, Computer Management, Storage, Disk Management, More Actions on the far right then click the arrow to get All Tasks, Shrink Volume and select the volume here[/h]The term 'drive' refers to a physical hard drive.  The term 'partition' refers to a part of the drive.  A partition can take up the entire drive or be divided into multiple parts (partitions).  In your case, you have one drive and it is taken up entirely by one partition on which you have vista installed.  Try the method above to shrink that partition so that you will have unallocated space on which to instal Ubuntu.  Having free space as you do inside your windows filesystem partition will not enable you to install Ubuntu there.  Also, when you get Ubuntu installed your windows will probably still show it as unknown or unallocated as a default windows system does not recognize Linux filesystems.

When you boot Ubuntu to install, select the Something Else option which is the manual install and create a partition of about 25GB for the Ubuntu filesystem, 2-4GB for a swap partition and leave the rest.  Later you can create another partition on which you can share data from windows/Ubuntu.  I would suggest you read through the link below which is a pretty detailed tutorial on installing Ubuntu 14.04 and also has a lot of useful information as well as a link to a tutorial on partitioning.  

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Mark Phelps on 2014-10-22
> **exodus3 said:**
> HDD started out as a 250gb drive,,after installation i had 232gb  with windows using 27gb of space leaving me with 205g free spaceFree space is unused space INSIDE a partition; unallocated space is unused space OUTSIDE a partition.  You need unallocated space to install Ubuntu.  So, you will have to shrink down the Vista partition to make room. 

> my os is vista ,,what options do i have for creating the partition ?Use the Disk Management tool to shrink Vista.  IT will reboot to do it, but it will work.  Do NOT create a new partition using that tool, instead, use the Ubuntu installer to create the partitions.

---

### Post by oldfred on 2014-10-22
Best to defrag Windows at least once, as then shrink goes faster.

Some files may prevent full shrink but you can work around those issues.
 [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

But Windows only runs well if you keep 30% free space inside the NTFS partition, so do not shrink too much. Best to also houseclean and have full backups before installing a new system.

---

### Post by exodus3 on 2014-10-22
well it seems the 1st thing i should is run the defrag ,,most likely run it several times [that's normal for me] 

and then get up to speed on the partitioning

---

### Post by exodus3 on 2014-10-23
> **yancek said:**
> The method on windows 7 and it should be the same on vista is:  
**Control Panel, Selecting Administrative Tools, Computer Management, Storage, Disk Management, More Actions on the far right then click the arrow to get All Tasks, Shrink Volume and select the volume here**




hmm wrong file attached

---

### Post by exodus3 on 2014-10-24
ok i can get to this point ,and now i understand disk shrinking and the risks 
but for the life of me i can't find disk manager  :( WTH is it at ??


[ATTACH=CONFIG]257454[/ATTACH]

---

### Post by Bucky Ball on 2014-10-24
You're using Vista?

[https://duckduckgo.com/?q=open+disk+manager+windows+vista](https://duckduckgo.com/?q=open+disk+manager+windows+vista)

Took two seconds. You should find out how there. If you're using something else, simply change the last word of the search criteria.

---

### Post by oldfred on 2014-10-24
Is your Vista updated with all the service packs?

Some features were only added with the service packs.

---

### Post by exodus3 on 2014-10-24
i have service pack 2  installed ,but the last 2 times i did the updates [during oct] on restart the os wouldn't boot,,so i had to safe boot to last known good configuration 
another reason to run from windows for me

---

### Post by exodus3 on 2014-10-24
well dang ! i was close but the wording threw me .the 1st search result gave me my answer 

also,i am always forgetting about alternative [better] search engines ,dam my google-fu




[ATTACH=CONFIG]257474[/ATTACH]

---

### Post by exodus3 on 2014-10-25
well i did all the work arounds to make the partition, but i just can't make it bigger then 15gb 

at this point i am believe i have some bad sectors which are causing me problems with defragging ??

i have no idea what to do next ??

[ATTACH=CONFIG]257478[/ATTACH]

---

### Post by Mark Phelps on 2014-10-25
Read the material in the link about tips for shrinking Vista:  [http://www.howtogeek.com/tag/windows-vista/]("http://www.howtogeek.com/tag/windows-vista/")

---

### Post by exodus3 on 2014-10-25
i have already used the windows program,,it won't let me shrink the the partition beyond 15gb 

not solved ,but i will mark it as such 


going to head in a differnt direction with this ,just don't know what ATM

---

### Post by Bucky Ball on 2014-10-25
You mean you can't shrink the partition to less than 15Gb or you can't shrink a large partition any more than 15Gb?

---

### Post by exodus3 on 2014-10-26
> **Bucky Ball said:**
> You mean you can't shrink the partition to less than 15Gb or you can't shrink a large partition any more than 15Gb?


i can't shrink the main partition down anymore then 15gb ,even after trying the work arounds link posted earlier in this thread

---

### Post by oldfred on 2014-10-26
We normally do not recommend using gparted to shrink Vista or later Windows, but many have said it works. 
But Windows will require a chkdsk after any resize and if it does not immediately boot, you need a Windows repair CD or Flash drive to run chkdsk. So make that while Vista works.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also there are Windows third party partition tools. They may work better. They have limited free versions that may be all you need or advanced versions that cost.
      
 EASEUS Partition Master - Windows .exe
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by exodus3 on 2014-10-27
well i got crazy and used the mini tool partition program,,and i was successful with no problems 


worst case scenario ?? i'd just go full on ubuntu and get it over with

---

### Post by exodus3 on 2014-10-28
well i spoke too soon  :D  2nd day after the  successful  partitioning ,,the file system became  unreadable    so i am full on ubuntu now .rather  ease into it,but life happens

---

