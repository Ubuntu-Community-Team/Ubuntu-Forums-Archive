---
title: "Triple boot ubuntu 12 with windows 7 and Mac OS X Lion. Need partition help."
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by acerbuntu on 2012-11-20
Hi guys,

Need help with the partitions to install ubuntu 12.

I bought Acer aspire 5755G UK model recently with windows 7 having two partitions where the first partition contains windows files and second partition was for data. From there I straight away install Mac OS X Lion install on second (data) partition. As I am able to do dual boot without any problems with both the operating systems. Now for me it is time to have Ubuntu for my work purpose, so I wanted to know whether I can triple boot ubuntu along with other 2 operating systems without messing partitions.

I wanted to know because I know there may exist problem with partition type and status.Here below i am attaching my disk management window screenshots taken from windows 7 and ubuntu live disk.

please advice me.

Many Thanks in Advance.

---

### Post by Bucky Ball on 2012-11-20
Where do you intend to install it? You have the disk full and no free space!

You also have four partitions and that is the limit. You will get into trouble if you attempt to create anymore. Someone may be able to help you with this but it is a quagmire I'm yet to have the need to get involved with. 

So, you need to shrink the Win partition and delete the Mac OSX, or vice versa, and create free space. You need three partitions and free space enough to fit Mac and Ubuntu (not sure if Mac runs on anything but a primary partition, though) into an extended partition.

With the free space, create an *extended partition*. Inside that extended partition you are going to need to create 'logical drives' (partitions) for MAC OS and Ubuntu (Ubuntu will need two, three if you intend a separate /home partition but you have a data partition you can link your personal stuff to which we can tell you about later).

---

### Post by acerbuntu on 2012-11-20
> **Bucky Ball said:**
> Where do you intend to install it? You have the disk full and no free space!

You also have four partitions and that is the limit. You will get into trouble if you attempt to create anymore. Someone may be able to help you with this but it is a quagmire I'm yet to have the need to get involved with. 

So, you need to shrink the Win partition and delete the Mac OSX, or vice versa, and create free space. You need three partitions and free space enough to fit Mac and Ubuntu (not sure if Mac runs on anything but a primary partition, though) into an extended partition.

With the free space, create an *extended partition*. Inside that extended partition you are going to need to create 'logical drives' (partitions) for MAC OS and Ubuntu (Ubuntu will need two, three if you intend a separate /home partition but you have a data partition you can link your personal stuff to which we can tell you about later).
Hi Bucky Ball,

Thank you for your reply.  You're right, that's what I am afraid to do. As you mentioned also believe that mac doesn't run on any other partition except primary. However I can still shrink some about of space from windows partition in which it will be unallocated space.

If you take from clean hard drive then after installing windows using acer recovery dvd there will be three partitions like recovery system reserved and windows. So from there I've to shrink and make another partition for data.

So do you think I can make it if I start from empty hard disk.If so I can back up and start.

So I am ready to start from the scratch if you have time to guide me. 

Many Thanks.

---

### Post by Bucky Ball on 2012-11-20
I'm  about to go to bed (in Australia) but others may well jump in and I'll be around tomorrow. If you can figure out a plan that involves two or at most three primary partitions for your Windows and Mac OSX and enough room to create an extended partition which will hold Ubuntu and its /swap partition, plus your data partition on logical partitions inside the extended partition, you are on your way. Be aware that your data partition needs to be NTFS for all three OSs to recognise it and read and write to it.

Yep, a clean hard drive would be a good place to start. With my old HP I made backup recovery disks for Windows (should be an option to do that) then wiped the lot. Installed Win7 back on a 30Gb partition and the rest became one large extended partition with everything else in there. 

Incidentally, Ubuntu will run on a logical partition inside an extended partition without any issue. ;)

PS: You may get some more clues here:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=triple+boot+mac+win+ubuntu&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=triple+boot+mac+win+ubuntu&ql=)

---

### Post by acerbuntu on 2012-11-20
> **Bucky Ball said:**
> I'm  about to go to bed (in Australia) but others may well jump in and I'll be around tomorrow. If you can figure out a plan that involves two or at most three primary partitions for your Windows and Mac OSX and enough room to create an extended partition which will hold Ubuntu and its /swap partition, plus your data partition on logical partitions inside the extended partition, you are on your way. Be aware that your data partition needs to be NTFS for all three OSs to recognise it and read and write to it.

Yep, a clean hard drive would be a good place to start. With my old HP I made backup recovery disks for Windows (should be an option to do that) then wiped the lot. Installed Win7 back on a 30Gb partition and the rest became one large extended partition with everything else in there. 

Incidentally, Ubuntu will run on a logical partition inside an extended partition without any issue. ;)

PS: You may get some more clues here:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=triple+boot+mac+win+ubuntu&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=triple+boot+mac+win+ubuntu&ql=)
Thanks bucky,

I'll try and let you know. However I don't need any data partition as i will be using ext drive for data.

Good night Sleep tight.
Catch u tomorrow.

---

### Post by Bucky Ball on 2012-11-20
Cheers. 

[QUOTE=acerbuntu]However I don't need any data partition as i will be using ext drive for data.[/QUOTE]

Even better. You should be good to go then! Three primaries and an extended or four primaries max and your good. 

As mentioned, Ubuntu with two partitions is fine and this creates a /home directory inside / (the Ubuntu OS partition). This will contain directories like Documents, Music, Video, etc. These can easily be deleted and symlinked to directories on your data partition or anywhere else. Of course, you will need to have the external on all the time (for instance, if you change the desktop wallpaper to an image stored on the data partition, there well be no wallpaper if you boot without the external on. 

Fine in a 'always on' situation, say a NAS device or a server proper. Annoying otherwise.

Not sure what size OSX or your version of Win needs, but 20Gb partition at most is fine for Ubuntu, 2Gb for its /swap. I'm thinking that is going to leave you with a fair bit of empty space on the internal drive if they are all using the same data partition ...

---

### Post by acerbuntu on 2012-11-21
> **Bucky Ball said:**
> Cheers. 



Even better. You should be good to go then! Three primaries and an extended or four primaries max and your good. 

As mentioned, Ubuntu with two partitions is fine and this creates a /home directory inside / (the Ubuntu OS partition). This will contain directories like Documents, Music, Video, etc. These can easily be deleted and symlinked to directories on your data partition or anywhere else. Of course, you will need to have the external on all the time (for instance, if you change the desktop wallpaper to an image stored on the data partition, there well be no wallpaper if you boot without the external on. 

Fine in a 'always on' situation, say a NAS device or a server proper. Annoying otherwise.

Not sure what size OSX or your version of Win needs, but 20Gb partition at most is fine for Ubuntu, 2Gb for its /swap. I'm thinking that is going to leave you with a fair bit of empty space on the internal drive if they are all using the same data partition ...
Hi bucky,

How are you today?.

I did manage to get ubuntu on windows shrink partition without disturbing other partitions.So now I am able to boot only windows and ubuntu but not mac os x. Anyways I try and sort out the triple boot issue later.Once I figure all hardware and power issues so then I can start doing fresh install on clean hard drive.

For now I am in-to my Ubuntu 12.10 interface and its time to check hardware and acpi issues.
By the way I forgot to ask the partition sizes required for ubuntu 12.10 install. Because I did 4 partitions (root 16GB, home 22GB, Swap 2GB, /boot 1GB) of total 41GB. I was bit confused by looking into various threads.

Finally after getting into ubuntu 12.10 the first problem is my brightness issue where the slider works with no change and I fixed it but still the brightness resets to max after every reboot.And also the brightness slider in system preferences does not change when using Fn keys.

After that I checked sound, WiFi and Ethernet where all are OK.

Now I checked connecting and disconnecting AC supply but there was no change in brightness levels.

I still have to check HDMI, VGA, USB 3.0 and some other things. I don't know exactly how to start with.

Many thanks.

---

### Post by Bucky Ball on 2012-11-21
Terrific you have gotten this far. I would/should have recommended 12.04 LTS for a smoother ride. It is a long-term support release, supported until April 2017 and very stable. Anyhow.

Yep, separate /home is good but remembering that is probably formatted as EXT4 and not accessible by any of the other OSs (not Win and I don't think OSX). You really need a shared partition if you are going to go that way (NTFS is best rather than FAT).

Post separate threads about the other issues, yes, and good luck with it all. Enjoy the beast you have created, the learning curve, the OS(s) and see you about the forums.

Please mark thread as Solved to help others if you feel it is. ;)

---

### Post by acerbuntu on 2012-11-21
> **Bucky Ball said:**
> Terrific you have gotten this far. I would/should have recommended 12.04 LTS for a smoother ride. It is a long-term support release, supported until April 2017 and very stable. Anyhow.

Yep, separate /home is good but remembering that is probably formatted as EXT4 and not accessible by any of the other OSs (not Win and I don't think OSX). You really need a shared partition if you are going to go that way (NTFS is best rather than FAT).

Post separate threads about the other issues, yes, and good luck with it all. Enjoy the beast you have created, the learning curve, the OS(s) and see you about the forums.

Please mark thread as Solved to help others if you feel it is. ;)
Hi Bucky,

Thanks for your great advice. It really helped me a lot. Any way I will get 12.04 LTS and check if it works more.

So now I am going to do clean install within 100GB partition space and would like to know the partition size for each one (like home, root, swap, boot) as you forgot to reply. By the way in some guides I don't find people using /boot.Do you think it is necessary.

What is the difference between 12.10 vs 12.04LTS?. Do they vary in huge things?.

Sorry which one do you recommend 32bit or 64bit?

My System Specs are as follows:

Screen Size          15.6 inches
Processor Type       Intel Core i5 
Processor Speed      2.5 GHz (Turbo boost upto 3.1GHz)
Memory RAM Size      8 GB
Computer Memory Type DDR3 SDRAM
Hard Drive Size      750 GB
Graphics Card        DescriptionNVIDIA GeForce GT 630M
Graphics Card Ram Size 1 GB VRAM
Pioneer DVD Super Multi DL Drive
HDMI out
USB 3.0
Audio Combo Jack
Acer Crystal HD Webcam
Average Battery Life (in hours)4.5 hours

Many Thanks.

---

### Post by Bucky Ball on 2012-11-21
64bit. That is AMD64 which is for all 64bit machines, Intel and AMD (some people get a bit confused by that).

/ = root, OS, 20Gb is plenty;
/home = large as you like as this needs to hold all personal data, e.g. music, vids, documents, etc.;
/swap = 2Gb is fine.

As for the /boot partition, I used one in the first install (back in 2007) and have never used one since. If you do use one it doesn't need to be big but you will need to research that.

The biggest difference is that 12.04 LTS is a long term support release (five years) and 12.10 is not (18 months). Incidentally, 12 = 2012, .04 = April. So it was released in April 2012 and is therefore more stable as older than 12.10 (for some people but this depends a lot on hardware). 12.10 may also have some slightly newer versions of some apps. Again, you might want to dig deeper about the differences but essentially they are pretty similar. 

Personally, a stable install is essential so I always run an LTS as my main squeeze and have three other partitions for my playthings (12.10 and 13.04 will soon occupy two of these partitions). Take note that all installs can use the same /home and /swap partitions so you don't need to create for each. 

I have a partition for data and use that as 'home' by stealth! Basically I create a 20Gb / partition and /swap, in which case Ubuntu automagically creates a /home *directory* in / rather than a partition. I then delete the folders in there (documents, music etc but NOT hidden folder or the Desktop folder) then symlink the existing documents, music, etc folders in the data partition so a shortcut to them appears in the /home directory. Voila! That way, you can have three installs and everything in all three /home directories is identical. 

Good luck. Ubuntu provides many options so you might like to have a beverage and sit with a pencil and paper to plan exactly how you're going to go about it. ;)

---

### Post by acerbuntu on 2012-11-22
> **Bucky Ball said:**
> 64bit. That is AMD64 which is for all 64bit machines, Intel and AMD (some people get a bit confused by that).

/ = root, OS, 20Gb is plenty;
/home = large as you like as this needs to hold all personal data, e.g. music, vids, documents, etc.;
/swap = 2Gb is fine.

As for the /boot partition, I used one in the first install (back in 2007) and have never used one since. If you do use one it doesn't need to be big but you will need to research that.

The biggest difference is that 12.04 LTS is a long term support release (five years) and 12.10 is not (18 months). Incidentally, 12 = 2012, .04 = April. So it was released in April 2012 and is therefore more stable as older than 12.10 (for some people but this depends a lot on hardware). 12.10 may also have some slightly newer versions of some apps. Again, you might want to dig deeper about the differences but essentially they are pretty similar. 

Personally, a stable install is essential so I always run an LTS as my main squeeze and have three other partitions for my playthings (12.10 and 13.04 will soon occupy two of these partitions). Take note that all installs can use the same /home and /swap partitions so you don't need to create for each. 

I have a partition for data and use that as 'home' by stealth! Basically I create a 20Gb / partition and /swap, in which case Ubuntu automagically creates a /home *directory* in / rather than a partition. I then delete the folders in there (documents, music etc but NOT hidden folder or the Desktop folder) then symlink the existing documents, music, etc folders in the data partition so a shortcut to them appears in the /home directory. Voila! That way, you can have three installs and everything in all three /home directories is identical. 

Good luck. Ubuntu provides many options so you might like to have a beverage and sit with a pencil and paper to plan exactly how you're going to go about it. ;)
Oh no!!!. I installed AMD64bit two times (12.10 and 12.04LTS). I knew that the title of the download file is AMD and some where I have in mind that it was not for intel but still it was in same location along with 32bit.So I was also bit confused, anyway my laptop is now running on 12.04LTS amd64 bit.

Do you think I may have problems of using amd64bit OS on intel 64bit machine?. Because for the last 12hrs I did had 3-4 internal errors reporting.Are there any 64bit for intel?.

By the way I fixed Brightness issue with executable script. So I got couple of things to get sorted.

Many Thanks.

---

### Post by Bucky Ball on 2012-11-22
No. Wrong track. Don't go there. That is what I mentioned. AMD64 ISO is for ***both*** Intel and AMD 64bit processors. I also mentioned people got confused about that ... which is why I mentioned it. 

The problems are not related to that. Look elsewhere and I advise you to mark this thread as solved and post a new one(s) with a descriptive title(s) for any further issues. Don't post one thread about several issues, one for each. You will increase your chances of us helping you and avoid confusion. ;)

Good luck.

---

### Post by acerbuntu on 2012-11-22
> **Bucky Ball said:**
> No. Wrong track. Don't go there. That is what I mentioned. AMD64 ISO is for ***both*** Intel and AMD 64bit processors. I also mentioned people got confused about that ... which is why I mentioned it. 

The problems are not related to that. Look elsewhere and I advise you to mark this thread as solved and post a new one(s) with a descriptive title(s) for any further issues. Don't post one thread about several issues, one for each. You will increase your chances of us helping you and avoid confusion. ;)

Good luck.
Alright Bucky. I got u. Confused before while reading your reply. Now  everything is clear for me.

Now I'm going to mark this thread as solved. 

Thank you very much for your time and support.

Have a nice weekend.

Catch you later. Bye.

---

### Post by Bucky Ball on 2012-11-22
Happy to help and catch you round the forums ... ;)

---

