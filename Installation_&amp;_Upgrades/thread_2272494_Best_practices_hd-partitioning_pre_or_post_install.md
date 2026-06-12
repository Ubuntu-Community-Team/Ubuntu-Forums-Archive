---
title: "Best practices hd-partitioning pre? or post? install.Can you partiton post install?"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by gregory10 on 2015-04-07
I have in mind quite a complicated set-up for Development of a CMS and a mobile app I am working on.
I'm installing on an Asus Zenbook UX303LA. I have 64GB for the Ubuntu so will need to use a backup device before long so not to congest the machines storage files.

What I had in mind is 
UEFI   /boot
50GB / windows 8.1
24GB /Root
10GB /Home
20GB /AMPPS <----- this is a web development stack like LAMP or AMP
10GB / Node.js-MongoDB-Ruby(or some alternative) <----- this is another development stack but for creating a mobile app.

MY QUESTION IS: 
What is the best way to do this? Is it possible? Can I have web server setups in two petitions on the Ubuntu OS?
Do I just create these partitions all together when I install Ubuntu along side Windows 8.1 as a dual boot system(or can I leave space for the partitions and make them later)?
Obviously the AMPPS web server development stack has to be set up later as does the Node.js-MongoDB setup but is this normal practice?
Is there anything wrong with this plan?

---

### Post by dino99 on 2015-04-07
you cant do an installation without formating/partitioning first; but you always can resize these partitions after installation if you want/need (on unmounted partition indeed)

as you are limited by the 64 gb you might set / to 15 gb max its enough, a swap partition <= your ram, and the rest for /home

---

### Post by mikewhatever on 2015-04-07
Any particular reason to try and keep it all separately? Why do you want root, home and ampps, or, as you might like to put it, what's the best (and the second best...) thing about it, and why?

---

### Post by gregory10 on 2015-04-07
@mikewhatever
It just seems logical to me to have those particular apps on a separate drive is all. I like to have things tidy. and it's about space and using that space.
Its easy to see how much of any particular space is used up then I can do some house work so to speak and store what i no longer need or is superfluous onto an external drive.
Same with the Home space being separated from the root space. Its all about house work and knowing how much I have to work with simply by looking at it.

Its about organisation and workflow. I know everything on that particular part of the drive is for one purpose so things aren't getting fragmented in any way. 
Same with the home directory. My project docs are all in there and wrote a little program that opens up every app I need for any single project. Its clean
one folder in that home directory is one project. open up a console hit the up arrow key until that project shows and one click I'm working same with closing it
close the console and that's it they all close with it. I'm trying to keep things organised and concise is all.

I know this is not normal practice but I am going to be running a bigger system before long so need practice at this level and get some habits.
Also for backup. I want to be able to backup all partitions separately in an image file so if anything goes wrong with any particular thing I have the backup image
to fix it easily and simply.

---

### Post by gregory10 on 2015-04-07
@9d9
thanks so much for answering the question and for the links that's just what I needed. 
I got my answer going to sign this as resolved as soon as I do the install. Working slow and being careful.
I just want to do a thorough job because I know it will save me time in the future if I plan it well. I want to be confident before doing this installation(its dual boot with windows 8.1).
Its a good machine and just want to do this right.

---

### Post by deadflowr on 2015-04-07
Why such a small /home?

---

### Post by gregory10 on 2015-04-07
@deadflower
such a small home because for one I only have 64GB to work with. The other main reason is because most of my work is going to be done in the other partition(s).
after reading through one of those links that ubfan1 gave looks like I change my my scheme to:

\swap ,<============== 8GB
\root  <=============== 24GB
\media\win_exchange <== 4GB
\home <============== 10GB
\srv <================ 20GB

But here's the thing: it seems more logical to me to have that '\media\win_exchange' the data exchange partition parked right next to the windows partition.
At this stage another question comes to mind: What order do I have the partitions in and what order do I have to have the partitions in?
does it have to be \swap followed by \root like in all the tutorials or doesn't it matter?

On the drive it goes like this once I have collapsed the that restore partition on windows by making the usb backup that windows has in one of their tutorials.
Once I do that restore I can delete that 12GB and take it back which makes up my 64GB for the Linux instal
The reason the Ultrabook was so cheap is that Asus trimmed back on everything but still gave high definition touch screen and everything else.
The drive is only 128 GB So not much to work with unless I use a backup drive. I got one and its 500GB dedicated to this machine.
Also have to upgrade the ram to 8GB the one I purchased only has 4GB ram.

So the total SSD Hard drive is 128GB

/-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------\
                                                             HARD DRIVE STARTS-128GB
\-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------/

<----------ESP/EFI PARTITION--------------> <----------- The factory set EFI partition as agreed to by manufacturers consortium body (closes off initial part of the drive from malware)
\UEFI Boot <============== Fat 32 100MB LBA primary
<----------ESP/EFI PARTITION-------------->
<----------WIN factory-set OEM--------------> <----------- The factory set Windows install (all set up according to their contract I guess)
\WIN-sytem-restore <=======  128MB (reads as unformatted primary but it's full)<--------------- Dos tools if windows breaks or errors manifest.
\WIN-8.1 OS <============  54.42GB ntfs primary
<----------WIN factory-set OEM-------------->

<----------------LINUX INSTALL---------------> <----------- below a scheme yet to be finalised (I need your comments) 64.60GB to work with
<---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
\media\WIN-exchange <===== 4GB ntfs <------------- I'm not sure if the 4GB is overkill might go with 3GB
\swap <=================  8GB SWAP <--------- Aiming to upgrade the ram to 8GB soon as I can afford it
\rooot <=================  24GB ext4 <---------- the tutorial said if the root partition gets congested you system ceases to function
\home <================= 10GB ext4 <---------- Having drive separate helps stop root partition from congesting opens easy monitoring
\srv <=================== 18GB ext4 <---------- The same as with the \home drive I can monitor then save to backup if it gets full
<---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<----------------LINUX INSTALL--------------->
/---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------\
                                                                  HARD DRIVE ENDS-128GB
\---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------/

QUESTION:
Is it ok to have: the '\media\anyNameYouChoose' <=Partition; before the '\root '<=Partition; on a linux install?

I noticed in some of the tutorials that the data exchange partition was mentioned as an option but none of them stipulated whether it had to be after the '\root' partition.
All of those tutorials did put it after the root partition though, so I am wondering if it is good or bad idea to put it before \root.
They did seem to have the \swap partition before the \root partition though (Or at least they mentioned the \swap partition before they mentioned \root

Anyway that's my revised plan after the comments I have received from this thread. Is this right or wrong in practice (to have partitions before root)?
In my mind it's logical to have it next to windows so to be able to pass data from one to the other as I work on one or the other.
Same with the \swap partition does it go before \root or after (does it matter)?

Thanks for anyone who can contribute
and thanks for all the input so far it has really helped
 I need the advice.
G

---

### Post by gregory10 on 2015-04-08
At this stage I am starting to think the best thing to do is to do a full install of Ubuntu 14.04.2 and rid this machine of windows for ever.

I just tried to do a backup of that recovery drive on the windows setup following their own instructions: they said
[http://windows.microsoft.com/en-AU/windows-8/create-usb-recovery-drive](http://windows.microsoft.com/en-AU/windows-8/create-usb-recovery-drive)

In step 7 of the tutorial on how to copy that recovery drive to a usb storage disk or memory stick.
[COLOR=#505050][FONT=WOL_Reg]"If you want to remove the recovery partition from your PC and free up disk space, tap or click [/FONT][/COLOR][COLOR=#505050][FONT=WOL_Bold]**Delete the recovery partition**[/FONT][/COLOR][COLOR=#505050][FONT=WOL_Reg]. Then tap or click [/FONT][/COLOR][COLOR=#505050][FONT=WOL_Bold]**Delete**[/FONT][/COLOR][COLOR=#505050][FONT=WOL_Reg]. This will free up the disk space used to store your recovery image. When the removal is done, tap or click [/FONT][/COLOR][COLOR=#505050][FONT=WOL_Bold][B]Finish."

[/B][/FONT][/COLOR]but guess what the said software they supplied gave me no option to delete that 12GB of disk space and free up the drive.
So I am disgusted with their monopolizing of my machine which I paid my money for and I now own.
So I got it in mind to delete theirpetty inept userpic distribution which is messing up my hard drive and getting in the way of my work.

Yes I'm really angry with their manipulations and pettiness they go too far. 
As for Asus shame on them for letting them do it on one of their machines. 
And for those reading please take note: when I first turned this machine on and started using it the machine had a resident Trojan on it.
Yes that's right before I even started using it and it was fresh out of a sealed package box it was infected. MsAfee was being used to carry Trajan visus(s)
those trojans need a horse to get in on apparently and they were using what is said to be an antivirus software but is actually a marketing tool. Its used to get user information.
In a very short time I had multiple trojans on my windows 8.1 system and all sorts of malware present. Lucky for me I had already made a backup of my own.
First deleted McAfee then started windows defender: windows defender kept stopping while running a full scan. I downloaded updates then it ran ok end of trojan plague.
That wasted a lot of my time but windows 8.1 is worse. I think it's a patched up mess that abuses users rights to full control of the machine they bought and paid for.

I didn't like Microsoft before this but now I have an absolute hatred for them. They have wasted a full week on my valuable time.

---

