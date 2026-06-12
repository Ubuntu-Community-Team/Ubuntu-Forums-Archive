---
title: "Couldn't install in the d drive"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by SyAu on 2009-11-15
I'm new to Ubuntu and tried with wubi for a month and really liked Ubuntu. So i want to dual boot it alongside xp. 

Now i'm almost stuck with a problem during installation. I got my xp installed in the c drive and would like to install ubuntu 9.10 in the d drive. This d drive got a total size of 111G and i want to allocate 25G for xp related data and allocate the remaining to ubuntu.

During installation, basically i was expecting to select the d drive and use the following option 'Install them side by side, choosing between them at each startup' and using the drag option to resize the d drive to 25G for xp and remaining for ubuntu. But i'm not getting this option but all the remaining three options (Erase and use the entire disk, use the continuous large space and specify partitions manually).

Please assist me to fix this.

---

### Post by coffeecat on 2009-11-15
Boot up the live CD and go to System > Administration > Gparted. Use that to resize your D: partition. It won't show as 'D:' because C:, D:, etc is a bit of Microsoft nonsense dating back to ms-dos days and not shared by *real* OSs. :wink: Your C: will probably show as sda1 and D: as sda2, unless you have a recovery partition of some sort. If you are in any doubt, post back with some details - preferably a screenshot - and we can take it from there.

If you are confident that you have identified which is your D: partition, you can use Gparted to resize it, leaving unallocated space for Ubuntu. Then you can start the installer again and use the 'use continuous free space' option at the partitioning stage. You should be able to do the resize in the manual option, but the above way using Gparted might be a bit more straightforward.

**Edit:** just a thought. By resizing your D: to 25G, that will leave about 80+GB for Ubuntu. That's quite a lot. You could use your D: partition in Ubuntu to store data as well - it will be called something else - so you could have one partition to store data shared by both OSs. This is what I do - Ubuntu read/writes NTFS quite reliably. So you might want to think about a bigger data partition and a smaller Ubuntu root partition. Once you get installed, post back and someone can tell you how to access the NTFS data partition, or tell you how to do a simple system file edit to have the partition mounted on bootup.

And, by the way, as a default you'll end up with two Ubuntu partitions - a large root (/) and a smaller swap.

---

### Post by darkod on 2009-11-15
Boot with the ubuntu cd and select Try Ubuntu option. Go into System -> Administration and open Gparted.
That will allow you to manage the existing partitions.
Select the 111GB partition and shrink it to 25GB if that is what you want. That will leave free spave to the right (after) the partition.

Then boot again with the ubuntu cd and select Install Ubuntu and you can use the automated method telling it to use the free space you just created, or create / (root), swap and if you want /home manually.

Did you deinstall wubi (ubuntu) from windows add/remove programs? You need to do that and it will also free space in your windows partitions.

Note: The partition shrinking involves some level of risk for the data on it. Sometimes things don't go as expected. It is advisable to have whole D: backed up before starting this.

---

### Post by SyAu on 2009-11-16
> **coffeecat said:**
> Boot up the live CD and go to System > Administration > Gparted. Use that to resize your D: partition. It won't show as 'D:' because C:, D:, etc is a bit of Microsoft nonsense dating back to ms-dos days and not shared by *real* OSs. :wink: Your C: will probably show as sda1 and D: as sda2, unless you have a recovery partition of some sort. If you are in any doubt, post back with some details - preferably a screenshot - and we can take it from there.

If you are confident that you have identified which is your D: partition, you can use Gparted to resize it, leaving unallocated space for Ubuntu. Then you can start the installer again and use the 'use continuous free space' option at the partitioning stage. You should be able to do the resize in the manual option, but the above way using Gparted might be a bit more straightforward.

**Edit:** just a thought. By resizing your D: to 25G, that will leave about 80+GB for Ubuntu. That's quite a lot. You could use your D: partition in Ubuntu to store data as well - it will be called something else - so you could have one partition to store data shared by both OSs. This is what I do - Ubuntu read/writes NTFS quite reliably. So you might want to think about a bigger data partition and a smaller Ubuntu root partition. Once you get installed, post back and someone can tell you how to access the NTFS data partition, or tell you how to do a simple system file edit to have the partition mounted on bootup.

And, by the way, as a default you'll end up with two Ubuntu partitions - a large root (/) and a smaller swap.

During installation, under 'Erase and use the entire disk', these 2 partition entries are present  
'SCSI1(0,0,0) (sda)-120.0GB ATA FUJITSU MHV212OB' (which refers C drive) and 
'SCSI3(0,0,0) (sdb)-120.00GB ATA FUJITSU MHV212OB' (D drive).

For 'SCSI3(0,0,0) (sdb)-120.00GB ATA FUJITSU MHV212OB', the only option available is 'Erase and use the entire disk'. ie. the option you mentioned 'Use the largest continuous free space' is only available for 'sda'-C drive not for 'sdb'-D drive. 

In this situation, I believe after using  Gparted to resize the D drive, I would be left with only the 'Erase and use the entire disk' option for the newly created partition. I wouldn't be in a position to use the 'Use the largest continuous free space' option, since whenever i select this it considers the C drive partition. I would like to confirm this before doing the partitioning on D drive.

---

### Post by SyAu on 2009-11-16
> **darkod said:**
> Boot with the ubuntu cd and select Try Ubuntu option. Go into System -> Administration and open Gparted.
That will allow you to manage the existing partitions.
Select the 111GB partition and shrink it to 25GB if that is what you want. That will leave free spave to the right (after) the partition.

Then boot again with the ubuntu cd and select Install Ubuntu and you can use the automated method telling it to use the free space you just created, or create / (root), swap and if you want /home manually.

Did you deinstall wubi (ubuntu) from windows add/remove programs? You need to do that and it will also free space in your windows partitions.

Note: The partition shrinking involves some level of risk for the data on it. Sometimes things don't go as expected. It is advisable to have whole D: backed up before starting this.

Yes i did uninstall wubi

---

### Post by darkod on 2009-11-16
I haven't been in this exact situation, but after you shrink D: (sdb) partition, I think you will be able to use 'Use largest available free space' option because shrinking sdb will create exactly that, free space.
Now you don't have any free space because the whole drive is used by the two windows partitions, C: and D:, or better sda and sdb.

---

### Post by TheHimself on 2009-11-16
What darkold says is correct. In the installer "free" means "not in a partition". 
You should NEVER choose any install option that involves "erase" unless you really want to get rid of some files/programs/OS you already have on your disk.

---

### Post by coffeecat on 2009-11-16
> **darkod said:**
> I haven't been in this exact situation, but after you shrink D: (sdb) partition, I think you will be able to use 'Use largest available free space' option because shrinking sdb will create exactly that, free space.

Agreed. But I think what is confusing the OP is that the Karmic installer is subtly changed from previous versions. I noticed this when doing a quick fresh installation of Karmic yesterday - as you do! :wink: *

Previous versions of the installer had a "use largest continuous free space" or words to that effect as one of the choices at the partitioning stage. But what I saw yesterday (this from memory) is something like:

1. - Install alongside existing OS.
2. - Use the whole drive.
3. - Manual.

I would imagine (hope) that choice 1 would detect any unallocated space and offer to install in that.

**SyAu**, why not try that and see what happens. No changes are made to the hard drive until later when you asked to review your choices and commit. You can back out at any time before then if you are not sure.

I'll have a look around if I get a moment and see if I can find more on the Karmic installer. 

* **Irrelevant footnote:** a message to all the moaning Minnies who are loathe to do a fresh installation because of all their carefully set up personal configurations, etc. The fresh install of Karmic (posting from there now) to a spare partition on my laptop was because my Karmic install was a fully-updated Alpha and I wanted to see if a fresh install with the final CD solved one or two very minor issues. Anyway - total install time from inserting the CD to getting a fully-updated, fully-configured, all my favourite apps installed, Firefox bookmarks imported and Adblock Plus installed, nicely themed, etc, etc, etc: **less that an hour**. *And*, I made myself supper at the same time. Granted, I copied all the .debs from /var/cache/apt/archives from my main desktop to this to save bandwidth, but even so. Beat that in Windows - or even with MacOS. :)

---

### Post by darkod on 2009-11-16
I haven't done too many installs because I just entered ubuntu now with the 9.10 version, but I believe I actually saw 'use largest continuous free space' in the partitioning screen.

Didn't pay too much attention coz I always like manual control of partitions, but I think the choice was there. Strange...

PS. We can't know for sure what the OP tried or not, but according to the title of the thread and other similar threads I've seen, I think many people actually try to install inside D: (/dev/sdb) partition thinking that if they have unused space there it can just work like that.

---

### Post by coffeecat on 2009-11-17
> **darkod said:**
> Didn't pay too much attention coz I always like manual control of partitions, but I think the choice was there. Strange...


I've done some experimenting, and it seems we were both right - but depending on conditions. I was wrong to say the Karmic installer was subtly changed. The 'subtle change' was the state of the hard disc I was offering it. :oops:

When I got to the partitioning stage of the installer on a machine with no unallocated space, I was give only three options. I took careful notes this time. :p They were:

- Install them side by side, choosing between them each startup.
- Erase and use the entire disk.
- Specify partitions manually (advanced).

But when I ran it with some unallocated space at the end, I got four options:

- Install them side by side, choosing between them each startup.
- Erase and use the entire disk.
- **Use the largest continuous free space**.
- Specify partitions manually (advanced).

Which makes sense - the option is only given if you actually have some free space. The trouble is, the free space on that occasion was less than 1GB - not nearly enough. The installer wasn't intelligent enough to warn the user at that point - hopefully it does so later.

Anyway, if the OP has followed the advice to free up some space, they should be offered the 'continuous free space' option.

And it's cleared up a puzzle for me. Like you, I always use the manual option and never take much notice of the others.

---

### Post by SyAu on 2009-11-18
Thanks for all the inputs so far.

I'm planning do the following,

1) Using Gparted to create a new partition from sdb (d drive)
2) Click 'Install', under 'Prepare disk space', select the newly created partition under 'Erase and use the entire disk', click 'Forward' and complete the installation.   

With these operations, will i be able to achieve,
1) No problems for xp
2) No problems for existing xp data
3) Dual boot option during startup. (Since with the current setup, I'm not seeing 'Install them side by side, choosing between them each startup')

---

### Post by SyAu on 2009-11-19
> **darkod said:**
> I haven't been in this exact situation, but after you shrink D: (sdb) partition, I think you will be able to use 'Use largest available free space' option because shrinking sdb will create exactly that, free space.
Now you don't have any free space because the whole drive is used by the two windows partitions, C: and D:, or better sda and sdb.

:D Thanks for everyone. Finally i installed ubuntu. Here's the summary of what i did,

1) Used Gparted to resize my sdb (d drive) to have some unallocated space.
    So i ended up with 30G in ntfs (for xp data) and 80G unallocated space. I didn't  do       anything more in Gparted.

2) Then clicked the 'Install' icon in the desktop, in the 'Prepare disk space' window, selected '... sdb ...' item under 'Erase and use the entire disk'. 

Now i got different information like,
'This computer has no operating systems on it' 
In a graphical chart, '/dev/sdb1/   30G' and 'free space 80G'

Next i selected 'Use the largest continuous free space' option and clicked 'Forward' and completed the installation.

---

### Post by robjmarquez on 2009-12-19
Ok, this may be an old thread, but I have similar issue. New HP EliteBook, running XP, when I try to install from LiveCD or just from the boot menu ubuntu gives, I can see my XP disk (250GB), but gparted will not allow me to re-size the XP partition and it does not see the OS to give me any other option except to format the whole drive and use it for ubuntu. 
I tried to use ntfsresize, but it says the disk isn't mounted. I can see the disk via dmesg as /dev/sda1.

My only other option is to use an external usb hdd, which I am going to try tonight (fingers crossed) and see how that works. But I really want to install this on the internal drive. And I cannot blow away the XP image, it is my employer's laptop. ;-) 

Let me know if there is anything you'd like to see as far as more info from the drive etc...

Thanks!

---

### Post by coffeecat on 2009-12-19
> **robjmarquez said:**
> Ok, this may be an old thread, but I have similar issue.

It sounds as though gparted may be having problems with your partition table, but let's get some more information. If you boot up with the live CD, can you get an internet connection and post from there? If so, open  a terminal and post the output of these two commands:

```
sudo fdisk -l
sudo parted -l
```I want to see if parted and fdisk detect the same thing - parted is the backend to Gparted. You'll need to use a copy and paste from the terminal, and please enclose the output in [noparse]```

```[/noparse] tags in order to keep the formatting.

Next thing:

> **robjmarquez said:**
> I can see my XP disk (250GB), but gparted will not allow me to re-size the XP partition and it does not see the OS to give me any other option except to format the whole drive and use it for ubuntu.

What exactly does it see? Perhaps you could post a screenshot of Gparted. This won't provide any more information than 'sudo parted -l' but it would be useful to see what you are seeing. In the live session, open Gparted and press ALT+PrtScr to get the screenshot and attach it to your post using the 'Manage Attachments' button below the message field.

When you say Gparted will not allow you to resize the XP partition, what do you mean? Do you get an error?

---

