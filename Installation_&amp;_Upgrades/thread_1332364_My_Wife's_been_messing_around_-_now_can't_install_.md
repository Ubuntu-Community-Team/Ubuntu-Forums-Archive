---
title: "My Wife's been messing around - now can't install Ubuntu-Help"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by maddad on 2009-11-20
I have been away working away from home, and on my return ive found that my wife has been playing around with my PC, its an ACER E500 , when I left home was running Windows XP Media edition , well it seems for some reason my wife had some trouble with Windows XP and ended up with the Blue screen of Death, I have tried re installing Windows OS  again using the ACER rescue set of CD's that came with the machine, the CD's load ok and install the OS, but on its next boot up , all I now get is this message
  
  **GRUB Loading Stage1 .5.0 - ERROR 17**
  
  
  So as ive been wanting to try Ubuntu , I downloaded on a friends computer the Ubuntu CD image and burnt it to a CD
  then I booted up the PC and started to installed Ubuntu , about Two minuets into the install I had this message ,,,,
  
  **[ 2.00003] Kernal Panic -not Syncing:VFS:Unable to mount root fs on unknown-block (8,1 )**
  
  so now I have a PC that won't for some reason not install Ubuntu , as we live in a remote area taking the PC in for repairs is a problem, can any one here please help me to install Ubuntu on my PC , any advice or comments are most welcome :frown:
   
   
   Thanks William

---

### Post by gradinaruvasile on 2009-11-20
Error codes from the GRUB site:

"17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

Download a live-cd image, boot from it ("Try Ubuntu without installing")
then click applications-accessories-terminal

type in the terminal:

sudo su -

then

fdisk -l

post the output.

---

### Post by maddad on 2009-11-20
> **gradinaruvasile said:**
> Error codes from the GRUB site:

"17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

Download a live-cd image, boot from it ("Try Ubuntu without installing")
then click applications-accessories-terminal

type in the terminal:

sudo su -

then

fdisk -l

post the output.


Thanks for the quick reply 

Ive booted from the Live CD , and clicked ...  Try Ubuntu without installing


this is a shot of what I get, it just stays on this and does not move ..?

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06628.jpg[/IMG]


I'm not too sure what to do next ..

Thanks

---

### Post by gradinaruvasile on 2009-11-20
Thats not good. Remove the HDD (unplug its power cable) to see if it starts that way.
Also, what version of Ubuntu are you booting?

---

### Post by darkod on 2009-11-20
And one more hint. Once you start dual booting forget about restore cd/dvd or restore partitions. In most cases unfortunately, it not only brings windows back but it creates the SAME disk layout on the hdd like it came from the factory/dealer.
I really feel sorry for all those customers getting only restore dvd or partition when they are in fact in titled to a windows operating system cd/dvd, and mocrosoft has acknowledged that. I even heard that people are requesting windows media from the dealers and they have to send it.
I can't be 100% sure but I bet the restore messed up ubuntu completely.
Have no clue why the LiveCD option wouldn't work though.

---

### Post by gradinaruvasile on 2009-11-20
If it still doesnt work, you should try the memtest option and let it do 1 full pass (about 10-20 minutes).

---

### Post by raymondh on 2009-11-20
William,

A little more history needed (for me at least).

Originally, did you have Ubuntu or any linux installed (either thru wubi or in its' own partition).?  

I ask because that error 17 message is a GRUB/linux error message which to me means that someone installed GRUB as the bootloader.  I also ask because when you re-installed thru the acer recovery system, it would have re-written the image but not necessarily the bootloader (my acer d250 did this).  If that were the case, a re-install of GRUB would have to be done.

Do you have the XP install disc?

---

### Post by maddad on 2009-11-20
Well I removed the HDD power , and tried again ( Try Ubuntu without installing ) 
and this time it did load ok,  so does this mean there may be some thing wrong with the HDD, 
fingers crossed I can fix it :frown:

---

### Post by darkod on 2009-11-20
I would first try:
sudo fdisk -l (small L)

to see if you have ubuntu partitions left at all after the restore. Just copy the result here if you don't understand it.

I guess that's one way to stop people using both windows and linux, the restore process which brings the computer to factory defaults. When restoring your windows you are destroying your linux. :)

---

### Post by maddad on 2009-11-20
> **raymondhenson said:**
> William,

A little more history needed (for me at least).

Originally, did you have Ubuntu or any linux installed (either thru wubi or in its' own partition).?  

I ask because that error 17 message is a GRUB/linux error message which to me means that someone installed GRUB as the bootloader.  I also ask because when you re-installed thru the acer recovery system, it would have re-written the image but not necessarily the bootloader (my acer d250 did this).  If that were the case, a re-install of GRUB would have to be done.

Do you have the XP install disc?

Hi, the ACER E500 just had Windows XP Media Edition installed on it , nothing else , **''BUT'' **
ive just questioned the wife again ( who  said before that there was a Blue screen and it would not go away, ) and now she is saying that her friend came around to install Windows 7 as a surprise for me. ( some surprise ) , so it now looks that her friend has messed up my PC. I only have a set of 5 ACER recovery CD's , and not a XP install disk .


Thanks

---

### Post by gradinaruvasile on 2009-11-20
> **maddad said:**
> Well I removed the HDD power , and tried again ( Try Ubuntu without installing ) 
and this time it did load ok,  so does this mean there may be some thing wrong with the HDD, 
fingers crossed I can fix it :frown:

Ok, next question is what version of ubuntu live cd u have? If u have 9.10 (latest), try the previous one (9.04). 

Also, i dont really know what Windows 7 has to do with GRUB... Did that error appear after the installing? Cause the installer installs GRUB at the end of the process AFAIK. If it was before the installing, someone surely installed something linux based...

---

### Post by darkod on 2009-11-20
Read post #9 please. We need at least fdisk -l to see what partitions you have now after unsuccessful win7 install and winxp restore.

Boot with Ubuntu CD, select option Try Ubuntu, go to terminal (Applications -> Accessories -> Terminal) and execute that command. Post results and that will give more info.

Like this we're guessing blind. :)

---

### Post by gradinaruvasile on 2009-11-20
Well look at the picture OP posted... That appears if he tries to boot with the HDD connected. So this version of Ubuntu (whatever he has) locks up for some reason that now seems to be the HDD probably read/filesystem/kernel error of some sort.

---

### Post by raymondh on 2009-11-20
As darkod says, let's see what your HD contains.

liveCD > live session > applications > accessories > terminal.  Type and copy/paste back results of

```
sudo fdisk -l
```

small L.

Also, reminds us again the end-goal.  Get XP running as well as Ubuntu? Or just sole-boot either XP or Ubuntu?  What version Ubuntu will you install because the bootloader in 9.10 is different from 9.04 (I,personally, am more comfortable with 9.04 which I installed in the D250 and later on did a network upgrade to 9.10)?

Regards,

---

### Post by Onesimus on 2009-11-20
Might it be a problem with the Ubuntu Installation CD ? 

If the CD was not written at a slow speed (e.g. 4x), then it could be that there are errors on the CD rather than the computer.

In trying to solve the problem, it might be wise to start with the easiest things first.

From memory, the Ubuntu 9.10 installation CD comes with a method to check the CD for errors.  I suggest trying this.

---

### Post by raymondh on 2009-11-20
> **gradinaruvasile said:**
> Well look at the picture OP posted... That appears if he tries to boot with the HDD connected. So this version of Ubuntu (whatever he has) locks up for some reason that now seems to be the HDD probably read/filesystem/kernel error of some sort.

Very true and likely.

I just have a nagging hunch on the win 7 (installed by friend) and the linux/GRUB error message .... as well as knowing that the stock acer comes with 2 primary partitions (recovery and C) and the latest image re-install ...... hence my request for a fisk -l :)

Regards,

---

### Post by maddad on 2009-11-20
> **darkod said:**
> Read post #9 please. We need at least fdisk -l to see what partitions you have now after unsuccessful win7 install and winxp restore.

Boot with Ubuntu CD, select option Try Ubuntu, go to terminal (Applications -> Accessories -> Terminal) and execute that command. Post results and that will give more info.

Like this we're guessing blind. :)


Hi just tried the Terminal and this is what I get ..

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06632.jpg[/IMG]

and nothing happens, I am using Version 9.10 

Thanks guy's for the help - its appreciated

---

### Post by maddad on 2009-11-20
> **Onesimus said:**
> Might it be a problem with the Ubuntu Installation CD ? 

If the CD was not written at a slow speed (e.g. 4x), then it could be that there are errors on the CD rather than the computer.

In trying to solve the problem, it might be wise to start with the easiest things first.

From memory, the Ubuntu 9.10 installation CD comes with a method to check the CD for errors.  I suggest trying this.


Hi, the CD was burnt at the slowest speed ( x8 ) and it verified burnt ok , but ive not as yet used the check for errors option 


Thanks

---

### Post by gradinaruvasile on 2009-11-20
Ummm... did you reconnect the HDD and restarted the computer?
Also, if yes, you should check the BIOS if it sees the HDD...

---

### Post by maddad on 2009-11-20
Ummm... did you reconnect the HDD and restarted the computer?
Also, if yes, you should check the BIOS if it sees the HDD...

------------------------------------------------------------------------

Ive still got the Ubuntu running from the CD, when I first tried the ACER recovery CD's 
I made the optical drive the first boot priority , and the 5 CD's all loaded ok, and the PC re booted , only to come up with the GRUB 17 Error , should I re connect the HDD and try Ubuntu again ?

I am not too sure how to check the BIOS to see if it sees the HDD?

Thanks

---

### Post by gradinaruvasile on 2009-11-20
U should reconnect the HDD. The fdisk -l command lists your HDDs partitions. So first you have the HDD connected. Also, i would say to download an older Ubuntu version (9.04 or even 8.04) if this one throws the same errors. 
And first check the CD integrity on reboot.

Edit:
If windows 7 was installed over your XP installation i dont know what remained of your original windows...

---

### Post by darkod on 2009-11-20
Yes, definitely plugg the hdd in, if it's not. Sorry for before, I misunderstood. I thought the lock up happened only once and now he is able to boot the live CD with the hdd plugged in.

Everything should be plugged in as usual, and try to do the same procedure again.

---

### Post by cgb on 2009-11-20
If you are still unable to boot the live CD with the hard drive reconnected I would possibly, if possible, try connecting the HD to another computer as slave and formating the drive.  Then once formated try again in this computer.  Either that or buy a new drive since it is quite possible the drive is going bad.

---

### Post by maddad on 2009-11-20
Well  I switched off the PC , re connected the HDD,  and re booted from the CD, and this time when I put in the Terminal ...  sudo fdisk -l

this is what I get ....

 [IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06636.jpg[/IMG]


I don't understand why its this time run ok with the HDD connected and every time in the past when the HDD was connected it would not run? 

does the shot tell any thing Good ?


Thanks

---

### Post by darkod on 2009-11-20
As I thought. No Ubuntu partition. You can clearly see you only have type linux swap, and no "linux". Probably your recovery cds took care of Ubuntu. :)

Just to clarify, at boot do you get the grub menu or it's just starting XP like you never had ubuntu? The restore should have made it XP to start right away, that's confusing me.

---

### Post by gradinaruvasile on 2009-11-20
Well somethings not right... where is sda3 and 4? (just a rhetorical question)...

Maybe someone with higher knowledge can answer to this. I encountered only once this thing (not even me, the guy next to me in the office, he is a linux admin btw) and i couldnt even understand fully what he did, but it was something along the lines of redefining the missing partition (he had 1) by recreating the node (or whatever it is called). But thats out of my league...

---

### Post by maddad on 2009-11-20
> **darkod said:**
> As I thought. No Ubuntu partition. You can clearly see you only have type linux swap, and no "linux". Probably your recovery cds took care of Ubuntu. :)

Just to clarify, at boot do you get the grub menu or it's just starting XP like you never had ubuntu? The restore should have made it XP to start right away, that's confusing me.


The last time I used the ACER recovery CD's they took me straight to the part where it says that the recovery CD's have installed Ok, and now I have to re boot to fully start Windows XP, 
after the re boot its then I get the GRUB Error 17 , nothing about Ubuntu any where . Should I now try the ACER rescue CD's again, just to see what happens ..?


Thanks

---

### Post by darkod on 2009-11-20
#3 and #4 are "skipped" because /dev/sda2 is Extended, which means /dev/sda5 is logical created inside extended partition. Because the maximum of primary partitions is 4 the numbering of logical ones is starting from 5 onwards.
That is perfectly normal. But what's not normal is that he doesn't have ubuntu partition at all, just swap.
And by the size of /dev/sda1 it's clear that it takes the whole HDD less 6GB. Just what I would expect from recovery discs. They take the whole drive for themself creating the factory default layout.
Never use the recovery discs again. Try to get hold of Win XP disc. Plus it's creating the partition as FAT32 and NTFS is better.

---

### Post by maddad on 2009-11-20
> **darkod said:**
> #3 and #4 are "skipped" because /dev/sda2 is Extended, which means /dev/sda5 is logical created inside extended partition. Because the maximum of primary partitions is 4 the numbering of logical ones is starting from 5 onwards.
That is perfectly normal. But what's not normal is that he doesn't have ubuntu partition at all, just swap.
And by the size of /dev/sda1 it's clear that it takes the whole HDD less 6GB. Just what I would expect from recovery discs. They take the whole drive for themself creating the factory default layout.
Never use the recovery discs again. Try to get hold of Win XP disc. Plus it's creating the partition as FAT32 and NTFS is better.


Hi, Ive just talked to my neighbor and he's given me a copy of Windows Vista he's never used , Would it be worth trying to install that just to see how far things go ..?

---

### Post by darkod on 2009-11-20
@maddad
No, you don't need the recovery discs again. If I am correct you are booting now with ubuntu live CD with Try Ubuntu option, right?

In that case you can use Gparted to shrink /dev/sda1 because it's taking the whole hdd. Open Gparted, delete /dev/sda5 and /dev/sda2 because they are useless now (BE CAREFUL, not the /dev/sda1 where Win XP is!!!!).
Then when only /dev/sda1 is left, shrink it to size you want to keep for XP system partition. Be careful to shrink it sothat the free space is right of (after) the partition, not before it.

After you have created space for Ubuntu, boot with the Ubuntu CD again, select Install Ubuntu option and you can manage from there if you already had it installed once.

PS. It's up to you if you want to give Vista a shot. But be careful, you do not have license for Vista and it might even not work after a while because they can detect if both your neighbor and you have installed the same.

---

### Post by scottuss on 2009-11-20
> **maddad said:**
> ... and now she is saying that her friend came around to install Windows 7 as a surprise for me. ( some surprise ) , so it now looks that her friend has messed up my PC...


That's grounds for divorce! :P

Seriously though, why would people think that installing Windows 7 is a good thing? If my Mrs stuck Windows 7 on any of my PC's I'd be outraged. Anyway, back to my actual point of posting: Did you ask this "friend" exactly what they did and what the state of the system was when the "upgrade" was attempted? It might give you a better indication of what's going on...

Edit: Seems like someone has already suggest a good fix for this.

---

### Post by maddad on 2009-11-20
> **darkod said:**
> @maddad
No, you don't need the recovery discs again. If I am correct you are booting now with ubuntu live CD with Try Ubuntu option, right?

In that case you can use Gparted to shrink /dev/sda1 because it's taking the whole hdd. Open Gparted, delete /dev/sda5 and /dev/sda2 because they are useless now (BE CAREFUL, not the /dev/sda1 where Win XP is!!!!).
Then when only /dev/sda1 is left, shrink it to size you want to keep for XP system partition. Be careful to shrink it sothat the free space is right of (after) the partition, not before it.

After you have created space for Ubuntu, boot with the Ubuntu CD again, select Install Ubuntu option and you can manage from there if you already had it installed once.

PS. It's up to you if you want to give Vista a shot. But be careful, you do not have license for Vista and it might even not work after a while because they can detect if both your neighbor and you have installed the same.


Hi,  The copy of Windows Vista has never been used and my neighbor has told me 
I can keep it , so as ive not got a copy of Gparted yet, if I for now installed Windows Vista 
with the current problem I have ,  do you think it would install ok  as its a direct Vista OS disk and not Recovery disks ?
 


Thanks

---

### Post by darkod on 2009-11-20
OK, first of all, Gparted is on the Ubuntu CD, you don't need separate copy.
But if you want to use Vista, install that before installing Ubuntu.
Yes, Vista will install perfect regardless of this "problem". And it's much better that it's a Vista OS disc and not recovery disc.
But when installing Vista be sure to leave enough unpartitioned space on the HDD for Ubuntu. Make calculation about how many and how big partitions you like before starting with Vista.

---

### Post by maddad on 2009-11-20
> **darkod said:**
> OK, first of all, Gparted is on the Ubuntu CD, you don't need separate copy.
But if you want to use Vista, install that before installing Ubuntu.
Yes, Vista will install perfect regardless of this "problem". And it's much better that it's a Vista OS disc and not recovery disc.
But when installing Vista be sure to leave enough unpartitioned space on the HDD for Ubuntu. Make calculation about how many and how big partitions you like before starting with Vista.


Thanks again, Ive just found the Gparted ...

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06637.jpg[/IMG]

So I am first going to have a go with that , and I will post back how things Go, 

Many Thanks

---

### Post by darkod on 2009-11-20
You see the keys/locks next to /dev/sda2 and /dev/sda5? That means the partitions are mounted. You can not delete them until you unmount. Just right click on one and unmount. Then the other one. After that you can delete them and try to shrink /dev/sda1.

---

### Post by maddad on 2009-11-20
Just tried to delete .....  /dev/sda5 and /dev/sda2  but the Delete is grayed out , only 
/dev/sda1 fat32 has the delete option , am I missing some thing ?

---

### Post by maddad on 2009-11-20
> **darkod said:**
> You see the keys/locks next to /dev/sda2 and /dev/sda5? That means the partitions are mounted. You can not delete them until you unmount. Just right click on one and unmount. Then the other one. After that you can delete them and try to shrink /dev/sda1.


Thanks, just posted before I saw this.

---

### Post by maddad on 2009-11-20
> **darkod said:**
> You see the keys/locks next to /dev/sda2 and /dev/sda5? That means the partitions are mounted. You can not delete them until you unmount. Just right click on one and unmount. Then the other one. After that you can delete them and try to shrink /dev/sda1.


Just tried and I get this .. /dev/sda5 no unmount option shown ...

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06638.jpg[/IMG]

and with ....  /dev/sda2 the unmount is grayed out  .....

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06639.jpg[/IMG]

---

### Post by darkod on 2009-11-20
How about Swapoff? Sorry, I guess that's the option for the swap file. I think /dev/sda2 will get the option to be deleted after that.

---

### Post by maddad on 2009-11-20
> **darkod said:**
> How about Swapoff? Sorry, I guess that's the option for the swap file. I think /dev/sda2 will get the option to be deleted after that.


ok, this is what ive got left after deleting ... /dev/sda2 and /dev/sda5


[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06640.jpg[/IMG]

so now I have to re size /dev/sda1 - where the small Grey box is on the far Right ..? 
any ideas what size would be correct , sorry to be a pain

---

### Post by darkod on 2009-11-20
OK. First you can see in the bottom that the operations are just booked and pending. Click on the big green tick mark to execute them first. Only then the partitions will be deleted.

After that, click once on /dev/sda1 and in the menu Partition there will be Resize or Shrink/Expand (don't remember exactly). That will open a window to shrink the partition. You need to drag the right end to the left, shrinking it. The size will keep changing while doing that.
After you are happy, close that resize window and again you will need to click on the green tick mark to execute the operation. And the resize might take a while...

---

### Post by maddad on 2009-11-20
> **darkod said:**
> OK. First you can see in the bottom that the operations are just booked and pending. Click on the big green tick mark to execute them first. Only then the partitions will be deleted.

After that, click once on /dev/sda1 and in the menu Partition there will be Resize or Shrink/Expand (don't remember exactly). That will open a window to shrink the partition. You need to drag the right end to the left, shrinking it. The size will keep changing while doing that.
After you are happy, close that resize window and again you will need to click on the green tick mark to execute the operation. And the resize might take a while...


Thanks again, just waiting for the re sizing , as its 1.25 AM in the morning here I will post back later how things go, Many Thanks for your help, its appreciated

---

### Post by gradinaruvasile on 2009-11-20
It is interesting that the /dev/sda1 has fat32 file system on it. Windows uses ntfs and ntfs is also known by Ubuntu.
Anyways if u done resizing the partition you should try mounting it from the live cd to see whats on it.

---

### Post by presence1960 on 2009-11-20
> **gradinaruvasile said:**
> Well somethings not right... where is sda3 and 4? (just a rhetorical question)...


In an extended partion the first logical partition is sdx5 whether or not there is a second or third primary partition. In this case there is a primary partition (sda1) and sda2 is an extended partition. There are no other primary partitions. thus the next partition is the logical partition inside sda2 (extended partition) so the numbering begins at sda5.

---

### Post by maddad on 2009-11-21
Well this is an up date, after great help from you Guy's I finally managed to get the ACER E500 up and running with both Ubuntu and Windows XP, I played about with Ubuntu for some time which I really like the look of, before turning the PC off and going to bed. This morning wanting to check out Ubunta some more, I booted up the PC , only to be met by a constant boot up, cycle . I could not get the PC to load any thing , so I put back the Ubunau live CD and booted up the PC once more , this is screen which just stays there.....

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06653.jpg[/IMG]


This is a bit like a roller coaster ride , and at the moment I am down. :frown:

The wife's not speaking to me  [-( , as I said it was all her fault and my neighbor keeps telling me I should have bought a Mac. 

Not too sure where to go from here ,  apart to the local Bar. 


Thanks

---

### Post by Bartender on 2009-11-21
There are at least 3 or 4 things not making any sense here.

1) Any Windows XP recovery discs would have installed the NTFS file system, not the antiquated FAT32 file system.
2) Where the heck did the original GRUB errors come from unless the "friend" installed Linux?  It almost sounds to me like the "friend" botched things up and tried to install Linux in some sort of mis-guided attempt to fix things or retrieve data or get it back to where it was before you found out...is this the same guy who's saying you shoulda bought a Mac?  
3) The error message posted in #45 looks like the PC is trying to boot from HDD.  You sure that the optical drive is #1 in BIOS?  It doesn't make any sense that it would have been working last night, then screwed up again in the morning.  Unless there are hardware problems too.  Did anyone go inside the PC and monkey with cables?  I'm just wondering if the cable to the optical drive or HDD could be loose.  I had a dual-boot PC once that would boot into Windows but not Linux.  Turned out the old-school IDE data cable to the HDD was a little bit loose.

---

### Post by gradinaruvasile on 2009-11-21
Set the cd to be the first boot drive. It wants boot from the HDD still.

I suggest booting from live cd, backing up your personal files to a usb stick or whatever, then delete all partitions on the hdd, and after that do a clean XP install - from an install CD, not tha acer recovery stuff. Then if u want, install Ubuntu (be sure u have at least 3 partitions available, one for XP, one for Ubuntu, one swap for Ubuntu).

---

### Post by maddad on 2009-11-21
> **Bartender said:**
> There are at least 3 or 4 things not making any sense here.

1) Any Windows XP recovery discs would have installed the NTFS file system, not the antiquated FAT32 file system.
2) Where the heck did the original GRUB errors come from unless the "friend" installed Linux?  It almost sounds to me like the "friend" botched things up and tried to install Linux in some sort of mis-guided attempt to fix things or retrieve data or get it back to where it was before you found out...is this the same guy who's saying you shoulda bought a Mac?  
3) The error message posted in #45 looks like the PC is trying to boot from HDD.  You sure that the optical drive is #1 in BIOS?  It doesn't make any sense that it would have been working last night, then screwed up again in the morning.  Unless there are hardware problems too.  Did anyone go inside the PC and monkey with cables?  I'm just wondering if the cable to the optical drive or HDD could be loose.  I had a dual-boot PC once that would boot into Windows but not Linux.  Turned out the old-school IDE data cable to the HDD was a little bit loose.

Hi, The wifes friend is not the same person  who said get a Mac,  when I went to bed last night the only thing I did was move the PC from the basement to a bedroom, currently ive now managed to get the GRUB menue back  .....

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06657.jpg[/IMG]

and when I select Ubuntu generic , it loads all Ok, but when I select Windows XP I now get this on screen ....

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06658.jpg[/IMG]


When I press any key to restart, it just boots into Ubuntu and runs OK, ive checked inside the PC and found no loose cables, ive tried to contact the wifes friend who messed things up, all they are saying is that they tried to install Windows 7 , but it went wrong, I think there's more to the story some where, so at the moment I now can boot into Ubuntu but not Windows XP,  not too sure where to go from here ?


Thanks

---

### Post by zuerston on 2009-11-21
"[B]My Wife's been messing around"  well well, i would certainly keep an eye on her! 
:D:D:lolflag:
[/B]

---

### Post by maddad on 2009-11-21
> **zuerston said:**
> "[B]My Wife's been messing around"  well well, i would certainly keep an eye on her! 
:D:D:lolflag:
[/B]


She has gone to see her Mother since we had a few words about her and the friend messing up my PC, hopefully I can  fix this problem then I am going to give the PC to her and get my self a new One, then lets see how she gets on :D but at the moment I could do with some advice about the NTLDR and what to do next ?

---

### Post by darkod on 2009-11-21
Since Ubuntu is working, boot Ubuntu, open /dev/sda1 (mount it if necessary) and in the root of /dev/sda1 (not Ubuntu root) see if the files ntldr and ntdetect are there.

PS. Since your situation has changed a bit, it would be good to run:
sudo fdisk -l

again and post the result here to see the partitions.

---

### Post by zuerston on 2009-11-21
> **maddad said:**
> She has gone to see her Mother since we had a few words about her and the friend messing up my PC, hopefully I can  fix this problem then I am going to give the PC to her and get my self a new One, then lets see how she gets on :D but at the moment I could do with some advice about the NTLDR and what to do next ?

I would just load that Live CD up if you can ,and then click the install icon on desktop and when it gets to the Hard drive stuff ,tick the **"use entire drive"** and it should delete all partitions and re-format the whole thing and then it will install Ubuntu.
can you get it to boot the live cd?

Fook window$!  ,and don't give **anyone** the passwords after you do get it installed!

---

### Post by confused57 on 2009-11-21
I'm not familiar with Grub2(1.97beta), but from what I've read you might try this in a terminal:
```
sudo grub-mkconfig
```
as described here:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig)

This "shouldn't" hurt anything, but it might re-detect & add the correct entry for XP in grub.

Sorry to interject, you're getting some great assistance here.

---

### Post by maddad on 2009-11-21
> **darkod said:**
> Since Ubuntu is working, boot Ubuntu, open /dev/sda1 (mount it if necessary) and in the root of /dev/sda1 (not Ubuntu root) see if the files ntldr and ntdetect are there.

PS. Since your situation has changed a bit, it would be good to run:
sudo fdisk -l

again and post the result here to see the partitions.


Hi,  I mounted /dev/sda1 , and looked for the files , this is all I could find, I noted that the Two files are not the same color as the rest ?

1.  ntldr

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06659.jpg[/IMG]


2. ntdetect

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06660.jpg[/IMG]


I ran the sudo fdisk -l , and this is what I got ..

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06661.jpg[/IMG]


Thanks again

---

### Post by darkod on 2009-11-21
Ok, they are there. Now open:
gedit /boot/grub/grub.cfg

and look for a section starting with something like
*** BEGIN   30_os-prober
menuentry Windows XP etc..{

Copy that part from menuentry until the closing }, it's few lines. Or take a screenshot. That will show us where grub is looking for ntldr.

---

### Post by maddad on 2009-11-21
> **zuerston said:**
> I would just load that Live CD up if you can ,and then click the install icon on desktop and when it gets to the Hard drive stuff ,tick the **"use entire drive"** and it should delete all partitions and re-format the whole thing and then it will install Ubuntu.
can you get it to boot the live cd?

Fook window$!  ,and don't give **anyone** the passwords after you do get it installed!


That's my aim, but as I am still very new to Ubuntu I really need to be able for now to 
boot into both Ubuntu and Windows XP.  Ive borrowed this laptop I am using for now 'but I will have to return it soon .

---

### Post by maddad on 2009-11-21
> **darkod said:**
> Ok, they are there. Now open:
gedit /boot/grub/grub.cfg

and look for a section starting with something like
*** BEGIN   30_os-prober
menuentry Windows XP etc..{

Copy that part from menuentry until the closing }, it's few lines. Or take a screenshot. That will show us where grub is looking for ntldr.


Ok this is what I get ...


# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set cb55da26-a200-41c2-87c5-4a6e30b0123e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb55da26-a200-41c2-87c5-4a6e30b0123e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cb55da26-a200-41c2-87c5-4a6e30b0123e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb55da26-a200-41c2-87c5-4a6e30b0123e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cb55da26-a200-41c2-87c5-4a6e30b0123e ro single 

initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1d0f-11d5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by darkod on 2009-11-21
It looks correct.
It's a move of desperation but you can try to let grub2 update itself, in terminal just execute:
sudo update-grub

Reboot and check if the WinXP entry will work. I think it's small chance because grub.cfg looks correct, but it's worth trying.

---

### Post by maddad on 2009-11-21
> **darkod said:**
> It looks correct.
It's a move of desperation but you can try to let grub2 update itself, in terminal just execute:
sudo update-grub

Reboot and check if the WinXP entry will work. I think it's small chance because grub.cfg looks correct, but it's worth trying.


Ok, and thanks I will try it now

---

### Post by maddad on 2009-11-21
> **darkod said:**
> It looks correct.
It's a move of desperation but you can try to let grub2 update itself, in terminal just execute:
sudo update-grub

Reboot and check if the WinXP entry will work. I think it's small chance because grub.cfg looks correct, but it's worth trying.

Ok well I did the sudo update-grub , and got this ...

[IMG]http://i451.photobucket.com/albums/qq232/Filesaver1/DSC06662.jpg[/IMG]

then re booted into Windows XP  , but the same error message came on a black screen ...

[B]NTLDR is missing 

Press any key to restart [/B]

---

### Post by darkod on 2009-11-21
I am starting to think something got corrupted when shrinking your windows XP partition.
After the shrink, did you boot XP at least once? Windows likes to run those check disk tools when it detects partition resizing. Just a guess here. If it wasn't working even before installing ubuntu, this might be a result of that.
Although the message is that ntldr is missing...

Sorry, I really have no explanation for this. First of all your windows recovery should not have created FAT32 system and it did. That's also confusing me. But without a XP CD, you have little options.

One option might be to restore the MBR for XP, see if XP is working fine. And then restore grub2 on the MBR using Ubuntu LiveCD. If you are willing to try this?

PS. Is your XP Home or Pro?

---

### Post by maddad on 2009-11-21
> **darkod said:**
> I am starting to think something got corrupted when shrinking your windows XP partition.
After the shrink, did you boot XP at least once? Windows likes to run those check disk tools when it detects partition resizing. Just a guess here. If it wasn't working even before installing ubuntu, this might be a result of that.
Although the message is that ntldr is missing...

Sorry, I really have no explanation for this. First of all your windows recovery should not have created FAT32 system and it did. That's also confusing me. But without a XP CD, you have little options.

One option might be to restore the MBR for XP, see if XP is working fine. And then restore grub2 on the MBR using Ubuntu LiveCD. If you are willing to try this?


Hi, there are as you say some strange things going on here, I will try the restore again just to see how it goes, as its late here so I will try it tomorow and post back , thanks for your help and every one else who offered this noobie  some comments and advice, its really appreciated . I hope I can get the PC working again so I can learn more about Ubuntu.

---

### Post by darkod on 2009-11-21
If by restore you mean using the restore CDs again, they won't help much. They will mess up everything again.
If you have XP Home I found a disc image for you here:
[http://www.thecomputerparamedic.com/files/](http://www.thecomputerparamedic.com/files/)

Look for WXPHOME_EN.iso it's close to the top. Download it and burn it on CD. Since you have license purchased with the computer you are in titled to use downloaded images, they didn't give you a windows CD with the computer.

If the disc is what it says it is, you can use it just to install windows XP Home, without messing up your partitions. The only thing to check is whether it will work with the CD-KEY from your license.
You might give it a go, try installing XP Home but with this image, not your restore CDs. That will install it properly and just on your current partition, not on the whole disc. And it will format it as NTFS as it should be.
After that Ubuntu will have no problems, I'm almost sure about that. You will not even need to reinstall whole Ubuntu, just to restore grub2.

---

### Post by phillw on 2009-11-21
> **darkod said:**
> If by restore you mean using the restore CDs again, they won't help much. They will mess up everything again.
If you have XP Home I found a disc image for you here:
[http://www.thecomputerparamedic.com/files/](http://www.thecomputerparamedic.com/files/)

Look for WXPHOME_EN.iso it's close to the top. Download it and burn it on CD. Since you have license purchased with the computer you are in titled to use downloaded images, they didn't give you a windows CD with the computer.

If the disc is what it says it is, you can use it just to install windows XP Home, without messing up your partitions. The only thing to check is whether it will work with the CD-KEY from your license.
You might give it a go, try installing XP Home but with this image, not your restore CDs. That will install it properly and just on your current partition, not on the whole disc. And it will format it as NTFS as it should be.
After that Ubuntu will have no problems, I'm almost sure about that. You will not even need to reinstall whole Ubuntu, just to restore grub2.

hi, just getting my OP to download the image and we're going to try it. I have an xphome iso image ftp'ing it's way over to a server - if  one above fails & the one i send is okay - I'll drop you the link in.

the xphome image from there is a good image. beat my upload by 3 minutes - lol

Phill.

---

### Post by maddad on 2009-11-21
Thanks Guy's the help and support here is really Great and Its really appreciated .

---

### Post by raymondh on 2009-11-21
> **maddad said:**
> Thanks Guy's the help and support here is really Great and Its really appreciated .

If you decide to re-do .....

1.  Download and burn 9.04
2.  Restore your existing XP thru the restore function of acer
3.  You may not be able to boot into windows so .... boot into the 9.04 liveCD
a.  Check CD for defects and MD5 sum
4.  Install 9.04.  In step 4, select SIDE-BY-SIDE.  There is a slider below (same window) that you have t grab with your mouse and slide.  When you do, you will see the sizing change (same window).  Slide to desired Ubuntu partition size (at least 20GB).
5.  In step 7, select ADVANCED and make sure that GRUB (this will be legacy and not grub2) is to be installed in the MBR of the HDD ..... which should be the first to boot in BIOS.
6.  As you had booted into the liveCD, at start-up, you need to go into BIOS and set the HD to boot first and save as default.

That's how I did my D250.  Grub overwrote and is now the bootloader.  Hope this may help you or give you clues (at least).

Good luck.

---

### Post by maddad on 2009-11-21
> **darkod said:**
> If by restore you mean using the restore CDs again, they won't help much. They will mess up everything again.
If you have XP Home I found a disc image for you here:
[http://www.thecomputerparamedic.com/files/](http://www.thecomputerparamedic.com/files/)

Look for WXPHOME_EN.iso it's close to the top. Download it and burn it on CD. Since you have license purchased with the computer you are in titled to use downloaded images, they didn't give you a windows CD with the computer.

If the disc is what it says it is, you can use it just to install windows XP Home, without messing up your partitions. The only thing to check is whether it will work with the CD-KEY from your license.
You might give it a go, try installing XP Home but with this image, not your restore CDs. That will install it properly and just on your current partition, not on the whole disc. And it will format it as NTFS as it should be.
After that Ubuntu will have no problems, I'm almost sure about that. You will not even need to reinstall whole Ubuntu, just to restore grub2.


Some One some where has put a curse on this :D Ive tried Three times to download the 
WXPHOME_EN.iso , and each times the download gets to 99% and stops, I tried different download managers as well , still no luck :frown:

---

### Post by darco on 2009-11-22
Strange, I d/l it just fine.....you can check some of the torrent sites for the .iso as well.


darco

---

### Post by maddad on 2009-11-22
Well yes another development , the son of the person who messed up my PC has just called and given me a new HDD , ( its actually larger GB than the original one ) and said they were sorry for all my computer problems, so now I have a larger brand new HDD , so I now have to think what to do next, I would like both Windows XP and Ubuntu on my PC as I would like to learn more about Ubuntu . May be I can install the New HDD first then install Windows XP back using the ACER recovery CD's , then install the old HDD as a slave and try to do some thing with Ubuntu on that . Talk about a roller coaster ride :D

---

### Post by 00b00nt00 on 2009-11-22
maddad, it seems that you're in a bit of a pickle. My ten cent's worth:

You need a working computer, so how about allocating all of the new HD to Ubuntu, and running Windows XP (or Vista) in Virtualbox? At least then you will have a working PC.

Then, when you have a free afternoon, you can try to use the XP recovery discs on your old HD again, and play around (like your wife) until you have a satisfactory system.

---

### Post by darkod on 2009-11-22
We are starting to get you "all over the place" with different advice but I would even look at torrents first for a XP Home ISO rather then using the recovery discs. Teh yonly mess up things, plus they create your XP partition as FAT32 which has been long gone situation. It should be NTFS. Make another try to get XP ISO, that will solve it for the future too. You will have XP disc to restore or reinstall XP whenever you like, without the recovery discs destrying everything that was on the HDD because that's what they are actually doing.

PS. If you decide to start again and use the recovery CDs on the old or new HDD, I wouldn't shrink the partition the recovery CDs will create at the same time with the ubuntu installer. Part of the problem might be corrupted files during the shrink, or even just XP refusing to "accept" the shrink with running disk checks. After you have used the recovery CDs (which I do NOT recommend), boot with ubuntu Try Ubuntu option and use Gparted to shrink, I think you did that last time too. Do NOT install ubuntu right away.

Boot into XP at least once, at boot if it asks for HDD checks let if finish them, then you might as well boot few more times into XP to see if everything is good and it has "swallowed" the shrink.

Only when you are sure you have a working XP boot the ubuntu CD and select Install Ubuntu and continue installing on the free unpartitioned space created with the shrinking.

---

