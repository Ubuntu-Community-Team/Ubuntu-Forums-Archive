---
title: "A few ques. about partitioning and wireless networks"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by JollyRoger on 2005-10-22
I'm kind of new to linux, so hpoefully this question isn't too dumb, heh, but I want to dual boot my system with WinXP, and I have about 9 GB's free, and when I started to install Ubuntu, and I went to guided partition, it only game me three choices.  Sorry I don't know the details of each one, but the first one said something like parition 59 GB's, and the other two both started out with erasing the HD...  What should I do if I don't want anything erased?  How much is the minimum needed for Ubuntu?  I can free up more space if it is nessecary.  I was also wondering if wireless internet (or wireless networks in general) worked with Ubuntu.  In the installation it said it couldn't find the network...but its not a huge deal because most of the time I'm connected to the internet at college...

ok, thanks for everything :)

---

### Post by Herman on 2005-10-22
JollyRoger, just click on my signature link (bottom of post) for some info that might help you. I don't know anything about wireless networking though. Have you got a desktop or a laptop? You should check the laptop lists first to see if you laptop is listed. (three links under here).
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)
[http://www.ubuntu.com/support/custom/hplaptops](http://www.ubuntu.com/support/custom/hplaptops)
[http://linux-on-laptops.com/](http://linux-on-laptops.com/)
 Have you got FAT32 or NTFS with Windows XP? If you have NTFS, you should  create an extra small FAT32 partition while you are in the partitioner anyway, for passing files through between your two systems later on.
Also, 9.0 GB should be plenty, you can increase it later if you want, but it's harder to do things the other way around. Good luck, from (Herman).

---

### Post by JollyRoger on 2005-10-22
Its a laptop, and I'm not sure if I have FAT32 or NTFS (Its less than a year old if that helps)  and how would I create this extra small partion?  And thanks for all the info!  If I can't find what I'm looking for in there I'll just ask again

thanks again

---

### Post by Herman on 2005-10-23
Well you should have a look if it's FAT32 or NTFS by clicking on your 'My Computer' icon, (start menu), right-click on 'drive C', and click 'properties'.
You should be able to read there somewhere if it's FAT32 or NTFS.
If it's FAT32, you are in luck, because you will not have as much work to do to make it into an excellent dual boot computer! (Just follow the example in my link, and hopefully it'll all go smoothly for you.)
If it's NTFS, you can still do pretty much the same thing, but I didn't really set out to make my web page with NTFS in mind, so I added 'part two' on later. Have a look right down on the bottom of my web page, at 'part two', which explains how to make this partition as a seperate operation, after the fact.
See how you get some scary red screens? Well, to avoid getting those scary red screens, we need to figure out how to combine part one and part two as one streamlined single operation. Now I haven't got NTFS myself, and I don't want it either, so I can't do this myself, I'll have to guess what I think you should do. 
But before we waste a lot of space going into details about that, check and let me know if it's FAT32 or not, it might save us some work. (Herman).

---

### Post by JollyRoger on 2005-10-23
Unfortunatelly its NTFS, but your site is very informative, I'll see what I can do.

thanks again

---

### Post by Herman on 2005-10-23
Well I think a good plan it might go something like this then, and I hope this will be pretty accurate, I'm just using my imagination here; 

NOTE: These directions have been corrected on 28th Oct, and are not the same as those originally posted. (Herman).
1. Choose to manually edit the partition table
2. Select your Windows partition (59GB NTFS) (probably)?
3. select 'size: 59.0 GB'  
4. write changes to disk and resize the partition (yes).
5. Type in 'new partition size': 50.0 GB (for example)
6. Select 9.0 GB FREE SPACE
7. Choose 'create a new partition'
8. new partition size
9. change size to 1.0 GB
10. choose 'type for the new partition: 'logical'
11. location for new partition: the END of the available space
12. How to use this partition: change from ext3 to FAT32
13. Select 8.0 GB FREE SPACE
14. Automatically partition the free space
15. finish partitioning and write changes to disk
16. Finish Breezy installation




And hopefully, if it goes the way I'm guessing, you'll 'have the tiger by the tail'! You can just finish the install , it should go like on my website.
I could be severley embarrassed if it does something different after being so bold as to stick my neck out this far. I think this might be at least approximately right. This should give you an idea anyway, better than no help at all (I hope).
Also I hope you did check whether your laptop is one that is suitable on the supported laptops list too, and defragged and all that. Don't rush anything okay? (Herman).

---

### Post by JollyRoger on 2005-10-23
Well I got it installed, but when I tried to have two different partitions it didn't really seem to be working, but maybe I wasen't doing it the exact way you told me...sorry about that, but I think I'll juts do it the other way you have on your web-site, it works fine doing it that way dosen't it?

thanks again for everthing

---

### Post by Herman on 2005-10-23
Yes, that will be fine, JollyRoger, 'there's more than one way to skin a cat', it only means if you do need to be able to move files between the two operating systems, you'll have to do it by making a CD or CDRW. Well that won't hurt anyway, you can back up your stuff at the same time! Some people never need to move their files anyway. Just enjoy your new operating system, I'm happy for you that it went in okay! :D :
And a couple of more ways to move files are by network to another computer and then boot into your other OS, and send it back, or maybe use a USB device too. There are lots of ways to do things!
You'll still be able to copy files out of NTFS, you just can't paste things into it. Maybe you should wait and see, and make your extra partition some day if you need it.

---

### Post by Herman on 2005-10-23
Oh, did you mean you still want to put in the extra FAT32 partition by 'Part two' example method? Yeah, that should be okay too, if you want. I was just trying to think of a better way to do it all at once and save you from having to look at those red warning screens at the end. But it's okay to do it that way. :p

---

### Post by JollyRoger on 2005-10-23
thanks for the info again, that site really helped me out.  Now I just need to find out how to get the internet working in Ubuntu...heh

---

### Post by JollyRoger on 2005-10-24
I tried to create the extra partition, and I think I was doing everything right, and before I could change it to Fat32, it says the partition is unusable.... Any ideas of what I can do to change this?  To either change it to a usable partition, or if I can't do that at least add it back to the normal windows partition?

thanks

---

### Post by Herman on 2005-10-25
I'm not quite sure, but it sounds like you have created some kind of partition. Is it a FAT32 logical partition? If it is, try it out anyway, and see if you can paste a file into it from Ubuntu, and then go into Windows and receive the file. If you can, then it is okay!
If it is not a FAT32 logical partition, then what file type is it? ext3? 
I have read in another post where someone else was doing the same thing and they did the first part the way you did with the Ubuntu partitioner, and then used Windows XP to reformat the partition as FAT32, but I don't know why. Maybe you have to do that. Have a look in your Windows XP Control Panel, Administrative Tools, Computer Management, Disk Management and see if  you can 'see' your new partition, and tell me what it says about it. Is it coming up as FAT32? 'Healthy'? Or something else? Let me know and I'll do my best to help. (Herman).

---

### Post by JollyRoger on 2005-10-25
I think the partition I set aside to become the Fat32 just says Unallocated in Computer Management.  How would I go about formatting this to Fat32

I also had another question, I had a seperate partition right when I started setting Ubuntu up, its only about 200 megabites, is this fine to just leave alone?  I guess I should of asked earlier.

thanks for all your help though

---

### Post by Herman on 2005-10-25
Simply right-click on it, click 'format', and make sure the you set the file system type to FAT32 and see wht that does. 
It's okay to just ignore the other 200 MB one alone for as long as you like. Or we can discuss that later if you want. Let's just ignore it for now. (Herman).

---

### Post by JollyRoger on 2005-10-25
It actually dosen't give format as an option, at least I can't find it anywhere for that partitionwhen I right click on it it just lets me go to its properties.  On the Linux and its swap partition format shows up, but it won't let me choose that option.  The other 200 mb's isn't a big deal, I was just making sure it was ok to have.  Have an ideas as to what I should do?

thanks for all your help

---

### Post by Herman on 2005-10-25
You mean it's not there at all? Or, it's there but it's 'greyed out'? Doesn't matter, we'll keep on trying. Have you got an option for 'delete partition', that isn't greyed out? Probably if we do that first it will start co-operating, and the option for 'format' will become active.
If even that doesn't work, another way is to use Qtparted off a knoppix or a system rescue CD, both of which you should be able to download for free, and burn to a disk. Either of those will do, I have them both. Knoppix_v3.9.2005 is my favourite. I have knoppix std edition too, but it's a bit dark and secretive.
 While I'm waiting I'll look into Qtparted for you. I like helping people, and I can save the notes for next time. (We all can, and we'll all be able to do things better in the future). The best example of how to use Qtparted we have so far that I'm aware of is by zcox: [http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)
In his example, he uses qtparted for the resize, and then Ubuntu to automatically partition. But we already have the size, and we just want to format it. I'll look into that for you right now, and I think it will be an easy job.
Bye for now (Herman). :smile:

---

### Post by JollyRoger on 2005-10-25
The only options I get when I right click on the Unallocated partition is New Patition... (which is greyed out), Properties, and help.  It was the other partitions that had Format but it was greyed out, sorry, didn't mean to confuse you.  I really appreciate your help...Ubuntu seems like its a cool OS, I just need to figure these few things out heh.

thanks again! :)

---

### Post by Herman on 2005-10-25
Okay then, I used my Knoppix 3.9 CD, if you can download one of those, and burn one, they are a great thing to have, you can do lots of great tricks with Knoppix!
Try this:
How to format a partiton with Qtparted off Knoppix 3.9
1. Start Knoppix 3.9 (put it in CD drive and re-start computer)
2. 'K' menu,  System,  Qtparted
3. click /Union/dev/hda  (left-hand column)
4. View information on /Union/dev/hda, main (middle) feild.
5. Select your partition to be modified, and right-click on it for a menu.
6. &format,   (change partition type to FAT32), hit 'OK'.
7. File menu, (top right-hand corner), 'commit' to go through with the operation.
   (I chose 'undo', because I don't need to go through with it this time. When my
 new hard-disk arrives for my experimental computer, I'll be able to do more).  
8. When done, log out, restart computer.

---

### Post by Herman on 2005-10-25
If even that doesn't work, or for some reason that's not agreeable to you, then try the Ubuntu CD again, and 'delete the partition' again ,and just try reformatting with Ubuntu one more time. Failing even that...?:confused: 
Well, we'll all be experts in formatting partitions pretty soon anyway, but it would be nice to be successful experts! (LOL) Not just experts at messing around with it. (LOL). But other people can do this, so I know if we keep on trying, we can do it too. (Herman).:D

---

### Post by JollyRoger on 2005-10-26
I tried the Qtparted from Knoppix, and it didn't give me the option either..but I'll try to Ubuntu installer disc again, and thanks for all your help again, I really appreciate it. :)

---

### Post by Herman on 2005-10-26
JollyRoger, tell me more about this seperate 200MB partition you mentioned earlier; open up your 'terminal' in Ubuntu, (Applications, system tool, terminal),
and type in:              sudo fdisk -l               and press 'enter' for me, you will be asked for your password, then it should give you a list of your partitions and you might be able to copy them and paste them into a post, so we can have a look at them.
 I think I might have an idea what's wrong, I'm sorry. I should have thought of it right away when you mentioned about that other 200MB partition.

---

### Post by JollyRoger on 2005-10-26
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6541    52540551    7  HPFS/NTFS
/dev/sda2            6664        7240     4634752+  83  Linux
/dev/sda3            7241        7270      240975    5  Extended
/dev/sda4            7271        7296      208845   88  Linux plaintext
/dev/sda5            7241        7270      240943+  82  Linux swap / Solaris


This is what it came up with, but its weird, the partition I tried to make was about 1 GB., so it dosen't really look like its listed here.  I think I also saw somewhere it started at around 5,000, or something like that anyway.  I might of just screwed something up when I tried to partition it, but I don't know.

thanks for the help again

---

### Post by Herman on 2005-10-26
Okay, well I just woke up, and will have to go away for a while,  but let's see now... 
 So you have your Windows partition from 1    to   6541 NTFS      (sda1)
                         Ubuntu                 6664    to   7240 linux       (sda2)
                         Extended partition  7241     to   7270             (sda3),                  including:                                       7241     to   7270 swap     (sda5)
(your swap partition is inside your extended partition)
and then you have:                         7271    to   7296 linux plain text(sda4)

There's usually a sign underneath to say it isn't in disk order, and I just wanted to sort it out again and list it in disk order to help think about it. Now, I wonder why there's a gap between 6541 (the end of your Windows partiton), and 6664,(the beginning of your Ubuntu partition)?
Your Extended partition looks okay I think, (it has your swap partition inside it). And then you've got from 7271 to 7296 'linux plain text' ? (I don't know what that is?).  So, what's this 'linux plain text'?, it might be your 'unallocated' partition we were trying to convert to FAT32, but there's already that gap between your Windows and Ubuntu partition (that might be your 200MB one?)
But you have to have all your logical partitions inside your extended partition as far as I know. I suspect that gap has something to do with it. Unfortunately I'm already running late and have to go for a while. If you're still here when I get back I'll continue helping all I can, but really, there are probably lots of others who are better than me at this. I'll be back in around 30 hours, but I'll be tired. Bye for now, got to go, (Herman).

---

### Post by JollyRoger on 2005-10-26
well thanks for all your help, I'll try to figure it out somehow heh

---

### Post by Herman on 2005-10-27
How did you go, JollyRoger? Hey what does that gap between Windows and Ubuntu look like when you look at it in Xp computer management, in Qtparted? Can you remember what the Ubuntu installer partitioner said about it? 
The reason I'm asking is because I have a new notebook here with some kind of special software called 'PQService', (whatever that is), coming up as a seperate partition (2.93 GB). If yours has anything like that, we wouldn't want to wipe out any special software that's there for a reason. 
On the other hand, maybe you tried to follow my instructions, and made a 9.0 GB logical partition, then automatically partitioned off 8 GB of that for Ubuntu and swap. I thought the Ubuntu and swap would go to the first part of your 9.0GB, but it might have gone to the other end of it instead. If that is what happened, and you have 'FREE SPACE' in the middle (gap), maybe we can move Ubuntu and close up the gap. But we better be careful and go slowly and check everything first. It's probably just free space because it isn't coming up as a partition, but just make sure.

---

### Post by Herman on 2005-10-27
JollyRoger, I have now installed the new hard disk in my experimental computer and I am nearly finished installing a simulation of your set-up. Then I will solve your problem in my experimental computer first, and then let you know how I did it. You should wait if you can, however, I have to go again for a little while (work)  :smile:  (Herman).

---

### Post by JollyRoger on 2005-10-27
[QUOTE=Herman]JollyRoger, I have now installed the new hard disk in my experimental computer and I am nearly finished installing a simulation of your set-up. Then I will solve your problem in my experimental computer first, and then let you know how I did it. You should wait if you can, however, I have to go again for a little while (work)  :smile:  (Herman).[/QUOTE]

Actually, I tried to install a Nvidia driver, and it kind of messed up Ubuntu...so I just decited to start all over, sorry about that.  I just formatted the Ubuntu partition completely, and my unallocated partition became free space!
So I think I added them together, and then I made a partition of 1 GB off of all of that space.  I made the 1GB into a Fat32 finally, and used the rest of the partition for Ubuntu and your directions for mounting windows is working fine...so I think I solved it, even though I'm not sure what caused it in the first place.

Thanks for all your help again, I hope you don't go to too much trouble with the experiment there, sorry if you do.

But thanks for the help again :smile:

---

### Post by Herman on 2005-10-28
Okay then, JollyRoger, I'm glad to hear it's the working way you want now. Thanks for sticking around and not giving up. I'll still have fun with the experimental computer now that  have it working at last. I could have given you  much better instructions if I had it working sooner, (sorry about that). It's hard to get computer parts here in the Australian 'outback'. Thanks for letting me know it's okay now, too. I'll take it a little easier now, I have enjoyed working with you. Bye from Herman. :D

---

### Post by JollyRoger on 2005-10-28
Thanks again, you really helped me out!  Now I just need to get the internet to work in Ubuntu and I'll be all set heh

---

### Post by Herman on 2005-10-28
Maybe try making a post in 'hardware', under 'networking' with a suitable title to attract someone's attention. 
I found this link there, it might help, I' m not sure;
[http://ubuntuforums.org/showthread.php?t=81461](http://ubuntuforums.org/showthread.php?t=81461)
Good luck with it, having the internet working from Ubuntu allows you to make the best of your whole computer.  Windows is a good operating system, but it's too bad it gets so much adware, spyware, and viruses, etc. You waste all your time updating stuff and running scans to keep those under control. And the software you need to do that takes up some of your RAM. ('TSR's are 'terminate and stay resident' (in your RAM), and anti viurs programs are classic examples of 'TSR's)
 I don't allow Windows on the internet any more, only on rare occasions. It saves a lot of hassles. I still need to go on and keep my antivirus up to date though. If you pass files from the internet through your FAT32 partition into Windows, they can still have bad stuff in them that Ubuntu is immune to. Unless you watch what you are doing, you still need to keep your defences up to date in Windows. But you'll find you won't have to scan so often, and when you do, you'll hardly find any spyware etc, compared with before.
If you don't keep any important files in Windows, you can maybe do without the antispyware and anti-adware stuff that loads Windows up, and Windows will work a lot better. You can use it as an accessory to Ubuntu, and if it does get a virus, just re-install it! You need to convert all your files to Ubuntu useable formats before you can do that, it might be a lot of work. Anyway, good luck, and have fun! (Herman).

---

