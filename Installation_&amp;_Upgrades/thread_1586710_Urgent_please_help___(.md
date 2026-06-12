---
title: "Urgent please help  : ("
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by mrhank on 2010-10-02
Ok guys, i really messed up this time! I'm desperate here so please help me out. Yesterday I tried installing ubuntu studio, I have 4 hard disks each with 500gigs. In the installation process I chose to install U-Studio on hard disk D, where i had nothing. So at the end of the process the Installation tells me it need to install GRUB, I've had some bad experience in the past with GRUB so I totally FREAK OUT and choose not to install GRUB. Now before all this it tells me that it will format my drive D which was ok since I had nothing on it but after installation finishes U-Studio won't start and I CANNOT dual boot into Windows. This is where the massive panic starts, I had MY PICS AND VIDS(which are precious to me and yes i know i should've backed everything up, STUPID!!!) located in disk C where windows was installed! After windows won't start I insert the Windows installation disk and try to repair my pc...but nothing. So at this point I decide to install windows again, but in the installation process where i had to choose where to install windows it turns out that I couldn't choose any of my hard disks because it said that none of them were NTFS!!! I don't know what happened, I only chose hard disk DDDDD why did it format all 4 of them??? Ok so i use g-parted to format 1 into NTFS, i install windows and now i can see 3 of my hard disks...1 is missing and i am praying to god it's the one where i had all my stuff in. I attached a picture of what Disk Manager shows me, and I think i have way too many partitions there. Someone please help ME!!!  :' (
 
If you need any more info pls let me know...thnx...  : (

---

### Post by luvshines on 2010-10-02
You should try the testdisk utility.

It has proved to be a real magician in such cases

Install testdisk, run it and do a deep scan of your HDD
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by nlsthzn on 2010-10-02
I am unfortuntly very much a noob however I notice that almost all of the partitions are indeed showing as NTFS... can you access them from Windows?

---

### Post by mrhank on 2010-10-02
> **nlsthzn said:**
> I am unfortuntly very much a noob however I notice that almost all of the partitions are indeed showing as NTFS... can you access them from Windows?

Yes I can access 3 of them. 1 is still missing. It shows in the Disk Manager but I cannot access it.

---

### Post by nlsthzn on 2010-10-02
> **mrhank said:**
> Yes I can access 3 of them. 1 is still missing. It shows in the Disk Manager but I cannot access it.
 
Sorry if you did mention it (maybe I missed it) but which of your drives can you not access?  What was on the drive and what did you do with that specific drive?

---

### Post by mrhank on 2010-10-02
> **nlsthzn said:**
> Sorry if you did mention it (maybe I missed it) but which of your drives can you not access?  What was on the drive and what did you do with that specific drive?

In the picture you can see that E has a 2gig Capacity, while the 2 drive from top to bottom(no name) is the correct 500g disk. That disk is partitioned in 2, one has the linux swap in it(which i really don't know what it means) and the other is apparently free. Which i hope is not the case cause if it is im screwed.  =s

---

### Post by mrhank on 2010-10-02
> **luvshines said:**
> You should try the testdisk utility.

It has proved to be a real magician in such cases

Install testdisk, run it and do a deep scan of your HDD
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Thnx for the reply bro. I tried to use the testdisk thing but I only ended up making it worse. Now I can't start windows again. I am currently attempting a repair with Win disc. In the link you sent me it DOES say that it can recover files...I just didn't understand how? I'm too much of a noob for all this :(

---

### Post by raymondh on 2010-10-02
MrHank ...

First, a caveat.  It's been a while since I've manipulated/reconfigured my linux install so if anyone deems what I say as wrong ... no offense taken.  As usual, wait for for someone to either correct or chime in.

The windows bootloader will not load (boot) linux....unless we've got new scripts in the Kernel to do so now.  Some time ago, we needed GRUB to boot both Linux and Windows.  I don't know your 'bad' grub experience so I won't go there.

Since windows is your primary OS, let's try to get the booting.  have you tried to repair or fix the MBR?  If not, tell us :

- which windows OS are you using
- Do you have an original windows install disc (not the recovery disc)

See what Tavis and vegas techgeek [recommended]("http://www.astahost.com/info.php/Bootloader-Problem_t11250.html") in steps

Let's start from there.

Regards

---

### Post by mrhank on 2010-10-02
Raymond; I am using Windows 7 as my main OS. I thought I could install Ubuntu Studio just like Ubuntu Lucid with wubi...but i don't know what I did wrong but the thing is my most important files, pics and vids are either lost or gone. If you see in the pic i attached, there is one 500g disk that is not where it's suppose to be. The second from top to bottom. For some reason windows recognized a 2gig partition(don't know where it came from) instead of my 500g. I'm guessing that Ubuntu Studio installation formatted it and it is not NTFS. But I don't want to touch it because my files might be there. Is there a way to convert a disk to NTFS without having to format it???

---

### Post by nlsthzn on 2010-10-02
> **mrhank said:**
> Raymond; I am using Windows 7 as my main OS. I thought I could install Ubuntu Studio just like Ubuntu Lucid with wubi...but i don't know what I did wrong but the thing is my most important files, pics and vids are either lost or gone. If you see in the pic i attached, there is one 500g disk that is not where it's suppose to be. The second from top to bottom. For some reason windows recognized a 2gig partition(don't know where it came from) instead of my 500g. I'm guessing that Ubuntu Studio installation formatted it and it is not NTFS. But I don't want to touch it because my files might be there. Is there a way to convert a disk to NTFS without having to format it???
 
Seeing as we are dealing with "sensitive" data that may still be avaiable I am going to back down as I am not 100% sure what would be the best course of action... I will monitor the thread to learn and hope you all the best to get back your files... BACKUP BACKUP BACKUP next time... ;)

---

### Post by raymondh on 2010-10-02
> **mrhank said:**
> Raymond; I am using Windows 7 as my main OS. I thought I could install Ubuntu Studio just like Ubuntu Lucid with wubi...but i don't know what I did wrong but the thing is my most important files, pics and vids are either lost or gone. If you see in the pic i attached, there is one 500g disk that is not where it's suppose to be. The second from top to bottom. For some reason windows recognized a 2gig partition(don't know where it came from) instead of my 500g. I'm guessing that Ubuntu Studio installation formatted it and it is not NTFS. But I don't want to touch it because my files might be there. Is there a way to convert a disk to NTFS without having to format it???

re-reading your first thread ....

1.  When you could not boot into neither Ubuntu nor Windows, did you re-install windows?  If yes, re-installing windows means that you wipe out any existing data on the HD to write a new OS unto. 

2.  When you re-install windows (if you did), windows likes to be the first OS on disc.  For some reason, you chose to retain (or chose to have a) 'dynamic' volumne.  Dynamic (as I know it) is often used in raid configurations, etc. which "ties" up the various HD's into one. 

If my hunch is right, re-installing windows meant that it had reformatted the HD, effectively writing over any existing data.  Having retained a dynamic configuration meant that it re-wrote over the whole HD.

I think you're open to suggestions and here's a wild one.  Of course, understand that the more you use your computer now, the more you write over the HD.

1.  Boot into a Ubuntu (or linux) install CD.
2.  Select "TRY UBUNTU....." which is also known as a live session.
3.  In live sesssion, when you get a desktop, go to PLACES and see if you can access your other HD's.  Click on them and see what data it has.  If you do find your data, transfer them to an external HD.

Other than that, all I can think of now is to get a professional data recovery service.

I will google other options and post back any outcome.

Couple of questions :

1.  Were you in RAID or DYNAMIC configuration prior to installing Ubuntu?  
2.  Did you choose to go dynamic when you installed Ubuntu studio?

---

### Post by mrhank on 2010-10-02
I found a solution... [www.recovering-deleted-files.net](www.recovering-deleted-files.net)  I found a video on youtube with instructions on hoy to recover deleted files even when formatted. It's a lifesaver!!! It works prefectly and I have my files back!   =D   thnx for all the replies guys!!!!

---

### Post by nlsthzn on 2010-10-02
> **mrhank said:**
> I found a solution... [www.recovering-deleted-files.net]("http://www.recovering-deleted-files.net")  I found a video on youtube with instructions on hoy to recover deleted files even when formatted. It's a lifesaver!!! It works prefectly and I have my files back!   =D   thnx for all the replies guys!!!!

AWESOME!

[SIZE=1](Now be a good boy and mark your thread as solved :D)[/SIZE]

---

