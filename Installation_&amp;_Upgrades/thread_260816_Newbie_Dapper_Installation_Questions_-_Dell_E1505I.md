---
title: "Newbie Dapper Installation Questions - Dell E1505/Inspiron"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by jdmturbomr2 on 2006-09-19
Hi guys,

I've really been wanting to install Ubuntu for awhile now but have always been scared off because I'm not the most computer savvy person and have little to no experience with Linux.  I recently obtained a position with a company that requires me to do some computer science work and I've been told I may have to do some stuff in Linux later on so after laboring over what distro to go with I decided on Ubuntu because of it's popularity and community.  I tried to do as much research as I could before posting a thread but I just want to be sure I'm understanding everything...

I've got 4 partitions on my laptop from the factory:
1 FAT 47MB partition - this is the MBR? w/ the Dell Recovery tool thing in place
1 FAT32 4.63GB partition - Dell Utilities, media direct stuff, etc.
1 80GB NTFS - Windows XP
1 26GB NTFS - supposed to be used with Norton Ghost for backup files but I was thinking I could put linux on this partition...

Now for the questions.  Do I need to do more custom partitioning before installing Dapper?  I would like to keep my current XP installation intact and dual boot because I have to do some work in XP still.  I've read a bunch of tutorials that talk about splitting up linux into a seperate partition for '/' and another for '/home' or something like that.  I would like to know the best way to partition from a functional/stability perspective but if there is a compromise of simplicity I might go with that option (e.g. I would like not to have to reformat the entire drive if possible).  Also people make another FAT32 partition for storage of media files to share between Linux and Windows.  If anyone is kind enough to shed some more light on this or point me to a tutorial that would be great!

Also one last thing--I've seen a lot of threads complaining about GRUB being installed in the MBR.  Do I need to be concerned with this?  I know I will lose functionality of the Dell Restore Utility (Ctrl+F11 at boot) but I have the Recovery CD so that's no big deal.  Is there a better place to install GRUB from a functional perspective than the MBR? 

Thanks, I promise I've been trying to read as much as I can in the last 2 weeks..but I'm so anxious to install Linux ASAP and I just wanted to be sure so please cut me some slack if they are overly asked.

---

### Post by zxee on 2006-09-19
There are many install guides (+partitioning info) here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Grub should "see" your xp install and allow for dual booting.
Aways backup your data-of course. Maybe you could shrink the 80Gb partition that xp is on? ubuntu would work fine in a 10GB partition-particularly since you're just experimenting, or go with a usb drive install if that interests/works for you.

---

### Post by jdmturbomr2 on 2006-09-19
thx for the reply.  yeah i've looked at those install guides but they don't really give to much in depth info.  Like is the best setup to just split off windows and linux completely (without a shared data partition)?  Also should I try to do some fancy linux partitioning (seperating '/' and '/home', or whatever nifty functional way there is to do it)?  And is installing GRUB to the MBR the best option for me?

---

### Post by sleeperknight on 2006-09-19
heres a video guide might help 
[http://video.google.com/videoplay?docid=-6104490811311898236&q=dual+boot&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=dual+boot&hl=en)

---

### Post by fokuslee on 2006-09-19
im pretty new myself but i been running dual boot xp ubuntu just fine. i used 9 gig for / and 1 gig for swap and it worked fine 
im told 512mb of swap is enuogh thou
/home is just the home directory for diff users.  U save the stuff u been working on there, so i can see why someone would want to keep it on a seperate partition.
Then again if you install ext2ifs  (and yes it works with ext3) 
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to windows you can read/write to your linux partiton from windows environment. so you can always grab ANYthing from your linux folders. 
and here are some links that helped me a whole bunch when i started 
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[https://wiki.ubuntu.com/Tseliot](https://wiki.ubuntu.com/Tseliot)
and when u still have questions use irc forum etc there are alot of good pplz out there 
oh run the live cd and test it out first see if you like it 
good luck

---

### Post by confused57 on 2006-09-19
Excellent website, even though it's titled "Illustrated dual boot site", there's a wealth of information:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Another great website explaining most of the tasks you would need to know in Linux:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

I recommend you read over these sites, try out the Desktop Live CD for awhile to familiarize yourself with how Ubuntu works...the installed version will be basically the same as what you experience with the live cd.  Search and read thru the forums, google, etc.

It's my understanding that the mbr is on the first 512 kb of the hard drive, not actually on the first partition.
You can only have 4 primary partitions on a hard drive, Windows must be installed on a primary partition; but Linux can be installed on logical partitions...an extended partition(which is a primary partition) would need to be created and you can have as many logical partitions within the extended partition as you need or want.
I don't know anything about a Norton Ghost partition, but that may be the partition candidate for eliminating, and creating an extended partition in it's place...may want to wait on someone else to confirm this.
Keep asking questions, there's "beaucoups" of knowledgable people here in the forum who can help...once you think you have a "game plan", post before you actually go about implementing it.

---

### Post by alemora on 2006-09-23
I just installed Ubuntu on my Inspiron 6400 which is the same as the E1505 2 days ago

Here is what i did:

-Run the installation from the Ubuntu 6.06
When i got into the partition prompt:
-Did not resize nor modify the partitios for dell utilities or dell restore.
-Resize the partition for windows
-Create an extended partition with 3 logical partitions
1 GB for swat
9 GB for linux 
10 GB fat32 partition for sharing files between linux and windows (haven´t tested yet but i think it should work just fine)

-Load the Grub following the installation utility...

Almost Everything worked just fine: bluetooth, wifi, speakers, volume controls (the play/pause, ff, back, and stop didn´t).  

I still have to configure the screen to the 1600 x 1050 resolution ( i think i need to download de 915 resolution drivers for that).... 

The double boot from Grub worked great!!!!!! 

HOWEVER there is one thing i havent been able to configure properly: the media direct button, when i press it the computer gets into Grub and makes me start either windows or ubuntu... I haven´t found any "easy" solution that does not requires a Dell CD. My recommendation (from what i have read, i am no linux expert) is: try to set GRUB up on another partition not on the MBR or make a boot disc to use when u want to load Linux. 

Have somebody managed to work out the direct media button after settin up grub? Any help is welcome....

Good Luck with your installation

PURA VIDA

---

