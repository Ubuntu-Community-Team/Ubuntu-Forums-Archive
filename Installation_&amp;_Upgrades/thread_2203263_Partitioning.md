---
title: "Partitioning"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by Randy_Long on 2014-02-02
Hi all.
I'm starting to get into linux and have decide to try and prolong my dell laptop that I got 5 years ago. I currently have XP on it, and I'd like to partiotion the drive, (I have about 100gb of install hard drive space left.). I don't want to reformat, cuz I got a lot of work/research files on it. So, any tips/tricks to help out a noob would be very helpful.

I just dowlloaded the 12.x ubuntu iso and burned the iso to a disk. So, I'm still wondering what strategy/game plan to go with from here. 

Thanks a lot again and love learining new stuff.

---

### Post by Bashing-om on 2014-02-02
Randy_Long; Hi ! Welcome to the forum.

To assist you in utilizing that  " 100gb of install hard drive space left" for ubuntu, we need to look at what ubuntu sees.

Boot the liveDVD to the desk top, dash (top icon) -> search box -> enter the term GParted -> click on the resulting icon to activate Gparted. GParted is ubuntu's partition editor. At this stage look, but do not touch (apply). It would be helpful if you provide a screenshot of GParted.
For your info and acclimatization :
sda = Serial Device 1 - the 1st hard drive the system recognizes;
sda1 is 1st hard drive, 1st partition on the hard drive
sd5 is 1st hard drive, 5th partition
sdb is 2nd hard drive
sdc is 3rd hard drive
sdc3 is the 3rd hard drive, 3rd partition.

Then we also want to see what other attribute the hard disk has:
Activate a terminal (key combo ctl+alt+t) and post the outputs -between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

If it turns out that the 100 gigs space is "unallocated" we can advise on how to install ubuntu there.
Else: with the info provided by the above, we can explore other options.

[INDENT][INDENT]welcome to our world of
[INDENT][INDENT][INDENT]open source
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Randy_Long on 2014-02-02
Bashing-om,

Thx for the reply.

uh...well i just found out the iso file won't fit on a cd. ugh...I need to make a trip to target on super bowl sunday. at least it'll be dead quiet there.

Are you a Razor Back?

Thx and I'll be quick about it. I could have sworn I had some blank DVD's in this house...

---

### Post by Bashing-om on 2014-02-02
Randy_Long; Hey,

I expect I will be around still, or others !

When you are ready to proceed.

One can also install from USB .. got a thumb drive around ?

[INDENT][INDENT]many roads lead to
[INDENT][INDENT][INDENT]one end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Randy_Long on 2014-02-02
So, where do I use the command line?
[ATTACH=CONFIG]250036[/ATTACH]

A little nervous here...

---

### Post by cfmackey on 2014-02-02
That's Wubi, the windows installer. Don't do anything there, as that will install Ubuntu. We're not ready for that yet.

You're going to want to restart your machine with the disk in the drive. This will (after a little time) boot you into a live version of Ubuntu. From there you can assess the situation with your partitioning.

At least I think that's what Bashing-om wanted you to do.

---

### Post by Bashing-om on 2014-02-02
Randy_Long;

That screen shot you are already in the installer.
(did you choose "something else" at the initial screen ?)
Thanks @ cfmackey. never have seen a wubi install screen !

Try this to get to a terminal:
Reboot, and as soon as the bios screen clears, depress and hold the left shift key -> language screen, escape key to accept
the default -> boot options screen -> choose "try ubuntu" -> long load time -> desk top;
key combo ctl_alt+t yields a terminal.

We will get you through this, hang in there !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-02
Randy_Long; Hey !
Here is a thought:
Download the ubuntu .iso file ( ya might find that you like Lubuntu better);
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Check the integrity of the .iso ;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso to disk as an image !
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Now as far as I know 12.04.3 WILL fit on a CD ( I burned 12.04.1 to CD ).

Boot the liveCD -> as above to the boot options menu:
choose "check disk for defects".

Now you have an liveCD ! We can not only use it to install ubuntu, but, also check out things on the hard drive from this medium.


[INDENT][INDENT]we can do this !
[/INDENT][/INDENT]

---

### Post by Randy_Long on 2014-02-02
oh...I didn't click the left-shift button after the bios. i'll give it a go...

---

### Post by Bashing-om on 2014-02-02
Randy_Long; Hey,

OK, Waiting to see how it is going.

How else at this time I can assist.

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by mastablasta on 2014-02-03
> **Randy_Long said:**
> oh...I didn't click the left-shift button after the bios. i'll give it a go...


you need to boot from the media. if it's CD it has to be set as first boot device in bios. newer BISO have a boot menu where you can select to boot from device specified in that boot menu. how to access bios depends on version of BIOS on motherboard. in my case one motherboard wannts me to hold F2 on boot, other one esc, third computer needs F12 pressed on boot and 4th needs Del button to be pressed to enter BIOS or boot menu.

---

### Post by Topsiho on 2014-02-03
Randy_Long wrote:  "I don't want to reformat, cuz I got a lot of work/research files on it."
Even if you don't (plan to) reformat, please backup these data before you do anything else, preferably on an external disk.
Research and work  files I would back up, and keep in a place in an other building than that where my computer sits.
Possibly even in the cloud, if that is not a problem.

That is what you always should do, especially when making changes like this to your computer.

Topsiho

---

### Post by Randy_Long on 2014-02-04
Hey guys. I got to boot from the dvd. I'm attaching a pic of the  GPARTED, screen shot. I'm not really sure how much unallocated space I  need, but I suspect 7.73megs is a little short. Any Ideas on how to  proceed? I'm really wanting to do the install, but I got to keep my patience...[IMG]http://imageshack.com/a/img713/6785/xc7p.png[/IMG]Tthx again for all the help.

---

### Post by mastablasta on 2014-02-04
as mentioned even if you do everything right things can still go worng when moving partitions. goes for windows as well. so backup! backup! backup!

now that we backed it all up...

so we must not touch sda1, sda3 (what is there?) and sda4 will also be offlimits.

what you need to do is defragment the system drive (c:\) in windows 2 times. then use windows disk manager to shrink it a bit more. just move the slider to the left as i remember. this should create more unallocated space (in the window it is shown as unformated but i am not sure as it's been a while since i've done this). create about 20 GB of this unformated disk space (this will be enough for OS and some programes, you can create more if you want to - if you have 100 GB free then you can create about 70-80 GB, leave some space on xp). while in windows disk manager note the number of prmary partitions. there should be only 3 of them. post back when you are done. 

or continue with install - boot and then choose to install to largest empty disk space. the rest will be handled for you by installer. again if you don't get this handy option post back and we will guide you through manual setup.

edit: to do backup to external hard drive i recomend redo backup. same as with ubuntu install image you create boot CD/USB from image, boot from it and then it's really simple to use it to create compressed bit-by-bit image of you disk on external drive.

---

### Post by Topsiho on 2014-02-04
Things are more complicated than first meets the eye, and I admit I can't advise here.

Studying the GParted screen I see that there are 4 primary partitions (one of which is used as an extended partition):

sda1, file system fat16
sda2, filesystem ntfs
sda4, filesystem fat32
and
sda3, used as an extended partition, used to contain the other partitions
The partition contained in sda3 is the secondary partition sda5.

We can't have more than 4 primary partitions, of which only 1 can be an extended partition, and any extra partition should be contained in this extended partition.
So as far as I can see we'll have to sacrifice sda4 and sda5, and create one big unallocated space using all space after sda2.

But that means sacrificing DELLRESTORE and MEDIADIRECT, the consequences of which I don't know.

My two cents, hope that someone can help here.

Topsiho

---

### Post by westie457 on 2014-02-04
Make a plan of action about this.

Some more advice.
The biggest stumbling block on resizing the C:\ drive of Windows is usually the 'hiberfil.sys' file. this file is always near the end of the drive and is unmovable if hibernation is turned on. This link shows how to check and turn it off. [http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/](http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/)
With hibernation turned off, defrag the drive again and shrink it again, as much as possible. Reboot to Windows to make sure everything is okay there.

Reboot to the Live Ubuntu desktop, open Gparted select SDA3 > right-click select resize. Drag the left-side end all the way to the left as far as it will go. Click on Okay, click on Apply (the green tick at the top) and again on Okay in the warning window.
Now in this free space select new, format this to NTFS. for now use the whole space, follow the previous instructions .
Close Gparted.
The next part can be done in either OS. Simply 'Cut and Paste' your files from Windows to the newly created partition. This frees more space in the C:\ drive.

If you have more files than will fit into the new partition reboot into Windows and repeat the process of shrinking Windows.
If you have to re-shrink Windows the procedure in Ubuntu will be slightly different. In Gparted this time instead of creating a new partition you will need to resize SDA3 again and resize the partition you have just filled up.
You will have to do this as many times as necessary to get the C:\ drive down to about 50 GB (this should leave enough working space depending on what you have installed.

**Never rush at partitioning work**, it can be very easy to make a mistake.

When you have done the above come back here for advice on the next steps.

---

### Post by mastablasta on 2014-02-04
> **Topsiho said:**
> Things are more complicated than first meets the eye, and I admit I can't advise here.

Studying the GParted screen I see that there are 4 primary partitions (one of which is used as an extended partition):




ah so one primary partition is hiding. naughty, naughty!

here is a simple solution - you windows system partition C:\ (sda2 in linux) is primary. make it extended. you can do that since you have separate boot partition. how to do it - there is a simple free windows tool called Mini Tool Partition Wizard home edition: [http://download.cnet.com/MiniTool-Partition-Wizard-Home-Edition/3000-2094_4-10962200.html](http://download.cnet.com/MiniTool-Partition-Wizard-Home-Edition/3000-2094_4-10962200.html)

in one of the menues you can change the primary system partition into extended and then continue as i explained in previous post. make sure you backup data first!

grub boot loader goes to sda1 during install anyway.

i did it like this and in my case restore and tools partition continue to work (but i have an HP laptop and partitions are a bit differently set, but still 4 primary). no data was lost during procedure nad no partitions were deleted (only new ones were created). as it should be, but we make backups just in case it doesn't.

---

### Post by Randy_Long on 2014-02-04
dood, this is getting complicated. I need to write this stuff down.

---

### Post by mastablasta on 2014-02-05
it is because they filled your laptop (for no good reason) with 4 primary parittions. it seems they too ran out of primary and resorted to secondary (extended) in one case.

here is the procedure in short:
1. backup any data
2. use mini tool partition wizzard to change windows/system/c: partition into extended (secondary) parittion
3. defragment C:\ "drive" using windows defragmentation tool (may take a while to be completed)
4. defragment it again (it will do it a lot faster)
5. open windows partitioning tool and resize C partition. make it smaller for about 50-70 GB (minimium is about 10GB, for peopprly trying out the Ubutnu OS 20-25GB is good). leave the space unformatted.
6. during install you should now get the option to install to largest empty disk space. use it. if you do not get this option post back and we will guide you how to set up partitions manually.

when installer asks where to put grub you put it to main disk. GRUB is a tiny program (bootloader). this starts after BIOS loads and before any OS boots. windows has it's own boot loader that can only handle windows. grub can handle a lot more different operating systems.

---

### Post by Topsiho on 2014-02-05
Isn't it far easier and ==>[COLOR="#000000"] [COLOR="#000000"][COLOR="#FF0000"]less risky[/COLOR][/COLOR][/COLOR] <== to add a second drive to your computer?
That way you can put Linux without much ado onto that second drive.

Drives are not expensive these days (in my country, anyway). Thing to remember is that there are IDE drives and Sata drives.
For experimenting with Linux a small drive (say 20 GB) is quite enough.

Use 5 to 10 GB for /, twice your Ram for swap and the rest for /home.

Maybe you, or someone you know, may have an odd drive lying somewhere, or sitting in a computer that is not used anymore.

Topsiho

---

### Post by oldfred on 2014-02-05
Since you already have the extended partition it should not be quite so complicated.
And not sure if XP has internal partition tools like Vista/7 does. I would shrink XP with gparted. But immediately reboot Windows as it has to run chkdsk and make repairs for its new size.

Then back in gparted, move extended partition left to include all the unallocated before the extended and in effect make all the unallocated inside the extended partition. Not other partition should need to be changed. 
With all the unallocated inside the extended you can make as many partitions as you like.
If continuing to dual boot I might also make a shared NTFS data partition, / (root) of about 20GB, swap of 2GB and the rest for /home. Or just / (root)  and swap for entire space. Not critical either way.

If you create partitions in advance you still have to use Something Else to format partitions and tell installer (change) which is / and swap (and /home if desired). Or you can create (+) partitions as part of install.

---

### Post by Randy_Long on 2014-02-05
ok guys I really appreciate the advice and help. I do have a pre-calc exam tonight (that's why I haven't been so diligent about getting back to you). I'll write down all these notes and back up the 180gigs of HD space on my laptop ( which I think will take a while). I'm really excited about this stuff!

---

### Post by Randy_Long on 2014-02-06
ok guys. A couple of things. Can I combine SDA3, 4, 5 as well as all three of the unallocated partitions? Mediadirect is junk adware, and DellRestore is probably the backup XP disc, I think. That's about 16 gigs of space. The C: drive that has 220gigs has all my papers/pictures/research/ etc. Can I upload these to google drive? I'm a little uneasy about that, but I don't want to get another 500 gig hd. Or should I?

Thanks fo rthe help.

---

### Post by Randy_Long on 2014-02-07
> **westie457 said:**
> Make a plan of action about this.


Reboot to the Live Ubuntu desktop, open Gparted select SDA3 > right-click select resize. Drag the left-side end all the way to the left as far as it will go. Click on Okay, click on Apply (the green tick at the top) and again on Okay in the warning window.
Now in this free space select new, format this to NTFS. for now use the whole space, follow the previous instructions .
Close Gparted.
The next part can be done in either OS. Simply 'Cut and Paste' your files from Windows to the newly created partition. This frees more space in the C:\ drive.

If you have more files than will fit into the new partition reboot into Windows and repeat the process of shrinking Windows.
If you have to re-shrink Windows the procedure in Ubuntu will be slightly different. In Gparted this time instead of creating a new partition you will need to resize SDA3 again and resize the partition you have just filled up.
You will have to do this as many times as necessary to get the C:\ drive down to about 50 GB (this should leave enough working space depending on what you have installed.

**Never rush at partitioning work**, it can be very easy to make a mistake.

When you have done the above come back here for advice on the next steps.

westie, will the sda3 partition be the ubuntu drive? I'm afraid I have about 150gigs worth of files and it won't be able to fit in the newly created sda3 partition.

i'll be getting my external HD tomorrow and backing up all my files. whoa! I just saw 1TB hard drives on best buy for $79US! 
thx for all the help,

---

### Post by mastablasta on 2014-02-07
> **Randy_Long said:**
> ok guys. A couple of things. Can I combine SDA3, 4, 5 as well as all three of the unallocated partitions? Mediadirect is junk adware, and DellRestore is probably the backup XP disc, I think. That's about 16 gigs of space. The C: drive that has 220gigs has all my papers/pictures/research/ etc. Can I upload these to google drive? I'm a little uneasy about that, but I don't want to get another 500 gig hd. Or should I?

Thanks fo rthe help.


restore is a restore partition. you can also back that one up and then remove the whole sda3this will create unnalocated space in that area where again you should be able to install Ubuntu.

google drive doesn't give you so much space for free. however if papers and research are not taking so much then sure you can back them up there. if you can, create the windows disc/DVD from recovery partition as well.

again you shouldn't loose any data if you follow procedure. the backup is just in case something goes wrong (which it can and when it does it's bad since you "mess" with disk partitions).

---

### Post by Randy_Long on 2014-02-07
mastablasta,
I'm not sure I understand the process we're doing. Do I WANT TO GET RID OF sda3? I thought SDA1, 2, 4 were off limits? So, If I get rid of sda3, where would I install Ubuntu? I have about 70gigs of HD space left on my HD. Honestly, I'm getting confused here.

---

### Post by Randy_Long on 2014-02-07
ok. this is what I have so far. 
Partitioning the XP box for Ubuntu Linux.
1. BACKUP YOUR DATA/FILES
2. Turn off the dreaded hiberfil.file.
3. SDA1, 2, 4 are not to be touched.
4. Defrag the C: drive 2X, then shrink C: drive a little bit more.
5. Resize sda3. Make it as big as you think is necessary = 50gigs.
6. Install Ubuntu on sda3????

please advise...

---

### Post by mastablasta on 2014-02-07
> **Randy_Long said:**
> mastablasta,
I'm not sure I understand the process we're doing. Do I WANT TO GET RID OF sda3? I thought SDA1, 2, 4 were off limits? So, If I get rid of sda3, where would I install Ubuntu? I have about 70gigs of HD space left on my HD. Honestly, I'm getting confused here.

well you asked if you could join them. this might not be possible. though i read here mini partition tooll can do that: [http://www.partitionwizard.com/mergepartitions/merge-ntfs-partitions.html](http://www.partitionwizard.com/mergepartitions/merge-ntfs-partitions.html)
i know it used to work with FAT32 partitions but there were some specifics there.perhaps it works with NTFS better.  never attempted it. you should still have backup if you do.

 but you could back them up and remove them. you said one is junk and the other one is xp restore. if you have other restore media then this one can actually really be removed. i created restore media as suggested by manufacturer. however i still kept the partition as it will be easier to restore from it should i need to do it. as i would just select restore from BIOS boot menu. i also kept my tools partition as it had some good tools (they weren't junkware).

> **Randy_Long said:**
> ok. this is what I have so far. 
Partitioning the XP box for Ubuntu Linux.
1. BACKUP YOUR DATA/FILES
2. Turn off the dreaded hiberfil.file.
3. SDA1, 2, 4 are not to be touched.
4. Defrag the C: drive 2X, then shrink C: drive a little bit more.
5. Resize sda3. Make it as big as you think is necessary = 50gigs.
6. Install Ubuntu on sda3????

please advise...

you forgot you need to change C: drive into seocndary/extended partition if you keep sda3, sda4, sda5.
but yes this is the procedure if you do not want to delete any partitions.

---

### Post by oldfred on 2014-02-07
sda3 is the extended partition which counts as one primary, but is really just a container for logical partition. Nothing is installed in just sda3, but you create logical partitions sda5 and up in the extended partition. In an extended partition you can have as many logical partitions as you want. So / (root) and swap both are logical. And optional partitions like another NTFS data partition and /home can also be logical partitions. All as logical in the one extended sda3.

Windows c: drive cannot be  a logical partition. Windows has to boot from a primary partition. Only second installs of Windows can be in logical partitions, but even then all Windows boot files are in first primary Windows install.

---

