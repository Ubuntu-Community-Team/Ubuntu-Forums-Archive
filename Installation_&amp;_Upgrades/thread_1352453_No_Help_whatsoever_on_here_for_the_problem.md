---
title: "No Help whatsoever on here for the problem"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Asguard on 2009-12-11
I cannot believe that no-one knows why so many people have had the problem after the update a few weeks ago when ubuntu boots it just goes to sh:grub7 command and does nothing.

I am glad I never got rid of Microsoft XP now if this is what Linux is all about then it is a very bad product. I have never known microsoft to do this. i assume I am going to have to get rid of Ubuntu as know help has COME FORWARD.

What a bad advert this is for linux its just rubbish. You get no help whatsoever on this. The best thing to do is take if of the pc 

Why is there no help as to what to type in to the command to get it working again.

This is what I get is there anyone that can help on here as there seems to be  a lack of knowledge somewhere for this. Other wise I will just get rid of it and probably never try it again. It was so promising too but too nervous now what it will do in the future as you could lose everything, very bad indeed.

GNU GRUB Version 1.97 Beta 4

[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]

sh:grub7 

the cursor just flashes after grub7.


 What on earth does this all mean

---

### Post by darkod on 2009-12-11
> **Asguard said:**
> I cannot believe that no-one knows why so many people have had the problem after the update a few weeks ago when ubuntu boots it just goes to sh:grub7 command and does nothing.

I am glad I never got rid of Microsoft XP now if this is what Linux is all about then it is a very bad product. I have never known microsoft to do this. i assume I am going to have to get rid of Ubuntu as know help has COME FORWARD.

What a bad advert this is for linux its just rubbish. You get no help whatsoever on this. The best thing to do is take if of the pc 

Why is there no help as to what to type in to the command to get it working again.

This is what I get is there anyone that can help on here as there seems to be  a lack of knowledge somewhere for this. Other wise I will just get rid of it and probably never try it again. It was so promising too but too nervous now what it will do in the future as you could lose everything, very bad indeed.

GNU GRUB Version 1.97 Beta 4

[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]

sh:grub7 

the cursor just flashes after grub7.


 What on earth does this all mean

I don't know why it happens, and I agree it's "bad commercial" but you are not taking into account the main fact: it ONLY happens to wubi installs which IS NOT full ubuntu install the way it's supposed to work.
In my personal opinion the developers went too far trying to make trying ubuntu easy for windows users with wubi. It is not easy to make linux work inside windows, because that's what wubi actually is.
Install Ubuntu properly, as side-by-side dual boot, in its own partition with its own filesystem, and it will work as expected. They made a very big mistake because the updates are the same as with full ubuntu install, but wubi working inside windows creates issues with them I guess.
As for no help here, there are steps to make it work after that happens with wubi, long ago here on the forum. Do you need them?

---

### Post by Asguard on 2009-12-11
Hi thank you. I have installed this from a disc I made. It was fine until I done the big update and also its on another drive so no partition. When XP boots it asks whether I want XP ot Ubuntu so of course at the moment I have to say XP as Ubuntu is rubbish at the moment. Even if I reinstall on the other drive I am thinking I will still get the same problem or has a fix been done. As there is no way of finding out.

---

### Post by darkod on 2009-12-11
> **Asguard said:**
> Hi thank you. I have installed this from a disc I made. It was fine until I done the big update and also its on another drive so no partition. When XP boots it asks whether I want XP ot Ubuntu so of course at the moment I have to say XP as Ubuntu is rubbish at the moment. Even if I reinstall on the other drive I am thinking I will still get the same problem or has a fix been done. As there is no way of finding out.

To be honest, from your words I still didn't understand if you used wubi or not. If you installed using wubi.exe then it's wubi, regardless whether it's on another hdd or not.
Another way to check is to open Disk Management in windows (windows button + R, type diskmgmt.msc, hit Enter). If all the partitions shown on all the drives are NTFS, you have wubi. If there are partitions with unknown filesystem, it might be separate ubuntu partition because their filesystem can't be recognized by windows.

If you have wubi at the sh:grub prompt you are getting execute these commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

Depending on which partition/drive you installed wubi, you might need to replace /dev/sda1 with something else. sda, sdb, etc are first, second, etc drive, and the number is the partition on it.

Once you manage to get it right and boot into wubi, open terminal (in Applications-Accessories) and execute:
sudo update-grub2

That should sort it out. And I would really consider proper ubuntu install, in case this turns out to be wubi as I suspect.

---

### Post by Asguard on 2009-12-11
Hi well I havent a clue about wubi never even heard of it. It was Ubuntu I downloaded and states ubuntu when it used to start up.

They do both stae NTFS though. Has anyone else out there heard of this so called wubi I assume its yet another linux  os then. Beginning to think its not worth the hassle and stick with microsoft.

Will try it though. But I def downloaded ubuntu so do not understand why you think its the other.

---

### Post by PRC09 on 2009-12-11
Wubi is on the disc that you downloaded and is a function which allows you to install Ubuntu and use it from within windows. When you installed Ubuntu were you in XP or did you have to restart your machine with the disk? If you were in XP and put the CD in and the Ubuntu screen pops up and you installed it from there then it is a WUBI install. The reason everyone wanted to know this is that the possible solution if any would vary depending on which way it is installed.I hope this makes WUBI a little clearer.Both ways of installing will give you a dual boot appearance,  however not the same approach to solving your problem.At least this is my understanding of WUBI.

---

### Post by oldos2er on 2009-12-11
Is this the bug? [https://bugs.launchpad.net/wubi/+bug/484799](https://bugs.launchpad.net/wubi/+bug/484799)
There are some suggestions there to try.

---

### Post by freeburn on 2009-12-11
i'm quiet surprised with the attitude of yours. it may be frustrating but why you are attacking people who wants to help?

and what makes you think no one heard of Wubi?

i think first you should provide the information about how did you installed the OS.

did u you restart the machine and boot from the live disc or just installed from your xp?

---

### Post by presence1960 on 2009-12-11
> **Asguard said:**
> I cannot believe that no-one knows why so many people have had the problem after the update a few weeks ago when ubuntu boots it just goes to sh:grub7 command and does nothing.

I am glad I never got rid of Microsoft XP now if this is what Linux is all about then it is a very bad product. I have never known microsoft to do this. i assume I am going to have to get rid of Ubuntu as know help has COME FORWARD.

What a bad advert this is for linux its just rubbish. You get no help whatsoever on this. The best thing to do is take if of the pc 

Why is there no help as to what to type in to the command to get it working again.

This is what I get is there anyone that can help on here as there seems to be  a lack of knowledge somewhere for this. Other wise I will just get rid of it and probably never try it again. It was so promising too but too nervous now what it will do in the future as you could lose everything, very bad indeed.

GNU GRUB Version 1.97 Beta 4

[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]

sh:grub7 

the cursor just flashes after grub7.


 What on earth does this all mean

Is [this]("https://help.ubuntu.com/community/Wubi") what you did to install Ubuntu? If yes then you used wubi, which is not the same as a full, dedicated Ubuntu install to a partition on a hard disk. As such it has it's quirks and disadvantages.

Also if you want some help on here I suggest you tame your attitude. All of us on here are not paid support. We do what we do because we like to do it. We do it on our own free time, time that could be spent doing other things instead of helping someone anonymously in here for no compensation other than maybe thanks if someone remembers to say so.

Sometimes we must be patient as the person(s) who know the answer might not log in for minutes, hours or even days. 

In other words don't trash the surgeon who is going to operate on you prior to the surgery!

---

### Post by MelDJ on 2009-12-11
> **presence1960 said:**
> 
Also if you want some help on here I suggest you tame your attitude. All of us on here are not paid support. We do what we do because we like to do it. We do it on our own free time, time that could be spent doing other things instead of helping someone anonymously in here for no compensation other than maybe thanks if someone remembers to say so.

Sometimes we must be patient as the person(s) who know the answer might not log in for minutes, hours or even days. 

In other words don't trash the surgeon who is going to operate on you prior to the surgery!

+1
OP see: [http://lmgtfy.com/?q=GNU+GRUB+Version+1.97+Beta+4+%20%5Bminimal+BASH+-+like+line+editing+is+supported.+For+the+first+word%2C+TAB+lists+possible+command+completions.+Anywhere+else+TAB+lists+possible+device%2Ffile+completions%5D+%20sh%3Agru](http://lmgtfy.com/?q=GNU+GRUB+Version+1.97+Beta+4+%20%5Bminimal+BASH+-+like+line+editing+is+supported.+For+the+first+word%2C+TAB+lists+possible+command+completions.+Anywhere+else+TAB+lists+possible+device%2Ffile+completions%5D+%20sh%3Agru)

---

### Post by presence1960 on 2009-12-11
> **MelDJ said:**
> +1
OP see: [http://lmgtfy.com/?q=GNU+GRUB+Version+1.97+Beta+4+%20%5Bminimal+BASH+-+like+line+editing+is+supported.+For+the+first+word%2C+TAB+lists+possible+command+completions.+Anywhere+else+TAB+lists+possible+device%2Ffile+completions%5D+%20sh%3Agru](http://lmgtfy.com/?q=GNU+GRUB+Version+1.97+Beta+4+%20%5Bminimal+BASH+-+like+line+editing+is+supported.+For+the+first+word%2C+TAB+lists+possible+command+completions.+Anywhere+else+TAB+lists+possible+device%2Ffile+completions%5D+%20sh%3Agru)

That link is great  :popcorn:

---

### Post by pricetech on 2009-12-11
Attitude does mean a lot.  I find folks here to be quite patient when someone blows off steam, but I rarely see those who blow off steam calming down and accepting the help they are offered, which makes me wonder why.

Give us all a lot more information and someone here will help.  Otherwise mark the thread as solved so it can die.

---

### Post by Asguard on 2009-12-12
> **presence1960 said:**
> Is [this]("https://help.ubuntu.com/community/Wubi") what you did to install Ubuntu? If yes then you used wubi, which is not the same as a full, dedicated Ubuntu install to a partition on a hard disk. As such it has it's quirks and disadvantages.

Also if you want some help on here I suggest you tame your attitude. All of us on here are not paid support. We do what we do because we like to do it. We do it on our own free time, time that could be spent doing other things instead of helping someone anonymously in here for no compensation other than maybe thanks if someone remembers to say so.

Sometimes we must be patient as the person(s) who know the answer might not log in for minutes, hours or even days. 

In other words don't trash the surgeon who is going to operate on you prior to the surgery!


Hi Presence as you can see I am not having a go at anyone its the company that does ubuntu. Let's face it who was to know if you install ubuntu you install wubi.

This is such bad management on their behalf its so annoying. Anyway sorry if you thought that.

---

### Post by Asguard on 2009-12-12
> **presence1960 said:**
> That link is great  :popcorn:
That link is not great its a waste of time dont know why you put this on as all it does is carry on putting the same in and not going to any page. If your trying to be funny yes it was but back to the point I will try the wubi.

---

### Post by MelDJ on 2009-12-12
> **Asguard said:**
> Hi Presence as you can see I am not having a go at anyone its the company that does ubuntu. Let's face it who was to know if you install ubuntu you install wubi.

This is such bad management on their behalf its so annoying. Anyway sorry if you thought that.

it is so simple to know. wubi is the windows based ubuntu installer. hence it runs in windows. when you installed, you either did it through booting into the cd, or wubi in windows. 
i don't mean to be rude, but it is very simple.
a simple way to check is by going to programmes in windows' control panel and see whether ubuntu is there. because through wubi, ubuntu is installed as a program in windows

---

### Post by Asguard on 2009-12-12
> **freeburn said:**
> i'm quiet surprised with the attitude of yours. it may be frustrating but why you are attacking people who wants to help?

and what makes you think no one heard of Wubi?

i think first you should provide the information about how did you installed the OS.

did u you restart the machine and boot from the live disc or just installed from your xp?



Ok I think you are also mixed up as I said I have never heard of Wubi so please stop attacking me as I was not attacking anyone other than the company that does ubuntu. So I apologise for misleading anyone and will be more positive.

---

### Post by Asguard on 2009-12-12
I put the disc in whilst XP was on yes. I then got the cd to put ubuntu on the other drive so is this where my problem lies? thanks for your help.

---

### Post by MelDJ on 2009-12-12
> **Asguard said:**
>  and will be more positive.

thats the spirit ;)
since you put in while windows was on, and installed it while xp was running, this is a wubi install.

---

### Post by darkod on 2009-12-12
> **Asguard said:**
> Hi well I havent a clue about wubi never even heard of it. It was Ubuntu I downloaded and states ubuntu when it used to start up.

They do both stae NTFS though. Has anyone else out there heard of this so called wubi I assume its yet another linux  os then. Beginning to think its not worth the hassle and stick with microsoft.

Will try it though. But I def downloaded ubuntu so do not understand why you think its the other.

If all your partitions are NTFS then you have wubi. Ubuntu doesn't work on NTFS. I told you that right away in my post #4. Also in that post are four simple commands to make it work again.
You got into all this argument but you never said if you tried those commands or not. Are you here to argue or sort your problem?
You had your help immediately, it's up to you to execute the commands.

---

### Post by Asguard on 2009-12-12
> **MelDJ said:**
> thats the spirit ;)
since you put in while windows was on, and installed it while xp was running, this is a wubi install.


Hi everyone so to be realistic should I reinstall. If so How do I from the disc without using WUBI?

I think I would rather do this and start again. Is the disc still able to do this and should I disconnect the drive with XP on for me to reinstall on the other drive.

Or do I have to download a different Ubuntu sorry but I am now confused with the whole thing as who would think tht if you put Ubuntu disc in it would be something else. Please any advice on reinstall will be grateful thankyou for your help.

---

### Post by darkod on 2009-12-12
deleted

---

### Post by issih on 2009-12-12
To clarify this.

Windows uses a file system called "ntfs". A file system is how it configures the raw hard drive (one with nothing on it at all just the hardware). Windows itself and all of its programs are then installed onto this file system.

Linux (including ubuntu) normally doesn't use the ntfs file system (as it is proprietary and owned by microsoft). Linux can be installed onto a hard drive formatted using a variety of file systems, the most common being "ext2" "ext3" and recently "ext4".

A classic dual boot setup therefore has the harddrive partitioned (i.e. logically if not physically split into two parts) with one partition being formatted as ntfs and one as ext23 or 4. The appropriate operating systems are then installed, one on each partition.

Wubi is an attempt to simplify this for new users who want to try linux out, without committing so fully to it that they repartition their hard drive.

Wubi effectively creates a giant "file" (don't actually know if its one or more - I assume one) on your ntfs formatted hard drive, and then within the space that file occupies on the hard drive creates a virtual partition, which it formats appropriately for linux, and installs the linux distribution inside this "file".

Consequently with wubi you install from within windows and can remove the installation from the windows add/remove utility, because the whole system lives within the windows file system.

This system, whilst helpful for new users, does present extra levels of complexity, and therefore can cause unique problems.

Finally, we come to the issue of boot loaders.
A boot loader is a very small bit of low level software, that sits in a special location on a hard drive. This little bit of software is what is triggered when a computer boots from that hard drive, because the boot loader is always where the computer expects to find it.

Windows has its own boot loader, and so does linux (actually like everything in linux there are several) the one ubuntu uses is called grub. In a normal multiple partition installation grub would be installed into the master boot record (the special location) and from there would give you a choice of which OS to boot.

With wubi, because the aim it to leave windows as untouched as possible, windows own bootloader is left in place, and is modified to offer the chance to load ubuntu from the special file in the system. Once you select to load ubuntu, the windows boot loader passes the work onto a version of grub to finish loading the OS.

So...you are not getting help because:

1) You are using a non standard setup that not many users here actually have.
2) You are behaving badly...I understand the frustration, but people get very pissed off with people feeling entitled to help. If people can help, they usually will, but if you have an obscure bug, particularly in a non standard install then you will need to be a bit more proactive in finding the solution. Its also unwise to attack ubuntu if you actually want help, because people here generally quite like it.
3) You do not know enough about your system to make it easy to help. The fact that you didn't know about any of the above is not a crime at all, but it makes fixing things (especially remotely) very tricky, because we need to work out what is actually wrong before we have any chance of finding a solution.

I suggest you search for problems with wubi installs and then make a thread in that forum explaining your actual problem in as much detail as possible...that will give you the best chance of a fix.

Hope that helps

P.S.  did a spot of searching..[http://ubuntuforums.org/showthread.php?t=1310820&highlight=wubi+grub&page=3](http://ubuntuforums.org/showthread.php?t=1310820&highlight=wubi+grub&page=3)
There are a few attempts at a fix in there...whether they will work or not I can't say..

---

### Post by darkod on 2009-12-12
deleted

---

### Post by Asguard on 2009-12-12
> **darkod said:**
> If all your partitions are NTFS then you have wubi. Ubuntu doesn't work on NTFS. I told you that right away in my post #4. Also in that post are four simple commands to make it work again.
You got into all this argument but you never said if you tried those commands or not. Are you here to argue or sort your problem?
You had your help immediately, it's up to you to execute the commands.

I answered your question by answering someone else so its not me being rude now its you. 

I did not do the command quotes as it was stated it would be best to reinstall as ubuntu not wubi. So I am trying to see how to do this so please if you read the others I am trying and I have already apologised soits your turn to try thanks anyway

---

### Post by Asguard on 2009-12-12
> **darkod said:**
> First go into windows in add/remove programs and remove the "ubuntu" entry. That will delete the ubuntu from the bootloader and delete the folder for ubuntu, creating free space.
After that you need to plan where you want it installed and how much space to dedicate to it. Since all your drives are taken by NTFS partitions you will have to shrink one and create unallocated space. Where and how much is up to you. You would need to dedicate at least 25GB for ubuntu in order to function properly.
After you have made this decisions, you have two option. Use windows Disk Management to do the shrinking (which will probably be easier for you), or boot with the ubuntu cd, select Try Ubuntu option, and use Gparted to do it. Note that you might need to defragment before shrinking.

After that boot windows few times to let it finish disk checks on the shrinked volume.
Then boot with the ubuntu cd, select Install Ubuntu, and in step 4 of the installer let it Use Largest Available Free space option. It will use the unallocated space you created. Note the name of the drive (device), it will either be /dev/sda or more likely /dev/sdb. In the last step 7, before clicking Install, click on Advanced and make sure the bootloader (grub2) is installed on the same device.
That's it.

PS. Windows Disk Management can shrink only in Vista and 7. If using XP you have to use Gparted or third party software.

Hi yes I found that in the add remove.

My question is as before on a reply how do I put ubuntu on the other drive? Its not partitioned on my xp drive but on a new drive which it is already on. XP and Ubuntu are currently on seperate drives not on partitions on the same drive. 

I must of not explained properly sorry. Thanks

---

### Post by Asguard on 2009-12-12
Hi darkrod will try this later toay thanks for your help. It's difficult as more than one option between everyone so if ubuntu cannot go on ntfs I assume it alters the drive when installing. It seemed to work fine for a few weeks until that update so I am unsure as to what I set the drive to when installing. But will give your  explanation above a go so thanks.

---

### Post by Bartender on 2009-12-12
> **Asguard said:**
> My question is as before on a reply how do I put ubuntu on the other drive? Its not partitioned on my xp drive but on a new drive which it is already on. XP and Ubuntu are currently on separate drives not on partitions on the same drive.

You got off to a bad start, people here helped you out anyway, you're still insisting on an "answer" when none can be given because it's clear you know almost NOTHING about how to install and furthermore haven't spent any effort learning.

There are probably more web sites, YouTube videos, and forum threads on dual-booting than just about any other Linux-related topic.

Hell, I've probably written 300 posts on various aspects of dual-booting myself, and I'm on freakin' dial-up.

On top of that, your questions are unclear.  Above, you ask how to install to a separate drive, then you say you've already installed to a separate drive.  So what's the problem?

EDIT: The title of your thread is just about perfect if your goal is to incite the people you're asking for help.

---

### Post by MelDJ on 2009-12-12
> **Asguard said:**
> Hi everyone so to be realistic should I reinstall. If so How do I from the disc without using WUBI?

I think I would rather do this and start again. Is the disc still able to do this and should I disconnect the drive with XP on for me to reinstall on the other drive.

Or do I have to download a different Ubuntu sorry but I am now confused with the whole thing as who would think tht if you put Ubuntu disc in it would be something else. Please any advice on reinstall will be grateful thankyou for your help.

to answer your question [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
i agree with the above poster that the title is inappropriate. but it gets everyone's attention
but the OP has since apologized for his/her behaviour in his/her earlier post, so i think we should all move on to assisting him/her

---

### Post by Asguard on 2009-12-12
Hi Bartender thank you for your reply But I am fairly good at doing things on Microsoft even repairing friends when they have problems. The problem here was I did not know I was not using Ubuntu until it was kindly explained to me that because XP was running I am using WUBI.

If you read my first post you may then understand the problem I had it was aftewr a few weeks of using this OS that the problem occured. Until then I was thinking how much faster etc it is to XP. Problem was after a few weeks when I got  an update anyway I need not go on as we are now getting sorted thanks to the kind people on here. I may of started off wrong but I was trying to get attention as I had no luck on a previous posting but I have overstepped the mark and apologies.

 Once I have done the things requested  I will post back  and at least this posting has probably helped many newbies to Linux as so much helphas been forth coming so for that I think this has been worth it to help others.

All the best to you all.

---

### Post by Asguard on 2009-12-12
I have checked the cd I burnt to and it is not what I downloaded or was lead to believe. It is indeed Wubi and not Ubuntu as one or two thought. I tried to download another copy and again it says Wubi so it seems you cannot download Ubuntu.

It also only allows you to download 32bit although it states to choose 64 or 32bit. So to this I am at the moment going to close this post as it seems you cannot get Ubuntu. Unless anyone can shed some light on how to get Ubuntu and not Wubi

---

### Post by Shazaam on 2009-12-12
Asguard...
When you go here-
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and choose 64-bit (lower right after clicking "Alternative download options") the "Begin Download" box does change to 64bit Ubuntu.

---

### Post by Asguard on 2009-12-12
Thank you done that and yet again it says its Ubuntu but it downloads a 64bit Wubi. So the same I have already. To those who say I should try the full Ubuntu then where do I get it no wonder I have been so confused.

Otherwise all I can do is try this version Wubi but it seems no point. If you can help thanks.

---

### Post by Bartender on 2009-12-12
Maybe this will help.
I go to Google.  I type in "download ubuntu".
The very first hit looks like the ubuntu website, so I click on it.

Attached is a screenshot where I, being the incredibly helpful guy that I am, took the time to point out three different downloads.  The standard Ubuntu LiveCD, wubi download, and the alt-install download.

I don't know if the website looks different in the UK but I'm guessing not.

Notice that the link to torrents is right below the alt-install link, where I believe you can still get the different downloads but via torrent.

EDIT:  Notice also to the right of the standard Ubuntu download you can choose 32 or 64 bit.

---

### Post by lisati on 2009-12-12
> **Asguard said:**
> Thank you done that and yet again it says its Ubuntu but it downloads a 64bit Wubi. So the same I have already. To those who say I should try the full Ubuntu then where do I get it no wonder I have been so confused.

Otherwise all I can do is try this version Wubi but it seems no point. If you can help thanks.

I think I see a clue here. The disks that you can download [here]("http://www.ubuntu.com/getubuntu") are designed in such a way that if you have Windows running when you put them in your machine, the Wubi process starts. If you have the CD in your computer when you restart, you can set your computer to start a "Live session" from the CD. What this means is that instead of starting Windows from your computer's hard disk, it starts a copy of Ubuntu from the CD. The standard "Desktop" CDs (both 32-bit and 64-bit) have an option to try Ubuntu without installing anything.

---

### Post by Asguard on 2009-12-12
Hi this is exactly my point I have tried this and it downloads wubi not ubuntu. The google search just gives the same I know that. As for pointing it out that was already done by a previous comment but thanks for trying.

I do not understand why if it states ubuntu why does it download wubi. Linux is doing itself no favours. You can see my frustration surely someone out there must have a copy of ubuntu they have downloaded and it really is ubuntu. If so where do I get it from as I cannot get it from the obvious source the home site. I am going to try the 32bit and see if this is ubuntu will report back when done. thanks

---

### Post by Bartender on 2009-12-12
It's quicker for me to just ask than search back thru your thread.  I think lisati is onto something.  The screenshot I posted is where I go to get a download.  I've never ever had any problems with wubi trying to take over.

Are you BOOTING from the CD?

Or are you starting up Windows, then tossing the disc in the tray?

You have to boot the PC from the optical drive.  If Windows is up, you cannot proceed with the standard Ubuntu installation.

---

### Post by Asguard on 2009-12-12
Hi lisati/bartender yea I guessed that to but have not got that to work either but will give it another go. It is so strange. On the cd the image burnt only show Wubi not ubuntu. 

It does seem that they are not allowing us to download ubuntu for use on its own but only Wubi to use with windows.  When I originally downloaded weeks ago I thought I was getting Ubuntu hence my confusion with all the guys trying to help me.Then I decided to look at the disc to see what was on it and then I realised it only downloads the Wubi version all the time. How annoying.

Have you looked at the cd you have bartender does it show Wubi.exe only like mine?

Will try the cd in the tray only tho again but didnt work last time but maybe I had windows running silly me. Let you know later thanks again.

---

### Post by Shazaam on 2009-12-12
Asguard...
Do you know how to enter your pc' bios setup screen? There are a bunch of keys you can click when the pc is booting. Usually the instructions will print out near the bottom of the screen. Here are a few that you can try...
1. F12
2. F11
3. The "Delete" key
If you do get to the setup/disk boot order screen choose "cdrom" to be first in the boot sequence. Once you have that set up insert the Ubuntu livecd in the tray. The livecd should now boot.
Before you install Ubuntu (especially since you also have Windows on your pc) PLEASE read as much information as you can about dual-booting AND partitioning hard drives. One mistake with that and you can overwrite Windows.

---

### Post by lisati on 2009-12-12
> **Asguard said:**
> Hi lisati/bartender yea I guessed that to but have not got that to work either but will give it another go. It is so strange. On the cd the image burnt only show Wubi not ubuntu. 

It does seem that they are not allowing us to download ubuntu for use on its own but only Wubi to use with windows.  When I originally downloaded weeks ago I thought I was getting Ubuntu hence my confusion with all the guys trying to help me.Then I decided to look at the disc to see what was on it and then I realised it only downloads the Wubi version all the time. How annoying.

**Have you looked at the cd you have bartender does it show Wubi.exe only like mine?**

Will try the cd in the tray only tho again but didnt work last time but maybe I had windows running silly me. Let you know later thanks again.
Did you get your CD from here? [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
If so, there will be more than just Wubi -  there should be other files and folders as well. As Shazaam says, you need to restart your computer, and change your computer's settings so it can "boot" (read) from the CD-ROM first.

---

### Post by Asguard on 2009-12-12
Hi Shazaam and lisati, Bartender,

Yes i know how to boot from cd thankyou mines f11 . Right this is what I have done I think my 64bit cd was corrupt as would not work so I downloaded the 32bit burnt the image to disc and have now put Ubuntu on my other hard drive by itself. Its working great have installed and ready for use.

I realise its not dual boot now and will have to change the way it boots by pressing f11 on mine between xp and linux but no big deal.

I ddi try what you said booting from the cd and yes it worked for the 32bit but not my 64bit cd so thrown that now lol.

I thought this would be the best way to give it its own hard drive as I had one just sitting there. Thank you so much for your help I got there in the end all be it by completely redoing ubuntu this way though I can start a fresh.

Just one thing though everytime I boot up in to xp it still ask me if I want xp or Ubuntu but of course it can not find ubuntu so is there a way to make the pc boot straight in to xp by removing the ubuntu choise. I have deleted the program by add removebut this still remains. Would appreciate help on this if possible thankyou.

---

### Post by presence1960 on 2009-12-12
> **Asguard said:**
> Thank you done that and yet again it says its Ubuntu but it downloads a 64bit Wubi. So the same I have already. To those who say I should try the full Ubuntu then where do I get it no wonder I have been so confused.

Otherwise all I can do is try this version Wubi but it seems no point. If you can help thanks.

DUDE, wubi is on every Ubuntu CD. You install wubi through windows. If you want a full dedicated installation of Ubuntu to a partition you must boot the CD. That is how you choose between a wubi install and a real Ubuntu install to a partition.

**Again wubi is on every Ubuntu live CD. You use wubi from inside of windows. You do not want that. So what you do is insert the CD and restart your machine . Make sure the CD is set to boot before your hard disk in BIOS. The installation that you want will begin.**

---

### Post by presence1960 on 2009-12-12
[QUOTE=Asguard;8487558]Hi this is exactly my point I have tried this and it downloads wubi not ubuntu. The google search just gives the same I know that. As for pointing it out that was already done by a previous comment but thanks for trying.

I do not understand why if it states ubuntu why does it download wubi. **_Linux is doing itself no favours. You can see my frustration surely someone out there must have a copy of ubuntu they have downloaded and it really is ubuntu. If so where do I get it from as I cannot get it from the obvious source the home site. I am going to try the 32bit and see if this is ubuntu will report back when done. thanks[_**/QUOTE]

Stop blaming Linux. We all want to help you. It is obvious that your computer knowledge is a little lax. That can be increased with some effort on your part as someone suggested earlier! But if you follow directions you will get Ubuntu installed. Again wubi is included on the Live CD. It is there in case you want to install wubi from within windows. If you don't want wubi, which you say you don't- then stop calling the Live CD wubi because it also contains wubi. Boot the Live CD man, keep it simple!

---

### Post by presence1960 on 2009-12-12
Dude, let's put this to rest once and for all. here is a screenshot of my karmic 9.10 64 bit Live USB. Note that it has wubi.exe in it. ***_Make no mistake, this is an Ubuntu Live CD (on a USB disk)! If you set the CD drive in BIOS to boot first then boot with the ubuntu CD in the drive your Ubuntu install will begin as if by magic._***

If you can't do this then I am afraid none of us can help you!

---

### Post by Bartender on 2009-12-13
Good morning, presence!

Thanks for helping out.  I've never messed with wubi at all.  Your posts got me to toss an Ubuntu 9.10 CD in the tray while Windows was up.

Sure enough, there's a wubi file, found when I clicked on D drive (in attachment).  When I clicked on that, I got the second window that clearly states you can try Ubuntu, or install Ubuntu, by restarting the PC with the CD in the tray.  The directions don't explain that your optical drive has to be first in boot priority, but that's a given.

I'd never seen this window before, but it makes perfect sense to have it there.  Now I understand what Asguard was saying about a wubi.exe file.

To the OP, it sounds a little bit like crazy talk to suggest that the people who administer the Ubuntu download websites are plotting to hide the Ubuntu download from you.  We've clearly pointed out the mistakes you're making.  If each step of the process is going to take four or five pages of discussion this is going to be a real grind.

---

### Post by presence1960 on 2009-12-13
I took my screenshot from Ubuntu. I already knew wubi is on every Live CD. But if you boot from the CD you will never know it exists unless you later browse the CD. The OP swears he is getting wubi because that file is there. If he would just listen to everyone trying to help and boot the CD he may install Ubuntu. I say may because in my opinion his knowledge is such that he may not succeed at first. I think he needs to really read & study the install process before he attempts it. This is not to be putting him down, just that he needs to advance his knowledge about what he is attempting to do before trying to do it.

---

### Post by nobar on 2009-12-25
I read through the entire thread and several similar threads (I had the same problem, and the same frustration), and I wanted to make the following postmortem:

1) The OP is knowledgeable about Windows but has no prior experience with Linux.
2) Wubi is prominent on Ubuntu CDs but @darkod confused the OP, making him think that what he installed was not Ubuntu.
3) The OP did not make enough effort to independently discover what Wubi was (he presumably didn't even google "wubi" before posting "Has anyone else out there heard of this so called wubi I assume its yet another linux os then").
4) The OP was legitimately frustrated by the fact that his computer wouldn't boot.
5) @darkod's instructions in post #4 were probably correct (they worked for me after some trial-and-error), but despite good intentions, the post was possibly too cryptic and intimidating for a Linux newbie (especially the part about making adjustments to /dev/sda1).
6) **Ubuntu has screwed up big-time** by breaking Wubi-based installs via a normal software update and not making it a critical priority to communicate a fix to Wubi users, who are more likely to be new to Linux.

---

### Post by presence1960 on 2009-12-25
> **nobar said:**
> I read through the entire thread and several similar threads (I had the same problem, and the same frustration), and I wanted to make the following postmortem:

1) The OP is knowledgeable about Windows but has no prior experience with Linux.
2) Wubi is prominent on Ubuntu CDs but @darkod confused the OP, making him think that what he installed was not Ubuntu.
3) The OP did not make enough effort to independently discover what Wubi was (he presumably didn't even google "wubi" before posting "Has anyone else out there heard of this so called wubi I assume its yet another linux os then").
4) The OP was legitimately frustrated by the fact that his computer wouldn't boot.
***_5) @darkod's instructions in post #4 were probably correct (they worked for me after some trial-and-error), but despite good intentions, the post was possibly too cryptic and intimidating for a Linux newbie (especially the part about making adjustments to /dev/sda1)._***
6) **Ubuntu has screwed up big-time** by breaking Wubi-based installs via a normal software update and not making it a critical priority to communicate a fix to Wubi users, who are more likely to be new to Linux.

I went back to post #4. I disagree with you the instructions were not cryptic, actually so simple a caveman can do it by copy and paste each command into terminal one at a time. Unfortunately that is the way it has to be done whether you are a linux newbie or a veteran.

On a personal note I dislike wubi. It has many quirks and since it is inside windows that says it all. I discourage people from trying to use wubi as a permanent install. That has become the trend here lately. Wubi was not meant to be used as a permanent install but rather as a test drive for those who were unwilling to partition their disk(s) until they were sure they liked Ubuntu. Wubi gives them that option, but as human nature is people are lazy and transfer that trait into putting off partitioning their hard disk and having a real installation of Ubuntu. Yes I said it, IMHO wubi is not a legit Ubuntu install, it is just what it is meant to be- "a test" to see if one likes ubuntu. See here from wubi's dev: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/) Here is the relevant quote in case you don't want to read the article>  Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Linux is what it is and should not change to meet what everyone thinks it should be. Maybe some of it is "cryptic", but if someone does not like that then they should not use Linux, but rather opt for an OS more to their liking.

Now I can relate to newbies fear of terminal, for I hated terminal when I started using Linux. But I liked the OS enough to persevere and learn. Today I consider terminal one of the strengths in Linux. Unfortunately for those people scared of terminal some things can only be done "cryptically" from terminal

---

### Post by raymondh on 2009-12-25
> **presence1960 said:**
> 

On a personal note I dislike wubi. It has many quirks and since it is inside windows that says it all. I discourage people from trying to use wubi as a permanent install. That has become the trend here lately. Wubi was not meant to be used as a permanent install but rather as a test drive for those who were unwilling to partition their disk(s) until they were sure they liked Ubuntu. 

[COLOR="Red"]+1 [/COLOR]

Linux is what it is and should not change to meet what everyone thinks it should be. Maybe some of it is "cryptic", but if someone does not like that then they should not use Linux, but rather opt for an OS more to their liking.

[COLOR="Red"]+2[/COLOR]

Now I can relate to newbies fear of terminal, for I hated terminal when I started using Linux. But I liked the OS enough to persevere and learn. Today I consider terminal one of the strengths in Linux. Unfortunately for some people some things can only be done "cryptically" from terminal

[COLOR="Red"]+ 3 .... *on a side note, I can still clearly recall Merlinus' advice .... "learn to use a terminal and you can make a commodore64 run".*[/COLOR]

.

---

### Post by bcbc on 2009-12-25
whether the wubi installation method is good or not or how long you should use it is a side-issue. The fact is, wubi exists, and it works (great). And an official Ubuntu "important security update" breaks it. For me the issue is - why hasn't the update been removed or replaced with something that works for us dumb wubi users.

PS there are a lot of users who know surprisingly little about linux (or windows) - and why should they have to? The day they can run ubuntu easily is the day that ubuntu will have arrived. I showed the grub boot commands to some windows users and we all had a good laugh - I guess it's part of the fun of linux that you have to know that cr*p, but it's part of the problem too.

---

### Post by presence1960 on 2009-12-25
> **bcbc said:**
> whether the wubi installation method is good or not or how long you should use it is a side-issue. The fact is, wubi exists, and it works (great). And an official Ubuntu "important security update" breaks it. For me the issue is - why hasn't the update been removed or replaced with something that works for us dumb wubi users.

**_PS there are a lot of users who know surprisingly little about linux (or windows) - and why should they have to? The day they can run ubuntu easily is the day that ubuntu will have arrived. I showed the grub boot commands to some windows users and we all had a good laugh - I guess it's part of the fun of linux that you have to know that cr*p, but it's part of the problem too._**

1. Sorry that you feel the need to label yourself as well as others "dumb". Uninformed would be more accurate.

2. In response to the bold, underlined above I suggest reading [this]("http://linux.oneandoneis2.org/LNW.htm"). It will take a few minutes. But if read all the way through one will see that Linux is not supposed to be like windows for those who came to Linux from windows. If you want a better version of windows there is windows 7 which is a vast improvement to the windows OS. I ran the Windows 7 RC for months- not because I like Windows but instead because I need to stay abreast of Windows because most of my clients boxes that I work on run Windows. If you don't want to go through a learning curve and want something that you are familiar with I suggest you stick with Windows. Just so you know there is a method to use the command line in windows- but most users don't even know it exists or as you said would scoff at it. That is your loss as the command line is the most direct, powerful way to accomplish tasks on an OS.

Linux's strengths lie in the fact that it is not like windows. To make it more like windows for the sake of those unwilling to learn Linux's ways would make Linux- well another Windows. Linux users will not allow that. I as well as many others use linux because we choose to do so and many of us use it specifically because we do not prefer the windows OS and linux fits the bill because it is unlike windows.

There are many flavors of ice cream for these very reasons. if you don't like a particular flavor you are not going to convince the manufacturer to alter the recipe. Your choice is simple, stick with the flavor you like or invent your own. Same goes for OSs.

P.S. I see you have one post (this one) to your credit. Did you join up just to complain about Linux or are you trying to learn linux? If it is the former that is OK because people who do that do not affect this community in a negative way, they actually help us be stronger in our resolve. If you don't like Linux then don't use it. If you have problems and want to learn how to fix them and learn about linux then post a question rather than bad mouthing an OS that you have the freedom to choose to not use if you don't like it. Here is a link for you, maybe you can join this community: [http://linuxhaters.blogspot.com/](http://linuxhaters.blogspot.com/)

---

### Post by phillw on 2009-12-25
> **presence1960 said:**
> 1. Sorry that you feel the need to label yourself as well as others "dumb". Uninformed would be more accurate.

2. In response to the bold, underlined above I suggest reading [this]("http://linux.oneandoneis2.org/LNW.htm"). It will take a few minutes. But if read all the way through one will see that Linux is not supposed to be like windows for those who came to Linux from windows. If you want a better version of windows there is windows 7 which is a vast improvement to the windows OS. I ran the Windows 7 RC for months- not because I like Windows but instead because I need to stay abreast of Windows because most of my clients boxes that I work on run Windows. If you don't want to go through a learning curve and want something that you are familiar with I suggest you stick with Windows.

Linux's strengths lie in the fact that it is not like windows. To make it more like windows for the sake of those unwilling to learn Linux's ways would make Linux- well another Windows. Linux users will not allow that. I as well as many others use linux because we choose to do so and many of us use it specifically because we do not prefer the windows OS and linux fits the bill because it is unlike windows.

There are many flavors of ice cream for these very reasons. if you don't like a particular flavor you are not going to convince the manufacturer to alter the recipe. Your choice is simple, stick with the flavor you like or invent your own. Same goes for OSs.

As always with your posts, a considered reply - you should be nominated for **[B]canonization**[/B] but you're not dead yet - and, hopefully not for some time to come.
I can feel empathy for windows users 1st dipping their toe into Ubuntu (or any Linux) - It is just, well, different. For some it is a God send, to allow them freedom and to learn, for others it is too scary from having "all powerful, all knowing" OS tell them what to do. For those at the beginning stage, try reading [http://blogs.techrepublic.com.com/10things/?p=406](http://blogs.techrepublic.com.com/10things/?p=406)  amongst other ones. With freedom comes responsibiity. 

Myself an u.b.u.n.t.u. have crossed horns about Wubi, it is very good for a test run, but, with the modern computers that can boot from USB - I think it is showing its age - especially as the updates have been knocking it out, which is, as pointed out - ubuntu shooting itself in the foot.

Burn a USB stick, with persistence enabled and you will have a 'slowish' ubuntu install, but one that does remember what you've been doing & will take updates. You can do that from the LiveCD - Or, if you're too lazy head over here and buy one, on a cute 4GB ubuntu logo'd memory stick -- I love mine :-)

[http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)

Phill.

---

### Post by bcbc on 2009-12-26
I don't think canonization is a bad idea. Unimaginative zealots often end up that way.

---

### Post by presence1960 on 2009-12-26
> **bcbc said:**
> I don't think canonization is a bad idea. Unimaginative zealots often end up that way.

I am unimaginative? Everyone has an opinion and you are entitled to your opinion. But I ask "What do you call you and your friends who got a good laugh out of the terminal commands"? Now that is unimaginative!

---

### Post by nobar on 2009-12-26
> **presence1960 said:**
> I disagree with you the instructions were not cryptic, actually so simple a caveman can do it by copy and paste each command into terminal one at a time.

If you know how to do this by copy-and-paste, please share more details.  I believe that working with the "sh:grub" prompt requires you to actually type in the full command lines without error.  I'm guessing that you didn't mean copy-and-paste literally, but I want to make sure, because copy-and-paste would be helpful.

Secondly, even for an experienced Linux user, this is not easy because the /dev/sda? entry does not appear in the file system and this leads one to wonder if they are on the right track.  Furthermore, if you make any mistakes, it fails without any helpful feedback.

> **presence1960 said:**
> 
IMHO wubi is not a legit Ubuntu install, it is just what it is meant to be- "a test" to see if one likes ubuntu.

The Ubuntu documentation and the Ubuntu install process do not agree with your opinion on this.  From [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide): "What is Wubi? Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way."  The only downside of Wubi indicated on that page is a greater possibility of file system corruption if you do a "hard reboot".  The install dialog also indicates that hibernation is not supported.

I think it is misleading to say the Wubi is "inside Windows".  It is really running Linux -- Windows is not running in the background.  It is accurate to say that the Wubi file system is inside the Windows file system, but for most purposes, that is not a major drawback -- it's just another file system that Linux supports (one of many).

> **presence1960 said:**
> Linux is what it is and should not change to meet what everyone thinks it should be. Maybe some of it is "cryptic", but if someone does not like that then they should not use Linux, but rather opt for an OS more to their liking.

In this case, the only reason Linux is cryptic is because there was a bug in a software update which broke the boot sequence of an officially supported release.  It shouldn't be too much for people to expect Ubuntu and the Ubuntu community to bend over backwards to resolve an issue of this magnitude whenever it occurs.

---

### Post by presence1960 on 2009-12-26
> **nobar said:**
> > If you know how to do this by copy-and-paste, please share more details.  I believe that working with the "sh:grub" prompt requires you to actually type in the full command lines without error.  I'm guessing that you didn't mean copy-and-paste literally, but I want to make sure, because copy-and-paste would be helpful.

I stand corrected there is no way to copy/paste. Be it as it may isn't it a shame that one has to type in commands correctly for them to work? :rolleyes:

[QUOTE]Secondly, even for an experienced Linux user, this is not easy because the /dev/sda? entry does not appear in the file system and this leads one to wonder if they are on the right track.  Secondly, if you make any mistakes, it fails without any helpful feedback.

**_Again this is linux not windows_**. If not sure one can boot from the live CD and see which device windows is installed to by running sudo fdisk -l. If one wants an exact answer they can run the boot info script from the live cd.



> The Ubuntu documentation and the Ubuntu install process do not agree with your opinion on this.  From [https://wiki.ubuntu.com/WubiGuide:](https://wiki.ubuntu.com/WubiGuide:) "What is Wubi? Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way."  The only downside of Wubi indicated on that page is a greater possibility of file system corruption if you do a "hard reboot".  The install dialog also indicates that hibernation is not supported.

Read the first sentence here from the community documentation of wubi: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
in case you don't want to look here it is- note the bold & underlined: The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user ***_try_*** Ubuntu without risking any data loss due to disk formatting or partitioning.

> I think it is misleading to say the Wubi is "inside Windows".  It is really running Linux -- Windows is not running in the background.  It is accurate to say that the Wubi file system is inside the Windows file system, but for most purposes, that is not a major drawback -- it's just another file system that Linux supports (one of many).

It is not misleading as the wubi file is inside of windows- like it or not.



> In this case, the only reason Linux is cryptic is because there was a bug in a software update which broke the boot sequence of an officially supported release.  It shouldn't be too much for people to expect Ubuntu and the Ubuntu community to bend over backwards to resolve an issue of this magnitude whenever it occurs.[/QUOTE]

I believe Darko did just that (bend over backwards). He does not run wubi but spent his own free time researching what the answer is until a more permanent fix comes in, if it ever does. I did some searching myself and Darko is indeed on the right path as others have solved the issue described here about wubi with just the solution you guys/gals are complaining about. [B][U]Some people complain with a loaf of bread under their arms.
[/U][/B] You have the solution now use it or find your own way to fix it.

As far as expecting Ubuntu & this community to bend over backwards- you could not be farther from reality. We are not paid support. Most of us do this in our free time because we like linux and want to help those who want to use it but are having problems. But you, I or anyone else has no right to demand anything from anyone in the community or even from Ubuntu. If you want the right to jaw at those helping you like you could in the windows world where you paid for software I recommend you purchase Canonical's paid support that they offer. Yes then you have paid and earned the right to complain to those trying to help you. But in here that attitude will stop most, if not all from attempting to offer even the slightest help. Don't believe me, go back and look at how much real help you have received since that post complaining about the help received! My advice is be nice to those trying to help. The linux is hard and linux shouldn't be like this rants turn most off. We don't and won't take that attitude. If there is a real problem and you feel so strongly about it the proper forum is to file a bug report.

---

### Post by nobar on 2009-12-27
It seems we disagree on just about everything -- with one exception: people who are helping other people deserve appreciation. :)  In particular, I would like to thank @darkod who provided the instructions which got my machine booting again -- thanks @darkod!  (Note: I'm not the original poster -- I'm just a lurker.)

Also, thanks for the suggestion regarding bug reporting.  It seemed like this problem should have already been well known and well reported (there are a BUNCH of web hits about this), but I'll see if I can figure out something about the bug report situation over the next week or so.

P.S. The other thing that I think we agree on is that Ubuntu is awesome!

---

### Post by presence1960 on 2009-12-27
> **nobar said:**
> It seems we disagree on just about everything -- with one exception: people who are helping other people deserve appreciation. :)  In particular, I would like to thank @darkod who provided the instructions which got my machine booting again -- thanks @darkod!  (Note: I'm not the original poster -- I'm just a lurker.)

**_Also, thanks for the suggestion regarding bug reporting.  It seemed like this problem should have already been well known and well reported (there are a BUNCH of web hits about this), but I'll see if I can figure out something about the bug report situation over the next week or so_**.

P.S. The other thing that I think we agree on is that Ubuntu is awesome!

A lot of us understand frustration and don't mind people letting off some steam, But the moment one starts the Linux isn't like windows or Linux shouldn't be like this or Linux is too hard rant comes down the pike  most will not accept that as legit because Linux is what it is and we each have the freedom to choose which OS we want to use. Hint: if you don't like windows do not use it, if you don't like Linux do not use it. It really is that simple.

BTW glad you got it working. Enjoy Ubuntu. You may want to consider booting off the Live CD/USB and making a clean install on a dedicated partition(s). You will probably have less problems and support for problems are easier to come by than support for wubi.

In reference to bold & underlined above: There problem is in the fact that most of those who experience problems never take the time to research & file a bug report. Most just whimper and moan in here, but never take any action(s) that will get the ball rolling towards a fix. If the "bug" is not reported it most likely will remain unknown & therefore unresolved. Again this goes to what using open source software is about. We did not pay for it or support. Open source is community driven. If the community does not participate in the "bug reporting" or improvement process then the status quo remains.

---

### Post by linuxonbute on 2010-02-20
Asgard
I do not know if you have got this working as you say you want but I suggest if you have not that you try the following:

1/ Shutdown your computer.
2/ Unplug your windows disc.
3/ Reboot your computer with the cd in the drive.

If it boots the live ubuntu fine you can now see that the live cd runs and you should see an "Install" option.

If not then you have got something wrong.

TELL US WHAT HAPPENS ( Please note capitals normally means we are shouting ) but I am just trying to tell you to do what we say and then TELL US WHAT HAPPENS )

We can then work from that feeding you the things you need to do bit by bit.

---

