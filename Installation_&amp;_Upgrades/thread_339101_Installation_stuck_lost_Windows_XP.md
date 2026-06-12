---
title: "Installation stuck lost Windows XP"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by helliewm on 2007-01-15
I have tried to install Ubuntu doing a dual boot and I clicked the option to use the availbable free space. The installation hung half way through so I quit it. I then tried to reboot and use Windows and it says "error opening operating system". I used a  XP OEM disc and went into Recovery Console but it still says error opening operating system.

How do get XP back or my data off?

Helen

---

### Post by confused57 on 2007-01-15
You might be able to use the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Maybe something here that might help:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by bigken on 2007-01-15
give this a try boot from windows xp cd when your promted select R for recovery console 
select the windows partition usually 1 the hit enter just hit enter again for password then type fixmbr enter fixboot enter exit enter the pc will now reboot to windows ;)

---

### Post by helliewm on 2007-01-15
When I go to in the XP OEM disc Recovery Console it says "Error Operating System!". However it will let me to a complete reinstall where I can see the partition with their old XP as its says 107gb which was total size of XP and the all their files. This is OEM disc I am using that I bought in July this year.

I do also have a Windows Upgrade disc from Windows 98 XP disc but this only has SP1 on it.

Its my Sisters machine unfortunately!

Helen

---

### Post by bigken on 2007-01-15
you could  try the ulitimate boot disc for windows and restore the registry

---

### Post by helliewm on 2007-01-15
How do I restore the registry as per the post above??

Also would Super Grub work or a Rescue CD such as Knoppix?

Also if I manually installed Ubuntu via the option to manually install the partItions as per the normal Ubuntu instalL process would I get XP back,

I can see THE  XP partition when I run the XP OEM disc as one of the partitions is 107GB. The Ubuntu install just got stuck half way in the install process. I was trying to a dual boot. 

Helen

---

### Post by bigken on 2007-01-15
take alook at this [http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by confused57 on 2007-01-15
> **helliewm said:**
> How do I restore the registry as per the post above??

Also would Super Grub work or a Rescue CD such as Knoppix?

Also if I manually installed Ubuntu via the option to manually install the partItions as per the normal Ubuntu instalL process would I get XP back,

I can see THE  XP partition when I run the XP OEM disc as one of the partitions is 107GB. The Ubuntu install just got stuck half way in the install process. I was trying to a dual boot. 

Helen

I'm not sure if Super Grub Disk will help, but one of it's uses is to restore Windows mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful)

---

### Post by bigken on 2007-01-15
if his windows partition is corupted the ulitimate boot disc might fix it by using the regisrty wizard tool this a great peice of kit and very powerful it has saved hours of scaning and repairs on win xp boxes for clients ;)

---

### Post by louieb on 2007-01-15
Yours is the second time I have heard of the problem and bigken's suggestion of fixmbr and fixboot did not work. It happen to me. I used the Knoppix live CD to copy the Documents and Settings directory to DVD. Never got XP to boot until I  reinstalled XP. I did not try to fix it with the Super Grub Disk wish I had. Even with the Documents and settings backup its still a pain to get XP set up the same as before.

---

### Post by helliewm on 2007-01-16
Is there a facitility in Knoppix to download FILES FROM C DRIVE TO  to DVD?

Helen

---

### Post by bigken on 2007-01-16
you can also retrive your files using ubcd4win ;)

the simplest way would be to pull the hdd and hook it to another pc ;)

---

### Post by helliewm on 2007-01-16
I have downloaded the UCD4win ( I think thats what it is called) rescue disc as per this forum but it is an exe program how do I burn it to disc using Ubuntu?

Helen

---

### Post by bigken on 2007-01-16
you need to look at the how too in the ubcd4win web page 

I made mine usuing windows 1st you need to copy the windows xp cd to a file then run the ubcd4win file then follow the prompts ;)

if you have downloaded the knoppix cd you might find this easier than the ubcd4win ;)

---

### Post by bigken on 2007-01-16
also if you can get into the xp terminal have run this command 

chkdsk /p /r

---

### Post by helliewm on 2007-01-16
I downloaded Knoppix but do not understand how to get the GUI. I downloaded by BTtORRENT

 TO DOWNLOAD IT BitTorrent, Download it, and visit the Knoppix BitTorrent Tracker, and click the "DL" link next to the image you want to download ( -EN or -DE ). Save that file, then run btdownloadgui KNOPPIX-[date].torrent. Leave the program running when your download has finished, as you'll be uploading it for other people.

I sudo to this in the terminal and it failed.

btdownloadgui KNOPPIX-[date].torrent

I need to download TO DISC  to it to run my on Sisters PC

---

### Post by bigken on 2007-01-16
the knoppix download should be a iso file which in ubuntu all you need to do is 
right click and burn to cd then boot from it its a live cd ;)

---

### Post by helliewm on 2007-01-16
At my sisters Knoppix will not Boot please see previous post my me above re Knoppix as it will not Boot as it has no GUI.

I have used Supergrub and it has went to Boot Windows on the menu and it let set there was no partition was it re did the Windows partition and it says it can restore to the state it was at the time of purchase but it will not let me do a System Restore that is blank.

Have I lost the data. Will KNoppix be able to retreive it?

Helen

---

### Post by aberry5555 on 2007-01-16
I have had this problem many times and there IS a simple solution, but not to easily get your drive back. If and when you wipe your drive, use extended partitions rather than primary ones. For some reason the primary partitions that Gparted etcetera create don't work well with original windows partitions, but they work fine as an extended partition, it's alot safer and alot less hassle I find.

---

### Post by helliewm on 2007-01-16
I do n't think I did wipe the drive I just choose the option to use the free space. Is this any different?

What is the best way to extract the data thats already on their?

Helen

---

### Post by bigken on 2007-01-16
cant you pull the drive from the pc and hook up too another as a slave or 
use a usb device this would be the easiest solution for you

---

### Post by helliewm on 2007-01-16
Don't know how to do this and its my Sister's PC? Hence if there is a Rescue Disc disc and I could just download the files and then reinstall?

Helen

---

### Post by bigken on 2007-01-16
ok can you boot into ubuntu if so look in places/computer and see if your windows partition is there if it is open it up and get your data ;)

---

### Post by helliewm on 2007-01-16
I am booting from CD. Does this make a difference.

Helen

---

### Post by bigken on 2007-01-16
yes it wont let you into the windows partion cant you just boot into ubuntu

---

### Post by helliewm on 2007-01-16
No nothing installed the system frozen/hung during the Ubuntu installation.

Helen

---

### Post by bigken on 2007-01-16
ok boot from the windows xp and see if you can do a repair install ;)

---

### Post by helliewm on 2007-01-16
Tried that it will not to a System Restore.

I have bought this download but how do I burn an exe program to disc. I only have Linux at home and its my Sisters PC.

[http://www.softplatz.com/Soft/Utilities/Backup/Windows-Partition-Data-Recovery-Software.html](http://www.softplatz.com/Soft/Utilities/Backup/Windows-Partition-Data-Recovery-Software.html)

Helen

---

### Post by confused57 on 2007-01-16
> **helliewm said:**
> Don't know how to do this and its my Sister's PC? Hence if there is a Rescue Disc disc and I could just download the files and then reinstall?

Helen
You can use the live cd to mount your Windows partition & copy to a USB stick, external hard drive, or if you have a 2nd cd/DVD writer:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

From the link, see what **sudo fdisk -lu** shows about your current partition table, your Windows partition is probably hda1.
You could always try to reinstall Ubuntu, maybe after you've recovered your data from Windows.

---

### Post by helliewm on 2007-01-16
I think the partitions are corrupted as I cannot do a system Restore using Super Grub.

That is why I bought this to see if I can download the files that on the hard disk. So long as I can get the file off. I can do a reinastll.

Could someone take a look at what I have bought?

[http://www.softplatz.com/Soft/Utilities/Backup/Windows-Partition-Data-Recovery-Software.html](http://www.softplatz.com/Soft/Utilities/Backup/Windows-Partition-Data-Recovery-Software.html)

Helen

Ps I have downloaded the above program its an Exe program how can I burn to CD/DVD using Ubuntu on my PC. Its my Sisters PC I have the problem with, that lives at her house so I am using PC ( at my house) to search the web and downlaod. I can run ubuntu on live CD on her PC.

They are 2 separate PC's at 2 separate houses. Mine is fine running Ubuntu, its my Sisters with the problem.

Helen

---

### Post by louieb on 2007-01-16
Perhaps you mentioned it but I did not catch it? How much memory does your sisters computer have? What type of processor? CD or DVD burner both, or neither?

Yes Knoppix comes with KB3  that is what I used to burn  my Document and settings folder to DVD.
You said the Knoppix CD would not boot on your sisters PC. My P2 computer will boot version 4 but won't boot the latest version (5 I think) of Konppix. Version 4 is out there to download. I really like it for a rescue CD. 
I know this is frustrating but don't give up. You can get the data off the PC.
But to do that you need to first learn do 1 of 2 things.
1. Boot the computer to a live CD that can burn a DVD or CD.    
or
2. Learn how to remove the hard drive and install in another computer.

The first option is only available to you if your sisters computer has enough memory and a burner. That why I am asking: How much memory does your sisters computer have? What type of processor? CD or DVD burner both, or neither?
Post that information here and we will try to help you.
P.S. I have not used the Acronis software you bought but I have herd a loot of good things about it. But I don't have a clue on how to use it in Linux or if it even can be used in Linux.

---

### Post by bigken on 2007-01-16
the software you have will restore lost or delete files you run this software in windows so if you reformat the drive then install the software it will restore the files I have used similar software in the past with lots of sucess only problem is when you save the retrived data you must save it to another hard drive or partition good luck 

I still think the knoppix rescue disc is your best option

---

### Post by helliewm on 2007-01-16
My Sister computer has 512 ram memory, 200gb and DVD/CD burner. Its fairly new 18 months old a Packard Bell.

Help.

Helen

---

### Post by bigken on 2007-01-16
dont you know anybody who could pull the harddrive for you and get the data for you ?

---

### Post by louieb on 2007-01-16
Well the good news is her PC should be able to boot Knoppix. It has enough of the right stuff to rescue her data.
Now the next step is getting Knoppix CD to boot on your sisters PC.
Will it boot on your PC? Burn it again at a very slow speed. 2x or 4x.
If that doesn't boot download and burn version 4 of Knoppix. 
Once you get Knoppix to boot. You should see an icon in the desktop for her Windows partition. Click on it and it should open the file manager and you should be able to see her data. 
When you get that done get back. and I will walk you through getting the data on DVD/CD. In fact I have Knoppix 4 up on another PC (P2 348 mb ram)
and i am going to burn something to CD. Just to refresh myself on how to do it.

---

### Post by helliewm on 2007-01-16
Thanks ever so much for that.  Just so you know I am in Bucks in the UK, for time differences.

Apologies for reposting but this is the bit where I am problems burning KNOPPIX to DVD/CD, I am stuck.

"I downloaded Knoppix but do not understand how to get the GUI. I downloaded by BTtORRENT and its the end of procedure I am stuck on.

TO DOWNLOAD IT BitTorrent, Download it, and visit the Knoppix BitTorrent Tracker, and click the "DL" link next to the image you want to download ( -EN or -DE ). Save that file, then run btdownloadgui KNOPPIX-[date].torrent. Leave the program running when your download has finished, as you'll be uploading it for other people.

I guessed and sudo to this in the terminal and it failed.

btdownloadgui KNOPPIX-[date].torrent

I need to download TO DISC from PC  (its at my house) to it to run my on Sisters PC ( at her house)"

Re Windows partition:

Also I put Supergrub in and just used the option to "Boot to Windows" but there was no Windows to Boot. It (Supergrub) wanted to create a Windows partition and then hung. When I went to fix Windows it said to make a back up of MBR ( I think) so I exited out. I did not want to make it worse.
 
I only HAVE Ubuntu on my own personal PC (at my house). My Sister has nothing on hers ( at her house- THE PC WITH THIS PROBLEM) I am using Ubuntu through the live CD to make sure my nephews are connecting to the internet if they need it. 2 separate house and 2 separate PCS.

And the software I brought as well see here, just another web site for it thats all, to sell it, it the same software as I previous posted about

[http://www.datadoctor.biz/bak-r.htm](http://www.datadoctor.biz/bak-r.htm).

I used friends computer to download that too.


How do I burn Knoppix as per my previous post? That I am stuck on see above where I reposted it inverted commas. It the last bit running the btdownoad GUI bit at the end of the download procedure that has me really stuck.

Thanks ever so much everyone for your help.

I am in the UK so am off to bed now.

Helen

---

### Post by bigken on 2007-01-16
I live berks helen bring the bloody thing to me and I will sort it for you :D

---

### Post by helliewm on 2007-01-17
Ken I have pmed  you. hank you so much. Where abouts are you? Can you email me [email]helen@wilkinson-makey.com[/email].

Don't worry I have excellent spam filters. 

I live in Lane End. The offending machine is in Stokenchurch down the road. I really just want to make sure all their data is foff.

This is doing someo0ne a favour and it goes wrong. The reason I did this dual boot was my Sister was downloading illegally Microsoft Software via Bit Torrent for her business!

Helen

Ps My Sister's screaming as it has my nephews GCSE course work on it.

---

### Post by bigken on 2007-01-17
dont panic it will be sorted lol I have emailed my number

---

### Post by louieb on 2007-01-17
Hi Y'all. Well if you don't remember I'm the one that opened my big mouth and suggested using Knoppix to burn the data to DVD. I thought the sisters PC would be able to do it. But it can't. In order to use Knoppix to burn a DVD, the PC has to have at least 1  gig of memory or 2 CD/DVD drives. You will just have to get the data off some other way.

I'm glad bigken is close to you. I was going to suggest finding a meeting of a local Linux Users Group. The Fort Worth LUG meeting are crazy and fun. People bring PC's,  new software, talk Linux, and help each other trouble shoot software and hardware problems.

---

### Post by helliewm on 2007-01-17
BigKen lives literally just down the road from me which is brilliant. I wish I had known this last week. I just spent a fortune having my lap top upgraded!

My Sister's PC is seriously sick looks like my teenage nephews and not very computer literate Sister and Brother-in-Law have not maintained it properly so it needed defraging. Hence when I went to use the free space to do a dual boot its completely wiped about Windows. 

When I did a dual boot on my laptop it worked perfectly hence why I did not think twice about doing on my Sisters machine.

I only offered to do a dual boot so they good use all open source software legally as they where downloading illegal software by Bit Torrent. Doing my Sister a favour has seriously backfired. 

Just hoping and praying Ken can retrieve their documents.

Thanks everyone so much for all your help.

Will update everyone with the outcome to this ongoing saga.

Thanks again

Helen

---

### Post by helliewm on 2007-01-25
Ken ( BigKen) has been absolutely fantastic. He managed to restore most of the documents although he was already to throw the machine out the window! The problem was that my Sister had not defragged her machine for months and it just did not occur to me to do so. 

It just amazing I ask for help on an international forum and meet someone who lives quite literally down the road from me.

So there is happy outcome to this saga and I have met a new friend who can help me on a professionally basis with IT/Computer problems,  as I work from home.

All rather amazing and I am immensely grateful to Ken.

Helen

---

