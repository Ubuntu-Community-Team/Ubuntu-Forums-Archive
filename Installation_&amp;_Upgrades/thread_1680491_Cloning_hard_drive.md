---
title: "Cloning hard drive"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Antarctica32 on 2011-02-02
My current HDD is only 60GBs and have a 180GB HDD that I want to clone EVERYTHING to. I have no clue how to do this, and I need a lot of help. I am running Lucid Lynx on my desktop. All help of any kind is greatly appreciated.

---

### Post by hansolo4949 on 2011-02-02
Okay, this is ONE way to do it:

First of all, open up two windows, one with your 180GB hdd in it, the other with your 60.

Click on the top file in the 60GB HDD, scroll down to the bottom, hold shift, and clikc on the bottom file. Everything should now be selected. Now, just drag and drop the files onto the 180GB hdd!

---

### Post by coffeecat on 2011-02-02
I presume you mean that you want to clone not just the files, but partitions, filesystems and the partition table.

One way would be with the terminal dd command, but you'd need to do this from a live CD or live USB if your current install is on the 60GB HD. You shouldn't clone a system from inside a system. Or, at least, you are in danger of getting inconsistent results if you do. Be warned that cloning 60GB with dd will take several hours.

The other way would be with clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

I've not used myself so I can't do more than point you to it, but there are a lot of good reports about it on the forum.

---

### Post by 0))) on 2011-02-02
Clonezilla is a great tool and one i would recommend, dd is the old school method but my motto is work smarter, not harder, and clonezilla will deal with all parts of the imaging process. Grab the liveCD version of it, run it on your machine, attach the new 180G harddrive and image the 60G harddrive to it using clonezilla's toolset. To avoid redundancy ill just direct you to a tutorial.
[http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla](http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla)

For the sake of completeness, the dd tool from the gnu core-utils is and has been used for years for this purpose, although as mentioned it takes awhile and i personally have never been able to get it to report its progress back properly (although thats mainly due to not taking enough time to understand it properly).
The syntax is as follows - 

```
dd if=/dev/sda of=/dev/sdb
```

Where sda is replaced with the /dev/ filename of the disk your wanting to image from ("if" stands for in file i beleive) and sdb is replaced with the /dev/filename of the drive your imaging too ("of" meaning out file, again im assuming).

---

### Post by YesWeCan on 2011-02-02
I've used DD. Very simple, made a perfect clone. Allow an hour or more for it to complete. Boot a live CD and get the if and of drives the right way around or you'll erase your 60GB disk!:
dd if=/dev/sda of=/dev/sdb bs=64k conv=notrunc,noerror

Note that your 180GB disk will literally be a clone of your 60GB disk as far as the OS is concerned. That means it will have the same UUID and you must not have both disks connected at the same time when you boot or the OS will throw a fit. After you have booted off the 180GB drive you can use Gparted to extend the 60GB partition to the whole disk space.

Excellent guide to dd: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Antarctica32 on 2011-02-03
> **coffeecat said:**
> I presume you mean that you want to clone not just the files, but partitions, filesystems and the partition table.

I want it to be exactly like it is now. The 60GB is the only HDD on my computer that has stuff on it. All you guys told me about programs for cloning, can't I just drag and drop into the 180? then turn the 180 into a master?

---

### Post by Antarctica32 on 2011-02-03
The whole DD thing looks incredibly confusing. I think if I go down that road I will need a lot of help, because I never really use the command line.

---

### Post by coffeecat on 2011-02-03
> **Antarctica32 said:**
> All you guys told me about programs for cloning, can't I just drag and drop into the 180? then turn the 180 into a master?

No. It doesn't work that way. A drag and drop only copies files. For the copy to be exactly as the original, you need to do a low-level byte-by-byte copy, thus copying the partition table, the partition boundaries, the filesystems as well as what the filesystems contain. For that you need dd or clonezilla.

In point of fact, dd is not at all difficult. Use the live CD and make sure you get the if and of options the right way around - as someone has already pointed out.

---

### Post by ebasa on 2011-02-03
I would reccomend Remastersys
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Create a live cd of your system then boot from it and install to the new drive,

---

### Post by Antarctica32 on 2011-02-03
What exactly do you mean when you say "live CD"?

---

### Post by ebasa on 2011-02-03
It will clone your existing system and allow you to run it from a CD you can then just click on 'install' rather than 'try'. All your programs and data will be installed as is.
All the info is in the link I posted.

---

### Post by Antarctica32 on 2011-02-03
OH! I get it! you want me to boot from a live CD and copy the files from the 60 to the 180 while running off of a CD. Why do I have to do it using a live CD? I absolutely hate running off of CDs, I am all about speed. But whatever, I get that part of it so far. Please correct me if i'm wrong.

---

### Post by presence1960 on 2011-02-03
> **Antarctica32 said:**
> OH! I get it! you want me to boot from a live CD and copy the files from the 60 to the 180 while running off of a CD. Why do I have to do it using a live CD? I absolutely hate running off of CDs, I am all about speed. But whatever, I get that part of it so far. Please correct me if i'm wrong.

Forget "copy" of files if you want to clone a disk. Copying files will not produce a clone of a disk as coffeecat already told you.

Trying to be helpful is sometimes trying. I say this because you asked for help cloning a disk, however you keep finding objections to the viable options presented to you. Why bother asking?

---

### Post by nerdy_kid on 2011-02-03
use a livecd and gparted.

turn off your pc, plug in the hard drive you want to clone too (dont unplug your old one) pop an Ubuntu LiveCD in the drive and boot from it.  Once its up, open Gparted, select the disk that you are cloning from.  right click the partition you want to clone (it should be EXT4) and hit "copy".  Select the drive you want to clone to, right click an unallocated area and click "paste".  Expand the partition to fill most of the disk, but leave about 1GB for a swap partition.  Click Ok.  Once its done, in the main gparted window right click the 1GB unallocated space that you left for the swap and hit "create new partition".  Under "type" select linux-swap and hit ok.  Hit apply.  Now, close gparted and open a terminal.
type:
```

sudo fdisk -l

```
find the disk you are cloning to in the list, it should be /dev/sdb or something similar.
then do:
```

sudo grub-install DISK_PATH

```
replacing DISK_PATH with /dev/sdb or whatever for your disk.  Make sure the path is right, or you will wont be able to boot from the disk you are cloning too.  Now you should be good, shut the computer down, unplug both hard drives and plug the 180GB drive into the slot that your old drive was in.  You should be good to go...

---

### Post by C.S.Cameron on 2011-02-03
+1 for dd

```
sudo dd if=/dev/sda of=/dev/sdb
```

Do this in terminal while booted from the Live CD.
(Once dd is running it is slow, but no slower running from the Live CD)

Make sure sda is the disk you want to copy and sdb is the target.

Use gparted to expand the partition after, unless there is a Windows o/s involved.

---

### Post by ebasa on 2011-02-03
did you even bother to read the information on the link? Sorry no more from me.

---

### Post by Antarctica32 on 2011-02-03
Thank you so much. A walk through that strait forward is exactly what I need. My only questions are, how would I "expand the partition to fill most of the disk", if it filled 98% of the disk would I only be able to use 98% of the disk?. Also, would it matter that my new disk is a WD and my old is a Maxtor? Is there some kind of bios like thing in the HDD? I probably sound like a noob asking that.

---

### Post by Antarctica32 on 2011-02-03
Sorry, I did read it, it's just that I want to make sure I'm doing it all right. This sounds like something it sucks to mess up.

---

### Post by Antarctica32 on 2011-02-03
When I put in my CD, won't it just start the install? How do I keep it from doing this and just boot from it?

---

### Post by ebasa on 2011-02-03
It's beginning to sound as if you have never installed an OS before.

---

### Post by Antarctica32 on 2011-02-03
I have and just did again yesterday, I just have very little experience.

---

### Post by Antarctica32 on 2011-02-03
should I set my HDDs to slave, master w/ slave, or master single?

---

### Post by timsdeepsky on 2011-02-03
> should I set my HDDs to slave, master w/ slave, or master single? 
Are you using sata drives??..I am curious??

---

### Post by C.S.Cameron on 2011-02-03
> **Antarctica32 said:**
> When I put in my CD, won't it just start the install? How do I keep it from doing this and just boot from it?


Install is the second option, run Live is the first. you can't install by accident.

---

### Post by Antarctica32 on 2011-02-04
Thats strange, whenever I put a ubuntu 10.04 CD in a computer it just starts the install outomaticly. Whatever.

---

### Post by Antarctica32 on 2011-02-04
> **timsdeepsky said:**
> Are you using sata drives??..I am curious??

No, I am using Parallel ATAs.

---

### Post by nerdy_kid on 2011-02-04
when you put the cd in the drive and you see the purple screen with a keyboard at the bottom hit <shift> and it will give you the option to try out ubuntu and not install it.  About "expanding":  Gparted will give you a dialog that lets you drag a slider to set the partition size.  That is what I was talking about.  And yes, if the partition is set to fill 98% you will only be able to use 98% (a little less due to other factors).  But, you do need a swap partition, so you need to leave room for one.

---

### Post by Antarctica32 on 2011-02-04
Let's just say I set the partition to 60% for the sake of... well idk. But let's just say I do, after everything is copied will I be able to set it higher or lower. Would it be best to set it to something really low like 20% so that there is a lot of swap room, then set it to 99% after it's all done. There is hardly anything on my HD, only about 15GB. I realized that I would run out of room in about a year at this rate, so I set out on a quest to upgrade to a better drive. Thanks for all your help and patience, I think I get how to do it now. First I will test it out on one of my crappier machines.

---

### Post by nerdy_kid on 2011-02-04
> **Antarctica32 said:**
> Let's just say I set the partition to 60% for the sake of... well idk. But let's just say I do, after everything is copied will I be able to set it higher or lower. Would it be best to set it to something really low like 20% so that there is a lot of swap room, then set it to 99% after it's all done. There is hardly anything on my HD, only about 15GB. I realized that I would run out of room in about a year at this rate, so I set out on a quest to upgrade to a better drive. Thanks for all your help and patience, I think I get how to do it now. First I will test it out on one of my crappier machines.

cloning, if done correctly, does nothing to the original drive. you need to set the partition to fill all of the disk except for 1GB, which you will need for the swap partition I mentioned.  FYI:  a partition size does not equal the sum of the sizes of all your files/folders.  A partition includes free space.  I will try and make a full blown guide on this subject (cloning) cause it seems to be something that people always are asking.

---

### Post by Antarctica32 on 2011-02-05
OK well long story short it didn't work. On one of my less used machines I have an Maxtor 80GB HD, I plugged an 80GB identical same model number and everything in as well. I then took one of my 10.04 CDs put it in and ran off of it. Well at least tried to. The keyboard picture at the bottom popped up and I hit shift and it then went to this language selection screen. I hit enter on my language and then a second screen popped up. It gave me the option to run off of the CD, install Ubuntu, or like 3 other things. I hit run off of CD. It then went to the boot screen with the 5 little purple dots for about 1 minute until the dots stopped changing color, and it stayed like that for about 30 minutes until I gave up and pressed the restart button on my computer. I tried it all again with the same result, except for one thing: the little purple and white dots stopped at a different spot, with only one dot white as opposed to the first time when it stopped at only one dot purple. This must mean that it either got further or shorter into the booting process. 

I think what went wrong was possibly caused by:
having both HDs on the same ribbon 
having both hard drives set to master
only having 512MB of RAM
maybe the CD I used was bad (I have used the same CD before and even used it to install Lucid on this computer, but maybe the live CD thing doesn't work on it?) 

Can I just do the cloning while running off of the being cloned HD? Is there some kind of constantly being updated data on the HD, is that why I can't run off it while cloning? I was thinking about running off of a 3rd HD while I do the cloning, would this work? My dad who knows a lot about cloning windows HDs said that the problem could be caused by both the HDs trying to be masters. I find this hard to believe as the bios already recognized the CD player as the master. He also says that the whole process could go much faster if they are on different ribbons, but he doubts thats what is causing it.

---

### Post by timsdeepsky on 2011-02-05
Wow....
Seems like you could save yourself some self induced trouble in the long run....
What about this....
Save all the info you want from your old drive onto dvd(s)....
Put the drive you want into your tower....
Start from scratch....
Install Ubuntu....
Live life and prosper....
(i have a 1tb drive as my main,,,,and added a 1tb for a backup,,,,"pysdm" auto mounts my backup drive at every startup,,,,and "sbackup" copies my info from drive #1 to drive#2 every week....)
This could be an option for you to add more drive space in the future....
And effectively solve the partition size thing you have going....
Just let Ubuntu use the whole drive and make it's own swap space,,etc....
My apologies if this is no help....

---

### Post by ebasa on 2011-02-05
> **timsdeepsky said:**
> Wow....

My apologies if this is no help....

Some people just can't be helped, he was given several easy solutions yet can't seem to follow simple instructions.

---

### Post by presence1960 on 2011-02-05
Use clonezilla for pete's sake!!

---

### Post by nerdy_kid on 2011-02-05
guys, give him a break:
> **Antarctica32 said:**
> I just have very little experience.


Antarctica32,  you can not be running the system that is getting cloned.  Try unplugging one of the HDs and see if the livecd will boot.  If it does, make sure the two hard drives are configured correctly in BIOS.  Another perhaps easier solution for you would be to keep Ubuntu installed on your 60GB drive and move all your files/settings onto the new hard drive, allowing you to keep your current system and increase your disk space at the same time.  Ubuntu can be "split" across multiple drives, allowing you to have pieces of it installed on different devices.

---

### Post by Antarctica32 on 2011-02-06
That sounds interesting. Would it be possible to create a virtual drive in Ubuntu, I am sure you can do this on windows. I could then just put in my 180 as a slave and join it with my 60 and then have a virtual 240GB drive. I tried running off of the CD with only my master and it works. I also made sure the 180 was set to slave on both the jumper and in Bios. It still doesn't work. Now for some reason after it goes into the whole 5 purple dot booting screen, it goes to a black page with "AUTHENTICATION FAILURE" 11 times on it. I tried switching the drives places on the ribbon in case that helped and of course it didn't. I was kinda hoping I could use the 180Gb as my one and only drive in the end. I need as many drives as possible for my eagle project[http://ubuntuforums.org/showthread.php?t=1676724]("http://ubuntuforums.org/showthread.php?t=1676724")
and I could always use my old 60GB as a master for one of the computers.

---

### Post by johncc on 2011-02-06
> **Antarctica32 said:**
> ...I tried running off of the CD with only my master and it works. I also made sure the 180 was set to slave on both the jumper and in Bios. .... I was kinda hoping I could use the 180Gb as my one and only drive in the end.....

You are quite correct in the notion that the two drives need to be recognized by the bios properly, prior to attempting to clone or copy the drive.  When you have both drives connected, and you go into your bios screen (prior to booting), do you see both drives listed with the correct sizes?  If not, then even if the LiveCD boots you will not be able to do what you want to do.

Also (separate issue) If you are having trouble getting the LiveCD to boot/run, you may have to dig in and learn how to change the boot parameters like "nomodeset" and vga settings... I think this is often necessary on older hardware such as you may be using.

My 2c :)

Cheers,
John

---

### Post by Antarctica32 on 2011-02-06
Yes the drives are completely fine in Bios, they have the correct names, sizes, and boot priority. I looked into the whole "nomodeset" thing. It sounded like it could be my problem, so I booted again (with an 80GB HD that has Lucid on it, and an 80GB master with maverick- remember I am doing most of this experimenting on my Asus   
[http://ubuntuforums.org/showthread.php?t=1678413]("http://ubuntuforums.org/showthread.php?t=1678413")) this time with a 10.10 CD. I was going to change the bios to nomodeset when I realized I had not tried using a 10.10 CD yet on this machine. So I said you know what the heck, I have nuthin to loose and decided to try it first with just a Maverick CD and no nomodeset. It went right into the boot screen and stayed there for a while. I was 100% sure it was going to freeze up or go to some black screen. After a while it did just that, it went to a plane black screen with no text. I decided to give it a chance and waited another 10 minutes. I was so happy when the desktop actually came up! That's right about ware I am now, just wanted to post this before I attempt to do the cloning.

---

### Post by Antarctica32 on 2011-02-06
And of course it didn't work. I was working for a little bit (about 15 seconds) before I tried to open "disk utility" under System- Administration so I could see what the disk were called. The little pictures next to the name of the program didn't pop up- EX: only the words "disk Utility" came up, no little picture of a HD, this was the same for all applications. I clicked it anyway and nothing happened, even after 30 Minutes. I clicked it again after that and waited another 30 mins. Then something did happen, the panels on both top and bottom disappeared. I waited a little longer and eventually several error message boxes popped up saying how the applications "Gnome Panel" "Notification area" and others like that had expectingly quit. I became so angry I just pressed the restart button on my tower. Next I guess I will try messing with the nomodeset thing.

---

### Post by nerdy_kid on 2011-02-08
alight, well lets forget the cloning.  Make sure both drives are plugged in, and boot up Ubuntu.  
I am going to refer to the 60GB drive as A and the 120GB as B.  I am going to assume that drive B is formatted with ext4

Figure out what the device files for both drives are by running
```

sudo fdisk -l

```

Now open up drive B in a filebrowser, figure out where it is mounted by running this:

```

sudo mount

```

look for drive B's device file, and it will tell you where it is mounted.  Should be /media/something.

now run:
```

sudo cp -R -p /home PATHTODRIVE_B_MOUNTPOINT

```
that will take a long time, as it is copying all your files.  When it is done, run:


```

gksu /etc/fstab

```
add this to the end of the file:

```

DRIVE_B_DEVICE_FILE /home           ext4    defaults        0       2

```

save the file, and close the editor.

finally run:
```

sudo mv /home /home_old

```
and reboot.

You _should_ be all good, run 
```

mount | grep DRIVE_B_DEVICE_FILE

```
and if it returns something then you are all set.  If not, then you probably are freaking out cause either Ubuntu didnt start or all your settings are missing :D  but no fear, cause I can fix that if it happens...which it shouldn't.

---

