---
title: "How do you easily install Ubuntu for dual-boot with Windows?"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by zcox on 2005-02-20
This seems to be an **extremely** common question I see in this forum and all over: if you already have a pc running Windows, how do you install Linux on that pc so you can boot to either Windows or Linux?  

Given the high rate of occurence of this question, I would say there has not been a satisfactory answer.  I think the Linux community could convert a lot of Windows users if it was exceptionally easy to put Linux on an existing Windows box.  Ubuntu is a great distro but it is still too difficult for newbies to get a dual-boot Linux/Windows system up-and-running.

So here's the challenge: either create simple easy documentation to allow a newbie to install Ubuntu on an existing Windows pc so the user can select which to boot without having to purchase commercial software (ie Partition Magic), or add functionality to the Ubuntu installer to automatically detect an existing Windows install and add Ubuntu to the pc in a dual-boot configuration.

Anyone up for the challenge?  Let's answer this question once and for all!

---

### Post by p!=f on 2005-02-20
Welcome, 

all you need to install Ubuntu or any other Linux distribution next to your Windows installation is a free unallocated (no filesystem exists) space on a hard drive (1,8GB at min). As soon as you satisfy this requirement you just start the installer and follow the self-explaining instructions and after it's done, a boot line for Windows will be added to GRUB (default boot loader in Ubuntu) so you just select if you want to boot Windows or your new fresh Linux distro.

And by the way, searching these forums for dual boot might reveal sufficient informations to succeed. ;)
Feel free to ask in case of troubles and good times with Ubuntu.

---

### Post by firehound on 2005-02-20
I think you hit it on the head.  I tried yesturday for 4 hours and had to reformat my system twice without success.  I take full respondsbilty for it as I am a newbie with linux.  I am quite comfortable with windows , installs, updates, adding hardware, partitioning, formatting and am always working on other people's systems who have problems.  That being said I didn't find the install easy.  I partioned my harddrive (200meg) and had 25 set apart for ubuntu.  Could not get it to load to that so i choose C: and thought it might partition it separately.  Not a chance, guess what a reformat.  Anyway I have tried researching and going thru the install procedure and still am not sure if I can do it.  I am going to try again just trying to find some install tips.  When I tried to choose the partition a wanted it said it couldn't find the root of something or else (sorry for the vage discription I didn't write it down and I'm at work now.  I hope to have better luck next try.

---

### Post by zcox on 2005-02-20
[QUOTE=p!=f]Welcome, 

all you need to install Ubuntu or any other Linux distribution next to your Windows installation is a free unallocated (no filesystem exists) space on a hard drive (1,8GB at min). As soon as you satisfy this requirement you just start the installer and follow the self-explaining instructions and after it's done, a boot line for Windows will be added to GRUB (default boot loader in Ubuntu) so you just select if you want to boot Windows or your new fresh Linux distro.

And by the way, searching these forums for dual boot might reveal sufficient informations to succeed. ;)
Feel free to ask in case of troubles and good times with Ubuntu.[/QUOTE]

I think the major stumbling block for newbies is how to create "a free unallocated space on a hard drive."  Windows installs are usually one partition on one hard drive and that partition uses 100% of the drive.  How do you easily create a new partition without using commercial software (ie Partition Magic)?

Most newbies don't even understand partitions, let alone know how to create new ones.  It would be awesome to have step-by-step instructions to create a new partition for linux, or have the Ubuntu installer automatically do it for you.  Ubuntu makes every other part of the installation so incredibly easy, this would make it even better!

---

### Post by machiner on 2005-02-20
the quick and dirty: using one particular flawless method.

install your shiny new harddrive. get the jumpers right.

boot to a "rescue" disc -- ( [http://www.sysresccd.org/](http://www.sysresccd.org/) )

type menu
choose rescue disc

let it voot you to a prompt.  Glorious.

type: run_qtparted.

make your partitions....the 1st is NTFS - 'cos you're going to install your winblows after  this.

hda1     ntfs     2gb    (set ACTIVE)
hda2     ext3     5gb     /
hda3     ext3      25gb   /home
hda4     swap  (if this is even necessary - got 1gb - you don't need a swap)

(sizes are arbitrary - pick your own sizes - just give win 2 gb)

cool -- there's your drive.

Now --  reboot, pop in your winxp disk -- get comfortable - install.

when it's in -- great -- go turn all those damned services off (server...anything remote...you know the drill)

reboot -- to your shiny new Ubuntu disc....when the partition screen comes up - you've got them -- just assign them now -- and leave hda1 alone - duh!

finish that - when you are asked if you would like Ubuntu to install Grub -- let it.

Ya - it's a GOOD THING. Just let it.....finish your ubuntu system.

Great.

Reboot - hit escape when ytou see Grub -- looky there - pick Ubuntu or windows to boot to.

You did it.  SPectacular....you ROCK!!!~


Just remember this easy formula:

if it's a windows disc - you've got a new frisbee. Ahem! -- windows goes on first - and it likes to be on the first partition of IDE1.

---

### Post by zcox on 2005-02-20
Those are great instructions if you can use a fresh Windows install.  What about if you have an existing Windows install of many years you don't want to/can't blow away, but also want to have Ubuntu on the same machine?

How do you easily split the single Windows partition so you have a new one to install Ubuntu to, without buying Partition Magic?

---

### Post by firehound on 2005-02-20
Machiner,
Thanks for the suggestion.  The only problem with that, is most systems like dell, compaq, gateway is that xp is already installed and if you try to reformat with a clean install it will try to recover the whole disk.  Most times the xp disk is on the harddrive in a hidden folder and if you erase that your in trouble.  Maybe trying to install linux is just a learning curve that must be overcome to become more self-suffient.

---

### Post by machiner on 2005-02-20
[QUOTE=zcox]Those are great instructions if you can use a fresh Windows install.  What about if you have an existing Windows install of many years you don't want to/can't blow away, but also want to have Ubuntu on the same machine?

How do you easily split the single Windows partition so you have a new one to install Ubuntu to, without buying Partition Magic?[/QUOTE]


Just do the same thing sans installing windows..

Don't fear partitioning.

If your box is a Dell, Gateway - or whatever...chances are you have one large partition, or your hdd bisected into 2 partitions.

This is no worry.  If you boot to a partition utility like in the above instructions you will be shown a graphical rep of your harddrive. So - say you have one large bar (qtparted will show you a horiz. rectangle depicting your hdd) accross the top, no worries. Simply click the pic - as it were, and then goto one of the menu items and choose "resize".

Shrink that giant partition.  Look - YMMV - I have never destroyed any data this way...just remember this maxim: operating in fear or panic mode will only bring trouble.

Relax.


So - after you resize that hdd, now you have some space -- create another partition. Then another  -- woohoo!! go crazy, man.

You can only have 4 primaries, but you can make 7 zillion logical partitions if you want. Go nuts.

Now nuke 'em cos if you need more than 4 on a drive, you should just get another drive.

-------------------------------------------

If you fear all this (you really shouldn't - sure, I'm pretty cryptic - but it really is easy and the developers do a damned good job making this software for you) then just burn all the stuff you want from windows and start from scratch -- see above directions.

You windows partition needs 2 gb for winxp to be happy...unless you stick the swap on another drive (which is good medicine) and also I used to like to install all my apps on that other drive as well - that's where I made my D:\ drive.

Sorry - more cryptic....

[EDIT: I had a cool-arse diagram of a hdd here but it was lost in formatting translation]


Now - you have your windows partition still intact - where it was - bootable....and you have 3 more partitions , or 2 or 34 logicals -- whatever.

reboot - pop in your shiny new Ubuntu disc -- follow above directions.

Rock On.  -- repeat after me: (looking into a mirror)

you da man.

Say it again. Feel it.  you da MAN!!!!

---

### Post by firehound on 2005-02-20
thanx machiner.

that helps.

I partitioned my harddrive (200 gig) and gave myself 25 for ubuntu.  When I tried to install to that partition it kept coming back that (and I'm sorry i didn't right this down) that there was _no root........._ and I couldn't continue on.  It would kick me back to the partition portion.  When it is loading and it gets to the partition part do I have to identifiy anything in the 25 gig space or leave it all the defaults.

Sorry if this seems repetitive, i've check the site haven't found that answer.

I got it to load the second attemp but lost my windows when i booted out of ubuntu.
My mistake I put it on the c: drive as it would go thru on that selection.
firehound

---

### Post by machiner on 2005-02-20
OK -- I feel your pain a little. I have seen a zillion gateway and dell and compaq computers bought from [pick yer retailler]....you are correct - there is usually a folder with the win(os) cd contents. Go find that and burn it.

When you bought your machine from one of these retaillere you also recieved a "rescue" disc. Or a disc that lets you boot to it and reinstall your "computer" to the point of "new purchase".

OK - let's wrestle with that for a moment, shall we?

Forget what you have heard and listen to me. This is easy. Go have a smoke - of play some ball - or do whatever it is that you do to relax.

OK - I will forgo all the variables and assume we are at dell central - winxp preinstalled - (forget all the ancillary "dell" stuff -) and you have one large partition (huh - 80 gb - ever wonder why your box had problems...)

Go download [http://www.sysresccd.org/](http://www.sysresccd.org/) .  Burn it to a disc.  You will be booting to this.  If you are really worried - just back up all yuour stuff - and burn it to a disc.... at least you'll have all your (??)  and emails, ey. 

All backed up? got that rescue disc burned and ready to go? Good 

Take a last look at windows. Give it that crooked smile of yours...put the rescue disc into your cd tray and reboot -- smile.

I'll reiterate my last post because I think I was talking on the phone when I typed it - I like to multitask...

Boot to the rescue disc...at the first prompt type MENU - hit enter.

Next prompt - arrow right, down 2 or 3 (memory here) choose Rescue ...
Do it.

Smile and wait for your prompt -- whiz-bang, you're at the prompt.

type: run_qtparted , hit enter.  (you ROCK!)

choose your mouse - ps/2 - just type - 3.

wait for it -- wait - cool.

You are in qtparted. Click hda on the left-top of your screen - now look right...

See the rectangle depiction of your hard drive...click on it. The pic...I think you can right click and choose resize now, or just click on the pic and use the menu to find resize.

You won't really see anything happen. In qtparted you must now "commit" the task. 

IN the menu now find "commit" tell it yes, and watch in technicolor-amazement as your harddrive is resized...well, your giant partition anyway.

Now - make some new partitions and read my above post.

What the really paranoid (or just responsible? I'm not sure) would do after creating their new partitions is this:

after you  make your new partitions, and format them (ext3 - just do it) you now have a new place to put an image you can make of your existing winxp installation.

Cool.  Close the qtparted proggy.

run:  cd /mnt
mkdir backup
(you're already root, silly)

mount one of the new partitions you just made to backup.
( mount -t ext3 /dev/hda4 /mnt/backup ) hit enter

run (type) partimage , hit enter.

partimage is friggen glorious and simple.  You will see a horizontal row of your partitions on your drive when partijmage opens.  What should be highlighted already is your first partition on the drive - that's your winxp installation -- see it -- you ROCK!!!!

tab down to choose backup - follow the directions, it's easy to figure out.  Stop thinking your a n00b or rookie or whatever and just do it. Get a grip, you rock.

make a image of your winxp partition - call it whatever you want (winxp-img), type in the address of your new mounted partition , hit F5 a coupla times and whiz-bang -- DOOD you just backed up your winxp partition in about 4 minutes -- you stored it on a newly mounted partition you friggen MADE AND FORMATTED and you did all this before breakfast.

Can you beat that with a stick --NO!? Now - feel good about your bad self and spread the word. Help a friend, go play tag 'cos you da MAN.

===============================
If you didn't just whip out partimage and back up your winxp partition you will be at the point of just having made your new partitions following the resize of your giant original partition.

close the proggy -- reboot.

Pop in your fancy Ubuntu cd and get to installing.  Remember - you already made partitions and they're ready to go -- when you get to the point of opening the partitioning manager during your Ubuntu install - just choose to use partitions, choose your file system and label and you're good to go.

Remember, leave hda1 alone, thet's NTFS (you'll see it) and it's your windows - that you just labored to save...

choose your 10gb hda2 partition to be /, then choose your giant-ass hda3 partition to be /home. Your last small partition is the place you saved your windows partition image to - if you did that - or you saved it to partition 3 or 4, who knows -- you know what you did and you ROCK!

So be done.  You have winxp and ubuntu. People the world over envy your savy ways.

happy computing.

PS - I never proof these long-winded posts. Sorry for errors.

---

### Post by firehound on 2005-02-20
thanx I'll give it a try

---

### Post by zcox on 2005-02-20
So I got Ubuntu installed for dual-boot alongside Windows ME (don't ask  why ME - it's the in-law's computer).  The key was realizing the partition manager in the Ubuntu installer lets you resize an existing partition.  This was really not obvious to a newbie like me.  Hint for Ubuntu developers: make a task-oriented partition manager for Ubuntu installer, with options like "create new partition from existing to install Ubuntu to" or something.

So I resized the single existing partition to half its size and created two new ones: one for / and a 500MB one for swap.  Made them both primary and set the / partition to bootable.  The rest of the install was flawless: Ubuntu works great, GRUB was installed fine, and I can still boot to Windows.  Yay for Ubuntu!

I think I'm going to make a tutorial for complete Linux newbies (like me) on how to add Ubuntu to an existing Windows machine.  I now have 2 more questions:
 1) how can you take screenshots of the Ubuntu installer?
 2) how can you access your Windows files from Ubuntu?  do you have to mount the Windows partition or something?

Thanks for all the great advice so far!

---

### Post by machiner on 2005-02-20
Terrific.

 1) how can you take screenshots of the Ubuntu installer?

                I would use my digital camera.

2) how can you access your Windows files from Ubuntu? do you have to mount the Windows partition or something?

You would make a directory for these files (your windows partition, directory...) to mount to:

cd /mnt
sudo mkdir <name>

then you would mount it:

sudo mount -t ntfs /dev/hda1 /mnt/<name>


in my fstab:

/dev/hdb1       /mnt/ntfs       ntfs noatime,defaults,users,ro,umask=0 0 0

will boot with my windows backup partition  (hdb1) mounted and read only.

---

### Post by caiphn on 2005-02-20
Just in case anyone is interested, my resolution ended up being just to redownload 4.10 AGAIN (I think the second one must have been corrupt) and I guess third time seemed to work for me, as it completely installed. Now that I have Grub on my system, it's letting me boot into my Windows XP again, and Ubuntu finally sucessfully installed. My problem wasn't the theory of partitions, I knew what was happening, I just didn't know how to fix the problem. Thanks for the suggestions, now I just need to figure out how to get my wireless adaptor detected in Ubuntu so I can hit up the Internet.

---

### Post by Ozitraveller on 2005-02-20
[QUOTE=machiner]the quick and dirty: using one particular flawless method.

install your shiny new harddrive. get the jumpers right.

boot to a "rescue" disc -- ( [http://www.sysresccd.org/](http://www.sysresccd.org/) )

type menu
choose rescue disc

let it voot you to a prompt.  Glorious.

type: run_qtparted.

make your partitions....the 1st is NTFS - 'cos you're going to install your winblows after  this.

hda1     ntfs     2gb    (set ACTIVE)
hda2     ext3     5gb     /
hda3     ext3      25gb   /home
hda4     swap  (if this is even necessary - got 1gb - you don't need a swap)

(sizes are arbitrary - pick your own sizes - just give win 2 gb)

cool -- there's your drive.

Now --  reboot, pop in your winxp disk -- get comfortable - install.

when it's in -- great -- go turn all those damned services off (server...anything remote...you know the drill)

reboot -- to your shiny new Ubuntu disc....when the partition screen comes up - you've got them -- just assign them now -- and leave hda1 alone - duh!

finish that - when you are asked if you would like Ubuntu to install Grub -- let it.

Ya - it's a GOOD THING. Just let it.....finish your ubuntu system.

Great.

Reboot - hit escape when ytou see Grub -- looky there - pick Ubuntu or windows to boot to.

You did it.  SPectacular....you ROCK!!!~


Just remember this easy formula:

if it's a windows disc - you've got a new frisbee. Ahem! -- windows goes on first - and it likes to be on the first partition of IDE1.[/QUOTE]

Enjoyed your post machiner! Just 1 question though, why [http://www.sysresccd.org/](http://www.sysresccd.org/) as a rescue disk? Are there others? Is this the best? Just curious..no quarrel. I've downloaded this one, until I find a better one...

I think it's worth adding this thread into "Unofficial Ubuntu Starter Guide"

---

### Post by wallijonn on 2005-02-21
I cleaned my W2KP (System Options -> Cleaner), then ran defrag, rebooted, defrag'ed, rebooted, de'fraged.
I downloaded and ran BootItNG.
I started the Ubuntu Install CD, chose manual for partitioning, selected the new space, installed Ubuntu and rebooted. I got the 'can't boot into W2KP problem, so I copied ntldr and ntdetect.com to C: and dual boot works fine.

Now I've done away with W2KP and installed W98SE in it's place. (I gotta play the original "System Shock", you know.) W2KP and WXPP are on my other machine, now.

---

### Post by machiner on 2005-02-21
[QUOTE=Ozitraveller]Enjoyed your post machiner! Just 1 question though, why [http://www.sysresccd.org/](http://www.sysresccd.org/) as a rescue disk? Are there others? Is this the best? Just curious..no quarrel. I've downloaded this one, until I find a better one...

I think it's worth adding this thread into "Unofficial Ubuntu Starter Guide"[/QUOTE]

Geez - I don't know, it's not very well written or very logical. If it helps then -  good.

My dics recommendation -
It's really a Gentoo live disc. You know what, though - it works, it's small - quick download - burn -- now you can rescue systems the world over...windows, linux...

I "found" this utility disc about a month after I started playing with linux again. It's very important to become fluent in admin utilities such as this.

If you run an OS - you need to know how to manage it - same with harddrives, cars, marriages, websites...so - I quickly got used to the desktop, then moved to maintaining, effecting - you know. I'm a geek, you're a geek.

I bet there are any number of alternatives to the rescue disc I mention. Some might even be better - who knows? The way I look at it:

If you search, and find something that suits your needs and quickly - well, damn - a good search. Keep the find and move on.

Best of luck in everything - happy computing.

---

### Post by Ozitraveller on 2005-02-21
[QUOTE=machiner]Geez - I don't know, it's not very well written or very logical. If it helps then -  good.

My dics recommendation -
It's really a Gentoo live disc. You know what, though - it works, it's small - quick download - burn -- now you can rescue systems the world over...windows, linux...

I "found" this utility disc about a month after I started playing with linux again. It's very important to become fluent in admin utilities such as this.

If you run an OS - you need to know how to manage it - same with harddrives, cars, marriages, websites...so - I quickly got used to the desktop, then moved to maintaining, effecting - you know. I'm a geek, you're a geek.

I bet there are any number of alternatives to the rescue disc I mention. Some might even be better - who knows? The way I look at it:

If you search, and find something that suits your needs and quickly - well, damn - a good search. Keep the find and move on.

Best of luck in everything - happy computing.[/QUOTE]

Thanks machiner. I've already donwloaded the iso and burned it. So this is a keeper for now! Any you are right about geeks, peel off the layers like an onion, and then put it back together blindfolded.

---

### Post by jacob on 2005-02-21
This thread should definitely be added to the user guides - it solved my problems when I had been about to give up on LINUX. The key seems to be using a LINUX program to do the partitioning - I had tried numerous other programs (xp installation, dos, seagate etc) and all of them gave me problems and didn't allow me to dual boot. The only other thing to add is changing the BIOS to read the disk in LDA (or is LBA I can't remember) mode if windows doesn't start.

---

### Post by Ozitraveller on 2005-02-21
This thread has moved to :

Ubuntu Linux Forums > Ubuntu Linux Support > Ubuntu FAQs & HOWTOs

HowTo: install Ubuntu for dual-boot with Windows 

[http://ubuntuforums.org/showthread.php?threadid=16353](http://ubuntuforums.org/showthread.php?threadid=16353)


And Machiner has smoothed out his instructions.

Thanks Machiner!!

---

### Post by wheatpuppet on 2005-02-21
Here's a related problem that's been vexing me for a while:

I have a 40gb drive and I want to put WinXP (64-bit edition) and Ubuntu (64-bit edition) on the same drive, with a 10gb partition for each OS and a 20gb shared partition. So far I seem to be failing...

The common-sense approach would be to partition the drive first, install Windows on the ntfs partition and then install Ubuntu. The problem I'm getting is that Ubuntu never recognizes that anything is installed in the ntfs partition.

One thing that's been a problem is when guides say "when the installer asks, DO NOT install GRUB" ... I don't get that option, as far as I can tell. Is this something specific to the Ubuntu 64-bit installer?

Any help would be much appreciated.

---

### Post by zcox on 2005-02-21
After I got Ubuntu installed alongside an existing Windows install for dual-boot, I put together a little [tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) on partitioning for newbies (like me).  Hopefully people will find it useful!

---

### Post by wheatpuppet on 2005-02-21
I'm giving your a tutorial a try with one major difference -- I used the WinXP64 installer to install Windows first, but into a 10gb partition instead of resizing partitions.

Here's a good question -- does the Ubuntu installer detect Windows XP 64-bit edition? We shall see soon, I guess... :-?

---

### Post by wheatpuppet on 2005-02-21
Well... the answer to the above question is a resounding **no**. The Ubuntu installer does not detect the beta version of Windows XP Professional 64-bit Edition.

I don't know a way around this. Is there a way to poke GRUB to boot Windows? I have no experience with bootloaders, so I don't know where to begin in order to do it myself.

If there's no way I can force GRUB to do what I want, I guess I'm going back to non-64-bit Winblows. *sigh*

---

### Post by Ozitraveller on 2005-02-21
[QUOTE=zcox]After I got Ubuntu installed alongside an existing Windows install for dual-boot, I put together a little [tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) on partitioning for newbies (like me).  Hopefully people will find it useful![/QUOTE]


I'm not surprised that this can be achieved with a fat32 partition, but ntfs is a differnet beast, and I'm tipping this won't work on ntfs.

The pics certainly made it easy to follow!

Maybe someone, with more linux knowledge than myself, could enlighten us.

---

### Post by wheatpuppet on 2005-02-21
Okay. I figured it out, in a manner of speaking--

After I installed Ubuntu, I selected "Give me a command line" and edited the grub.lst config file in /boot/grub and added the following after the other Grub entries:

title Windows XP-64
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

For some reason the account I set up in the installation process didn't stick. Or at least it never stuck in the login frontpage. Oh well. At least I know how to do it. Cheers!

I also commented out the line that hides the boot menu, so I can choose which one I want to boot into every time. I also increased the decision time to 10 seconds.

---

### Post by zcox on 2005-02-22
[QUOTE=Ozitraveller]I'm not surprised that this can be achieved with a fat32 partition, but ntfs is a differnet beast, and I'm tipping this won't work on ntfs.

The pics certainly made it easy to follow!

Maybe someone, with more linux knowledge than myself, could enlighten us.[/QUOTE]

You are right - I just wiped everthing (Windows ME & Ubuntu) and installed a fresh copy of Windows XP with ntfs.  When I get to the Parition Disks part of the Ubuntu installer, I see a single partition with ntfs.  I can select it, resize it to half its original size to make room for Ubuntu, but it doesn't actually get resized: I just get taken back to the Parition Disks screen and I still have a single ntfs partition that takes up 100% of the hard drive.

Does anyone know how to get the Ubuntu installer to resize an ntfs partition?  Or is there another free & easy way to resize the ntfs partition?  ie without buying Partition Magic?

I know others have posted to this forum about partitioning first, then installing Windows XP to one partition and Ubuntu to another.  But I'd really like to make a tutorial for people who want to keep their existing Windows XP installation and not have to blow it away.

---

### Post by wheatpuppet on 2005-02-22
[QUOTE=zcox]You are right - I just wiped everthing (Windows ME & Ubuntu) and installed a fresh copy of Windows XP with ntfs.  When I get to the Parition Disks part of the Ubuntu installer, I see a single partition with ntfs.  I can select it, resize it to half its original size to make room for Ubuntu, but it doesn't actually get resized: I just get taken back to the Parition Disks screen and I still have a single ntfs partition that takes up 100% of the hard drive.

Does anyone know how to get the Ubuntu installer to resize an ntfs partition?  Or is there another free & easy way to resize the ntfs partition?  ie without buying Partition Magic?

I know others have posted to this forum about partitioning first, then installing Windows XP to one partition and Ubuntu to another.  But I'd really like to make a tutorial for people who want to keep their existing Windows XP installation and not have to blow it away.[/QUOTE]
 A quick google search reveals [this](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html). It's an NTFS resizing tool. I just skimmed the page, so I don't know the details of making it go, but perhaps through a boot disk?

---

### Post by zcox on 2005-02-22
[QUOTE=wheatpuppet]A quick google search reveals [this](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html). It's an NTFS resizing tool. I just skimmed the page, so I don't know the details of making it go, but perhaps through a boot disk?[/QUOTE]

I actually found that earlier this morning after my previous post - it's a great tool!  I used it and successfully got Ubuntu installed for dual-boot with an existing Windows XP install.

I updated the [tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) so there's now info for both Windows ME (fat32) and Windows XP (ntfs).  If anyone has more info or corrections for this tutorial, please let me know.

---

### Post by machiner on 2005-02-22
Hey zcox - your pics rock.  I would've taken some, too - if I wasn't so damned lazy.  Your write up will be sure to please -- why did I write my cryptic one if you had one all along?

Dude?

Anyway - terrific.  The more the merrier.

---

### Post by zcox on 2005-02-22
[QUOTE=machiner]Hey zcox - your pics rock.  I would've taken some, too - if I wasn't so damned lazy.  Your write up will be sure to please -- why did I write my cryptic one if you had one all along?

Dude?

Anyway - terrific.  The more the merrier.[/QUOTE]

Thanks machiner!   :-)    I felt guilty for taking all this awesome free software so I decided to give a little back to the community.  Hopefully people find the [tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)  useful.

Your write-up was not only enjoyable to read but also helped me make sure I was doing things right.  Thanks!

---

### Post by Ozitraveller on 2005-02-22
Nice work guys!!!

---

### Post by BillyD on 2005-03-03
[QUOTE=zcox]After I got Ubuntu installed alongside an existing Windows install for dual-boot, I put together a little [tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) on partitioning for newbies (like me).  Hopefully people will find it useful![/QUOTE]


zcox,  

Thank you very much for making this tutorial.   =D>  I will be trying this tomorrow.

---

### Post by zcox on 2005-03-03
[QUOTE=BillyD]zcox,  

Thank you very much for making this tutorial.   =D>  I will be trying this tomorrow.[/QUOTE]

You're welcome!   :D  Feel free to post any problems/questions/comments in this thread - we'd love to help you out.

---

### Post by landotter on 2005-03-03
How to easily dual boot with Windows?

Easiest way, if you've got a desktop, is simply to throw a second cheap HDD in the box, and tell Ubuntu to install to hdb, a bootloader will automatically be installed.

Easy.

---

### Post by klutzini on 2005-03-16
Thanks for that Landotter...

I did that and get the bootloader, but no option to boot up winXP... just Ubuntu.

can I edit the bootloader? as I don't get any other options when I boot up.

I am using Ubuntu on 1 machine and is fast... very fast. fedora FC3 on the other machine... slow.... very slow!!! but it does come up with an option to boot into windows or other OS..

Please put things in simple terms... (pics help!!!) as I am fairly new to linux.

Cheers..

---

### Post by landotter on 2005-03-17
[QUOTE=klutzini]Thanks for that Landotter...

I did that and get the bootloader, but no option to boot up winXP... just Ubuntu.

can I edit the bootloader? as I don't get any other options when I boot up.

I am using Ubuntu on 1 machine and is fast... very fast. fedora FC3 on the other machine... slow.... very slow!!! but it does come up with an option to boot into windows or other OS..

Please put things in simple terms... (pics help!!!) as I am fairly new to linux.

Cheers..[/QUOTE]
 sure you didn't wipe windows and install to the xp drive?

I hope not!

Can't offer anything but Google and recommend the nice grubconf gui utility (grab it with synaptic)

---

### Post by Recked on 2005-03-17
I did all this but when qtparted came up it said it couldn't find any disks! I have two SCSI disks on my Dell workstation build, but it found none so I of course stopped there.

Any suggestions for this newb?

I would really rather just use the slave scsi drive as it is only used presently as a Photoshop scratch disk. Is it possible to have Winslows on the master and Ubuntu on the slave drive?

thanks

---

### Post by JVAGO on 2005-03-17
I am planning to install ubuntu in the future and need an expert opinion about a few things. I will also ask some questions. I would just make a thread but the reason for posting here is that I beleive that zcox and machiner are the best to answer me even though I would gladly accept and response. The opinion I need is odd because it has a few variables. This post might be long I do not know. I am new to linux, a very oldie to windows, and a complete stranger to mac. I own two PCs, one a six year old WinMe OEM PC and another a brand new emachines with WinXP and great stats. First question, is an 80 gig hardrive plenty of space? 2nd Can you use this method to have three OSes so you could run WinXP, Ubuntu, and MacOSX all on one PC? Can you use external hardrives? Does Ubuntu update through itself or do you have to download a live cd or order a new one everytime it updates? Can they all use the same resources E.G. Printer, scanner, webcam ect. Also I am using a PS2 eyetoy camera for my WinPC with old drivers, will these drivers work with Ubuntu and Mac? [If I get Mac] Here are my computer stats on the new one 

Microsoft Windows XP Home Edition SP2 Version 2002
AMD Sempron 3000+ 1.99Ghz, 448 MB RAM
Local Disk C:/ Total: 70.8 GB Free: 59.8 GB
Local Disk D:/ Total: 3.70 GB Free: 1.67 GB
E:/ F:/ G:/ H:/ I:/ Shared/Guests/Jeshuas Docs
Digital Media Manager Supports above mentioned drives
DVD/CD Burner DVD+/-RW 16x Double Layer Multiformat DVDRW  [Have a better one on old PC thats a universal LITE-ON]
C:/ 8200 RPM
10/100 Mbps Ehternet [I am dialup]
7 USB Ports with 2 being used [Camera and Scanner]
56K modem [Duh]
Nvidia Geforce4 MX Interated GPU
Emachines Model W3050 Purchased from Mcalister Walmart in OK
Browser FireFox
Media Player WinAmp
StatViewer [WINXP Only but thats okay] Samurize
The Sims Mega Deluxe [Not installed]
The Sims 2
Sim Coaster [Not Installed]
Empire Earth
EE: Art of Conquest [Above]
Antivir XP
AVG Free
AdAware Personal
FreeRamXPPro
17" Flat Screen Desktop [Not TFT] monitor
1280x1024 Res [ :mrgreen: ]
Headphones Headset Speakers
Lexmark Z22 Printer [Old]
HP Scanjet 4200C [Old]

I listed important programs that I care about and stats. If you need more to clearly asess my position then you are welcome. I was thinking about either splitting the 3/2 OSes in equal parts or making 3/4 parts. One for each and shared space. I am planning on Mac during xmas and must get permission from my PC smart but oh so ever doubtful of my intelligence mother about installing it. I am going to save up for an external 120 gig hardrive and hopefully/maybe mac OSX. The reason I would like to have Mac/Windows/Linux all on the same PC....well thats apparent :mrgreen: Its a hacker/geeks dream to be able to run every program that exisits to know man and have a megasmart computer! I know you only get out what you put in so I want to put it all in  :mrgreen:  Lol. I might not get Mac so hang tight on that dangling promise. I am definetly getting a external hardrive. Gotta have that space! I would love it *day dreams* but thats for later. Hope my PC can handle the Ubuntu. Thanks in advance ;)

---

### Post by JVAGO on 2005-03-18
I am planning to install ubuntu in the future and need an expert opinion about a few things. I will also ask some questions. I would just make a thread but the reason for posting here is that I beleive that zcox and machiner are the best to answer me even though I would gladly accept and response. The opinion I need is odd because it has a few variables. This post might be long I do not know. I am new to linux, a very oldie to windows, and a complete stranger to mac. I own two PCs, one a six year old WinMe OEM PC and another a brand new emachines with WinXP and great stats. First question, is an 80 gig hardrive plenty of space? 2nd Can you use this method to have three OSes so you could run WinXP, Ubuntu, and MacOSX all on one PC? Can you use external hardrives? Does Ubuntu update through itself or do you have to download a live cd or order a new one everytime it updates? Can they all use the same resources E.G. Printer, scanner, webcam ect. Also I am using a PS2 eyetoy camera for my WinPC with old drivers, will these drivers work with Ubuntu and Mac? [If I get Mac] Here are my computer stats on the new one 

Microsoft Windows XP Home Edition SP2 Version 2002
AMD Sempron 3000+ 1.99Ghz, 448 MB RAM
Local Disk C:/ Total: 70.8 GB Free: 59.8 GB
Local Disk D:/ Total: 3.70 GB Free: 1.67 GB
E:/ F:/ G:/ H:/ I:/ Shared/Guests/Jeshuas Docs
Digital Media Manager Supports above mentioned drives
DVD/CD Burner DVD+/-RW 16x Double Layer Multiformat DVDRW  [Have a better one on old PC thats a universal LITE-ON]
C:/ 8200 RPM
10/100 Mbps Ehternet [I am dialup]
7 USB Ports with 2 being used [Camera and Scanner]
56K modem [Duh]
Nvidia Geforce4 MX Interated GPU
Emachines Model W3050 Purchased from Mcalister Walmart in OK
Browser FireFox
Media Player WinAmp
StatViewer [WINXP Only but thats okay] Samurize
The Sims Mega Deluxe [Not installed]
The Sims 2
Sim Coaster [Not Installed]
Empire Earth
EE: Art of Conquest [Above]
Antivir XP
AVG Free
AdAware Personal
FreeRamXPPro
17" Flat Screen Desktop [Not TFT] monitor
1280x1024 Res
Headphones Headset Speakers
Lexmark Z22 Printer [Old]
HP Scanjet 4200C [Old]

I listed important programs that I care about and stats. If you need more to clearly asess my position then you are welcome. I was thinking about either splitting the 3/2 OSes in equal parts or making 3/4 parts. One for each and shared space. I am planning on Mac during xmas and must get permission from my PC smart but oh so ever doubtful of my intelligence mother about installing it. I am going to save up for an external 120 gig hardrive and hopefully/maybe mac OSX. The reason I would like to have Mac/Windows/Linux all on the same PC....well thats apparent :mrgreen: Its a hacker/geeks dream to be able to run every program that exisits to know man and have a megasmart computer! I know you only get out what you put in so I want to put it all in  :mrgreen:  Lol. I might not get Mac so hang tight on that dangling promise. I am definetly getting a external hardrive. Gotta have that space! I would love it *day dreams* but thats for later. Hope my PC can handle the Ubuntu. Thanks in advance ;)

Reposted. Its being thought over. Im dumping the mac idea I am getting a portable 80 GB HD so give me a suggestiong now TY

---

### Post by Thomas the fish guy on 2005-03-19
[QUOTE=zcox]This seems to be an **extremely** common question I see in this forum and all over: if you already have a pc running Windows, how do you install Linux on that pc so you can boot to either Windows or Linux?  

Given the high rate of occurence of this question, I would say there has not been a satisfactory answer.  I think the Linux community could convert a lot of Windows users if it was exceptionally easy to put Linux on an existing Windows box.  Ubuntu is a great distro but it is still too difficult for newbies to get a dual-boot Linux/Windows system up-and-running.

So here's the challenge: either create simple easy documentation to allow a newbie to install Ubuntu on an existing Windows pc so the user can select which to boot without having to purchase commercial software (ie Partition Magic), or add functionality to the Ubuntu installer to automatically detect an existing Windows install and add Ubuntu to the pc in a dual-boot configuration.

Anyone up for the challenge?  Let's answer this question once and for all![/QUOTE]
 Hi, as a newbie who installed ubuntu over windows (a bad mistake), if you find an answer to the dual boot dilema please let me know. I tried the "free full version" of partion magic only to find it restricted a new partion to 8MB in size. Loved the Ubuntu which I installed, however, like many other newbies I could not connect to the net or e-mail. In the list of server types there was no POP3 to chose from...and this is what my server uses. Long live Linux.....cheers Thomas the fish guy

---

### Post by landotter on 2005-03-19
[QUOTE=JVAGO]The reason I would like to have Mac/Windows/Linux all on the same PC[/QUOTE]

Wouldn´t we all..you do know that Windows and OS X have very different hardware requirements? Mac won´t run on a PC. [-X

I´d think about consolidating your windows applications on your higher spec box and dedicating the other one to Ubuntu.

Why you needed to mention possession of an uninstalled version of the Sims is completely lost on me.

Also, you&#341;e aware that Ubuntu is a completely different OS than windows?

---

### Post by JVAGO on 2005-03-19
Im not brilliant but I do get that Ubuntu is not windows but a seperate OS. Actually my brain was dead the other day with that mac stuff. Also if you noticed I posted I gave up on that anyway. And to point out more of the obvious I noted things like games and stuff so I could know if it wouldn't interfere with installation. I am gonna get a seperate HD and install ubuntu on my main HD and use the seperate for memory so I can carry it to multiple PC's and use it :D Then again to save me from my mother I might just put Ubuntu on a seperate HD so she won't go screaming at me :P Thanks anyway but prob solved.  :grin:

---

### Post by paltos on 2005-03-24
I still don't understand one thing. In machiners guide, the windows XP partition gets 2 GB, so where go all the windows programs? In the home partition?

Can you have like, e.g a 40 Gb drive, 

5 GB Windows OS
5 GB Ubuntu
30 GB Shared files?

I don't understand.

What would be best then? I got this 40 Gig Drive, How should i split it up best? I need bit less for Linux then for Windows atm, i guess..

---

### Post by mandy2tom on 2005-05-05
This is what I did
needed files attached 

I have raid0 2 raptor 74 sata's, and a few old drives laying around.
I wasn't going to play with my raid0 so..
I unpluged all my drives, pluged in an old drive
ran ubuntu install, defalt with grub, went fine! 
so then I pluged back in sata's raid0
but I had to change boot order in bios to switch
grub would not see sata raid0 no mater what i tried!
and I wanted "windows boot loader" anyway
found a very simple way,
works great
windows ntfs one drive, "drive's raid0" ubuntu other drive
[COLOR=Red]just drop 3 files on windows boot drive C: [/COLOR] 
and add     c:\grldr="Start Grub"     to last line of   boot.ini
the 3 file's are [COLOR=Red]gldr, bootgrub and in folder named BOOT/GRUB/menu.lst[/COLOR]
menu.lst say's this
######################################################
# GvR April 12th 2005
	color black/cyan yellow/cyan
	timeout=5
	default=0

title Default Boot on HD 0
	rootnoverify (hd0,0)
	chainloader +1
	boot
[COLOR=SandyBrown]#copied from grub menu.lst in unbutu install /boot/grub...somewhere in there find it[/COLOR] 
[COLOR=SandyBrown]#Dont use savedefault![/COLOR]
title		Ubuntu, kernel 2.6.10-5-k7 
[COLOR=Red]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/[COLOR=Red]hdc1[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
boot
########################################################### 
I dont know what gldr and boot grub do but it works
[COLOR=Red]YOU must set this in menu.lst root    (hd1,0)    to point to ubuntu drive[/COLOR] in grub speak!
and have normal install of grub on that drive

P.S. if anyone knows how to make ubuntu live boot from iso on ntfs let me know please.
I tried on raid0 ntfs and on fat32, "boot from ubuntu live.iso on windows"

---

### Post by Camo R on 2005-05-05
Have two laptops both dual booting xp (NTFS) and Ubuntu/Kubuntu.

The guides listed in this thread are very helpful, all i have to add is DEFRAG the drive at least twice before partitioning. Had driver corruption once without the multiple defrags.
After defrags i used an old copy of partition manager i had lying around (although "3d partition manager", "ranish partition manager" and "the partition resizer" should work. Freeware)
Usual installs for (K)Ubuntu have run well ever since, multiple installs on my current laptop.

---

### Post by ruach10 on 2005-08-21
I have a 10gig hdd and 30 hdd, is it possible to use raid0 to make this 40gig drive and have 5gig for xp 5gig for ubunto and 30gig for shared files. If this is possible please tell how and what I need to do it.

---

### Post by Rikko on 2005-08-23
Hi guys,

I read all the threads and can't find an answer (that works) to my situation... Here's my situation:

3 hard drives.
Primary boot disk (according to BIOS): 200GB SATA
Second disk: 40GB IDE
Third disk: 40GB IDE

Right now I have XP installed on the SATA drive. Linux recognizes this disk as /sda
My second disk is /hda
Third disk is /hdb

The primary disk has all space allocated to Windows - it's my massive download/win dev/photo/crap drive. I don't mind mounting it in Ubuntu to access those files so I'm happy to leave it alone.
The third disk (IDE slave according to the cabling, but looks like BIOS has more control than it used to) is my old Windows C:\ - I'm keeping that one unmolested for a few months until I'm sure I have everything I need from it (reinstalled XP a couple weeks ago)
The second disk is there I want Ubuntu.

What I did:
- install Ubuntu from the install DVD. It installed onto /hda fine. It installed GRUB fine. It didn't ask where - I assume it went onto the MBR of /hda... But that's not my boot drive.
I played with BIOS and made the Ubuntu drive the boot drive - that worked... Sorta. I saw "GRUB" at the top of the screen, and my HDD access LED went on solid and stayed that way.. The three fingered salute was the only thing that worked after several minutes.

I do know this approach works, as I installed Fedora Core 4 about a week ago (hated it) and was able to boot it that way - but couldn't install GRUB onto /sda (There's a bug with Anaconda, or at least there's a dialog that says there's a bug with Anaconda).

I read on a Fedora forum that it requires the FIRST 100MB of the primary partition to be /boot in order to install properly - is this a kernel thing or a Fedora-specific problem? It didn't work for me anyways.

What I'd like to try is just boot off a CD, manually install GRUB, and just create an entry for Ubuntu (on /hda) and a second one for Windows (on /sda). Problem is, I can't find instructions simple enough for a moron like me.
Can anybody feed me some step-by-step commands I need to plop into the commandline to get GRUB installed onto my MBL?

Thanks, and sorry for the novel.

---

### Post by Unit #134679 on 2005-09-02
I have Linux on two seperate harddrives. Linux is hda and my Windows drive is hdb. Would I use the tutorial the same way, just changing Linux to hda and Windows hdb?

---

### Post by Waqas on 2005-09-08
[QUOTE=landotter]How to easily dual boot with Windows?

Easiest way, if you've got a desktop, is simply to throw a second cheap HDD in the box, and tell Ubuntu to install to hdb, a bootloader will automatically be installed.

Easy.[/QUOTE]
Thats what Im looking for.. thanks for pointing that out!!

And zillion thanks to Machiner for cool instruction. Thats the best way to treat us newbie!! Thanks guru..  :-P

---

### Post by Ubunt24u on 2005-10-03
Hi my name is Glenn.
I am a newbie and I think I have made a fatal error.
I thought I was loading Ubuntu on to a new partition so that it dual boots with Xp.  But I am concerned that it loaded over Windows XP Pro. 
Bios only sees 1 drive and Ubuntu loads straight from reboot.
Can I salvage any of my files at least?
Any help would be apreciated.
Glenn

---

### Post by aysiu on 2005-10-03
To salvage your files, follow these directions:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

You'll be able to see your Windows files. You can then copy them over to a CD or external hard drive (or floppy or the internet).

---

### Post by Ubunt24u on 2005-10-04
Thank you Aysiu.
I will give it a try.

---

### Post by NemanjaM on 2005-10-04
One more question concearning this conversation(I'd already posted, but no1 replied).

This may sound retarted, but please have in mind that I am a complete linux newbie(and that I don't wish to mess anything big time). 

After finding instructions on setting most things I wish to work in ubuntu I will format my disks and do a fresh installation.

Could you please make a tutorial on how to install those 2 systems, step by step, having in mind master/slave problematics, and other(problematics)?

Thank you for your time!

---

### Post by aysiu on 2005-10-04
I like [this walkthrough](http://users.bigpond.net.au/hermanzone/) because it goes step by step and has pictures.

---

### Post by Ubunt24u on 2005-10-04
[QUOTE=aysiu]To salvage your files, follow these directions:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)
You'll be able to see your Windows files. You can then copy them over to a CD or external hard drive (or floppy or the internet).[/QUOTE]

I tried the directions to mount and I got the following message.

mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /
 
Where to from here?

---

### Post by superprad on 2005-11-09
Hi I need help. I have two seperate hard drives. One with Ubuntu and Other with RedHat. When I boot I get the options to boot either Ubuntu or Redhat.Now I Installed Windows XP on Redhat drive. when I boot It directly goes to windows without looking for ubuntu...what should I doo?

---

### Post by Ashtonian on 2005-12-20
[QUOTE=zcox]You're welcome!   :D  Feel free to post any problems/questions/comments in this thread - we'd love to help you out.[/QUOTE]

First off, I want to thank you for your tutorial. Now I just have a question for anyone who can help regarding this. I am up to the part where I resize my partition. When I move the green box dialog to half and push ok. I get an error saying 'new size can't be less than the space already occupied by data.' From that message i've decided I have done something completely noobish or completely stupid. HELP! 

I'll take a picture so that you can help me out better.
Sorry for the enormous size and thank you for anyone that helps!

[http://slackerhosting.com/qtparted/IMG_0683.JPG](http://slackerhosting.com/qtparted/IMG_0683.JPG)

---

### Post by hhh on 2005-12-22
[QUOTE=aysiu]I like [this walkthrough](http://users.bigpond.net.au/hermanzone/) because it goes step by step and has pictures.[/QUOTE]
That is the guide I used, made repartitioning and installing simple (the second section, "Ubuntu + NTFS". That guide also links to this one...
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

The problems come after that if your on some standard POS like a Dell or Gateway, when you try to wrap your Broadcom wireless card with ndiswrapper, hooboy. For that, I used this...
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)
This would have helped me too, if I had seen it...
[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

Some other stuff I've needed was to install Ogle and make it default (I couldn't get Totem to play copyright-protected DVDs) and to disable an external amp setting to hear sound...
[http://freshmeat.net/projects/ogle/](http://freshmeat.net/projects/ogle/)
Volume Control | Edit | Preferences, scroll all the way down and select External Amplifier.

Wish me luck with getting my Synaptics touchpad working properly, this wiki entry need a few more links added to it...
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by Hugo Magic on 2006-06-01
[QUOTE=aysiu]I like [this walkthrough](http://users.bigpond.net.au/hermanzone/) because it goes step by step and has pictures.[/QUOTE]

Hi aysiu, I'm trying to install Ubuntu 5.10 (Ubuntu+FAT32) on my hp pavilion 513c. The problem is that in the step where I need to do the partitons looks a little bit different, it does not give me this option: 
Resize IDE1 master, partitin #1 (hda1) and use freed space. 

Instead it gives me these 4 options 

Earase entire disk: IDE1 master (hda) - 40.0 GB WDC WD400EB-11CPF0
Erase entire disk and use LVM: IDE1 master (hda) - 40.0 GB WDC WD
Use the largest continuous free space
Manually edit partition table

So wich one do I use in order to get the same result?

-Cheers.:cool:

---

### Post by aysiu on 2006-06-01
I'm not 100% sure, but I think it would be this option: > Use the largest continuous free space If you're in doubt and want more control, you can manually edit the partition table. I think Herman's guide walks you through how to resize partitions.

Also, the new version of Ubuntu just came out today--you may find that installer a bit more friendly (it's point-and-click).

---

### Post by Hugo Magic on 2006-06-01
OK I tried to download the new version of Ubuntu 6.06, but I guess everyone is trying to download it at the same time that the download is very slow and it just stops downloading. So I would like to continue doing the installation with Ubunutu 5.10, so I'm in the partition window, so I clicked on "Manualy partition table" and this is where I am right now:

                                      !! Partition disks
This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings (file system, mount point, etc.), a free space to create partitions, or a device to initialise its partition table. 

                     Configure software RAID 
                     Configure the Logical Volume Manager
                     Guided partitioning
                     Help on partitionning

                     IDE1 master (hda) - 40.0 GB WDC WD400EB-11CPF0
                            #1 primary      5.4 GB    ? fat32   /media/hda1
                            #2 primary    34.6 GB  ? ?   ntfs         /media/hda2
                                                       pri/log              7.7 MB               FREE SPACE

                 Undo changes to partitions 
                  Finish partitioning and write changes to disk

              <Go Back>

OK guys, so I want to give windows 10.0 GB and the rest to Ubutu . 
What do I do now?

So the machine that I have is an hp Pavilion 513c, is the kind of computers that do not come with a disk of windows, so I was wondering if I am gonna be able to make a fresh reinstall of windows later on?

---

### Post by Hugo Magic on 2006-06-01
Hey guys in the last post there are some question marks that are not supposed to be there, in the #1 primary 5.4GB there is supposed to be a "black smily face". In the #2 primary 34.6 GB there should be an "arrow down" and a "black smily face". 

Oh, and I actually need 20.0 GB for windows.

---

### Post by Hugo Magic on 2006-06-04
Hi aysiu!

I'm writing this message from my new OS. I finished installing it five minutes ago. I had to download Xubuntu 6.06. Because I was having problems with Ubuntu 6.06 and Kubuntu 6.06. Two nights without sleep downloading the OS, but it is worth it. The installation was painless, and extremely easy. 

Cheers!

---

### Post by micmac on 2006-06-05
hi ive installed ubuntu on a dual boot  syatem, when i boot ubuntu it asks for my login name  then password  after this there is a command line " me@ubuntu:~$        what do i enter here?      ive got this far  aint wantin to give up now lol

---

### Post by aysiu on 2006-06-05
[QUOTE=micmac]hi ive installed ubuntu on a dual boot  syatem, when i boot ubuntu it asks for my login name  then password  after this there is a command line " me@ubuntu:~$        what do i enter here?      ive got this far  aint wantin to give up now lol[/QUOTE] Try one or more of these commands: ```
startx
``` to start the graphical display ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` to install the graphical display if it isn't installed ```
sudo dpkg-reconfigure xserver-xorg
``` to configure the graphical display if it isn't configured properly ```
sudo /etc/init.d/gdm start
``` to start the GNOME display manager

---

### Post by Pavilion on 2006-06-14
[QUOTE=zcox]This seems to be an **extremely** common question I see in this forum and all over: if you already have a pc running Windows, how do you install Linux on that pc so you can boot to either Windows or Linux?  

Given the high rate of occurence of this question, I would say there has not been a satisfactory answer.  I think the Linux community could convert a lot of Windows users if it was exceptionally easy to put Linux on an existing Windows box.  Ubuntu is a great distro but it is still too difficult for newbies to get a dual-boot Linux/Windows system up-and-running.

So here's the challenge: either create simple easy documentation to allow a newbie to install Ubuntu on an existing Windows pc so the user can select which to boot without having to purchase commercial software (ie Partition Magic), or add functionality to the Ubuntu installer to automatically detect an existing Windows install and add Ubuntu to the pc in a dual-boot configuration.

Anyone up for the challenge?  Let's answer this question once and for all![/QUOTE]

Well I can't express loud enough how really easy it was for me to duel boot breezy and XP also Dapper with W2K.  Grub did all the work.  I simply put fdisk to both hard drives, deleting everything and installed W2K on one machine and XP on the other.  Finally installing Ubuntu on top of windoz .  good luck:)

---

### Post by vasurg on 2006-07-22
Hi, I am a completly newbee for Ubuntu. I just installed Ubuntu. My question is how to access files on NTFS? Thanks.

---

### Post by machiner on 2006-08-24
Hello all,

--<b>WARNING</b>, longwinded and probably scattered, read with caution--


I see hits to my debiantutorials.org site everyday from this Ubuntu forum so I thought I'd chime in and see if I could help.  I'll try to be succinct  (fat chance).

ANyway the common thread here is -- how do I keep Windows and install Ubuntu next to it?  Well, there have been innumerable answers to this question throughout this and any number of other forums.  What you have to understand is that it's simple.  Really.  Just a few things to remember:

TO make things easy, Windows is installed first.  /dev/hda1  is where it wants to be.  If you're starting with a fresh hard drive, or reformatting your existing one to start from scratch here's something to keep in mind about Windows; it runs a lot better if you have its swap partition on another drive all together.  So, if I were to install WIndows I would ideally want 2 hard drives and after the install was complete I would change the swap file location to my next drive.  On a Windows machine, swap is 3X your physical RAM.  Put your swap partition near the beginning of the drive, like /dev/hdb1, or 2.  In Windows jargon it would go on D:\  if D:\ was your second drive.  If you've partitioned your second drive pick the partition on /dev/hdbX close to the beginning of the drive.  As a matter of fact, find a boot utility to partition your drives.  I like qtparted on the SYstem Rescue Disc that I mentioned.

If I had one drive and I wanted to dual boot:

   /dev/hda1 -- NTFS  * (bootable)  at least 3 GB
   /dev/hda2 -- /        ext3       10GB
   /dev/hda5 (logical) for all swap:

            /hda3      windows swap 3X RAM
            /hda4      Linux swap   2X RAM

   /dev/hda6    /home    ext3      XXGB

Sizes are arbitrary and i made them larger than necessary.  Consider your Windows programs - also consider that soon enough you will boot less and less to WIndows because you will find that working on Linux is easier and you will have Linux versions of your programs.


If I had 2 drives I might split the partitions up like this:

/dev/hda1   NTFS  * (bootable)  3GB
/dev/hda2   ext3   /(root)      3GB
/dev/hda3   ext3   /tmp (linux) 1GB
/dev/hda4   ext3   /var         3GB

/deb/hdb1   NTFS   D:\         10GB (for your programs)
/dev/hdb4   Logical Drive  For swap files  

        /hdb2  WIndows Swap 3X RAM
        /hdb3  Linux Swap   2X RAM

/dev/hdb5   ext3   /usr     5GB 
/dev/hdb6   ext3   /home    balance


OK -- the partition structures are sort of whimsical, but they work pretty well this way.  In some camps putting swap on a logical drive is a no-no, but I've always done it with no issues...I'm part of the other camp....I make my important partitions primary because I use partimage to back stuff upo (images) and it only workd on primary partitions.

SO now that you've got your partitions squared away - don't forget to make /dev/hda1 bootable, startable, active -- I think it's called "active" in qtparted.


After you create your partitions reboot to your Windows disc...and install it.  Once you've finished boot into your WIndows and goto your control panel, admin appys, and get into Services...disable at least the following:

remote anything (unless you need it and you're savy)
server (unless you know that you need it. Standalone boxes would do well to disable this, there goes 90% of your problems with internet bad-guys) 

messenger
computer browser
digital licenses - it's attached to media player, I forget what the name of the service is, but I always disable it.
etc., etc., etc.

I even disable plug-n-play (you DO need this to mod your hardware) the print spooler (no printer)  and a host of other crap that I do not need.

If you want to run Windows you need to cover yourself - disable all the crap you know you don't need.  Look stuff up on the internet, search for unnecessary windows services or something.  The scope of this is a whole 'nother article and if you're on a LAN the services that you need are different than those of a stand alone desktop.

After you've made Windows safer to run you can reboot to install Debian -- AHEM, forgot where I was -- Ubuntu.  Pop in that Live disc, etc., etc., etc.

When you're installing, pay attention to the Ubuntu formatter - to me it's more confusing than the old partition manager.

There will be a time when you are asked if you'd like to install Grub to ...  LET IT!!  Grub will see your WIndows install and add it to its list of bootable kernels.

After you have Linux installed -- reboot into Windows and change the location of the WIndows Swap file to reflect where you put the partition for it.  It's OK to make the partition on the C:\ drive zero (0) -- Windows will whine at you and tell you that you need at least x much so you can get debugging info when WIndows farts of otherwise runs like it does... (sorry -- I never had such problems but many (MANY) people do, so, like a good hippocrate I join the bashing fray).  It's OK if you want to leave a 2MB swap file on your c:\ partition -- but why?  Just set it to "0" and move the swap to your other drive on that logical partition that you made.  WIndows really will run better -- remember, 3X your physical ram is the max size, 1.5 X your ram is the min size.

That's it, really -- it's simple enough - don't panic.


For those of you with one hard drive that has been formatted with one large partition you will have to resize your partition and make more.  Again, don't panic -- just make sure that you defrag your existing windows partition 2ce before you start.

You can boot into that SYstem Rescue Disc and download, burn, and boot to it in order to use its utilities -- we'll use qtparted again.

If you've backed up your needed stuff and defraged your drive (twice!) than you don't need to panic here -- do yourself a solid, though -- don't buy software for this.  Send me the money instead.  Or keep it yourself...

When you boot to that rescue disc and "run_qtparted" you'll see a graphical rep of your harddrive, changing it is as simple as dragging a slider to the left.   Then go ahead and make some new partitions.

I wrote a lousy but helpful tutorial for resizing your drive <a href="http://www.debiantutorials.org/content/view/1/138/"> here </a>.


I hope this helps.  THere are zillions of articles net-wide that say the same thing that I just wrote, most of them are probably better - easier to read and understand - so seek those out if this mish-mash was no help to you.  Just consider that this is a pretty simple task and that your best bet is always to have 2 drives.  Raid and mirroring will take on a whole 'nother level -- but you're a geek -- you'll figure it out.  I don't need it so I cannot confuse you further with a tutorial on that.

--machiner

---

### Post by machiner on 2006-08-24
OOPS!

to see ntfs partitions from your Linux box.....If your distro (assuming Ubuntu here) doesn't see and load up your NTFS partitions (icons) on your desktop you can always add a mount for them.

# mkdir /mnt/ntfs
# mount -t ntfs /dev/hda1 /mnt/ntfs


This will mount the windows partition so you can browse it and collect your data.  You can import much of your data into Linux programs, like email, IM, browser stuff, docs...etc.

If you want to make a permanent mount for your windows partition do this:

# gedit /etc/fstab

in fstab add a line like this:

/dev/hda1	/name_it   ntfs <b>ro</b>,noauto,user	0	0


When you are installing Debian (there I go again, I meant Ubuntu) you will have the opportunity to add your windows partition to the list of seen partitions that you may get a desktop icon.  You simply choose to use your windows partition during the install and call it what you like.  It'll be there when you reboot into your OS.

Again -- there are zillions of articles and forum postings that address this.  Do a search, mon.


--machiner

---

### Post by Seine on 2006-08-26
Machiner's guide is excellent and I like his writing style. :) However sysresccd.org is down (temporarily?). Is there a mirror or another tool just as good?

Cheers
Seine

edit: I found this ( [http://ftp.sun.ac.za/ftp/iso-images/sysresccd/](http://ftp.sun.ac.za/ftp/iso-images/sysresccd/)         ) I hope it's the same!

---

### Post by chtidio on 2006-09-12
Well, so much for looking here *before* attempting what I was *so* confident I could master.  Yes, a newbie at Ubuntu, can't you tell?  Used it off the CD for a few days, fell in love and decided to install it, on a system running Windows Vista.  Nice graphical Installation interface, a few questions at the beginning, then an option to erase the detected partion, or resize it or manual partition.  So, I selected to resize it.  Everything appears to go fine.  System rebooted, but NO option to but in Windows :-(

Then, I can to these forums and spent a couple of hours wading through the messages.  Based on what I read, I rebooted, interrupted the process (ESC), went to Grub Edit mode (e), added the Lines (o)

title Windows XP-64
rootnoverify (hd0,0)
makeactive
chainloader +1

right after the "Savedefault" line and before the "boot" line, in the displayed sequence, and then tried to reboot. No dice :(   Then I figured I'd interrupt the process and go to GRUB command line mode (c).  Great..  Now I press tab and get all the commands supported in the mode, but no indication of how I can edit the grub.lst file.

May be I have mucked up the set-up beyond repair, I don't know.  I just gringe at going back to zero and re-installing Vista, etc. I should have read these forums first.  

Any words of wisdom?

Chris

---

### Post by 1peter318 on 2006-09-12
Hi, my name is dan though i am a seasoned windows user/tweaker i am  very green on the  xubuntu 6.06 i just installed. What i have is 3 HDs, the first 2 (hda + hdb)being used for windows (4 partitions) with ubuntu being installed on a "removable drive" (as windows calls it), as it occupies the place of one DVD drive. All went fine  with the install into that drive, and to my suprise my internal modem even works.

However the 1st problem is that Ubuntu must have altered the mbr on the windows disk (no ?'s asked), and so now if i remove the 3rd hard drive (hdc) i cannot boot into windows. I would like to know if there is some way to avoid this situation, or how to boot windows in case that old drive fails. 

The 2nd problem is that ubuntu says the 2 other drives cannot be mounted. 

Thank God for ububtu and for all your help.:wink:

---

### Post by chtidio on 2006-09-13
> **chtidio said:**
> Well, so much for looking here *before* attempting what I was *so* confident I could master.  Yes, a newbie at Ubuntu, can't you tell?...

Responding to my own messages , eh? How lame :-(

Well, I just wanted to add that using Ranish partition manager, I can see that the Windows Vista Partition is there. So, I don;t know if just the MBR is trashed, or what.  And, I was finally able to add the Windws Vista entry to the Grub options.  However, when I select that OS to boot from, I get the error message "Error 13: Invalid or unsupported executavble format".

Could it be that all I have to do is rebuild the MBR?  Are there any instructions on-line for doing that?

Chris

---

### Post by 1peter318 on 2006-09-16
I have also been looking for a reponse to a ?, but for you This may help:
[http://leb.net/blinux/list-archive/blinux-list/2001/msg00042.html](http://leb.net/blinux/list-archive/blinux-list/2001/msg00042.html) 

Grace and peace thru Jesus

---

### Post by You gota love it on 2006-10-08
I have just installed ubunto and the dual boot works fine, But how do i swap the os boot options around, so winxp is default and ubuntu is second (sorry but the wife like winxp)](*,)

---

### Post by el_colombiano on 2006-10-21
Hi am very new to linux my friend has been using ubuntu for a few weeks now and is nuts over it so he gave me a live cd of ubuntu to try out and i think it is something worth learning so i want to install it and still keep windows i have made the partitons but i have been reading tutorials and some say to install grub some say not to install it. so my question is should i istall grub or not? how if i do and should i make a windows recovery disk?

well I have been doing a little reading and answered me old questions. also now I got new questions. First is when i start (only have win media center installed) I get ask if i want to boot windows media center or windows recovery will that have any affect when installing ubuntu?(just to let u know windows recovery is installed in a seperate partition and it cant be moved be partition magic i tried it)
 also i dont want to use grub to dual-boot could i not just add ubuntu to the list i get now(windows media center and windows recovery) if so how?](*,) 

ohh one last thing had 2 partitons a HP_PAVILION(C: ) and HP_RECOVERY(D: ) now i have those two as well as a linux ext3 and linux swap. I can see them all in partition magic but only C: and D: show when I open up my computer in windows should i be able to see the other two or no? ](*,) 

thanks

---

### Post by Chandanp on 2007-02-20
As a newbie I found this website EXTREMELY useful:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You will find info on planning your partition as well as step-by-step instruction with screenshots to install Ubuntu in a dual boot scenario.
Hope this helps.

---

### Post by fritzk9 on 2007-04-01
I know this is an age-old question (dual-boot in Ubuntu/ Linux).  I am currently installing Ubuntu 6.10 on a laptop (HP ZD7000), and found the following online source very helpful for creating a dual-boot system with Windows XP as one of the boots:

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

The above link describes a previous version of Ubuntu (ver. 6.06), but the information is still applicable.  Hope this helps!

---

### Post by Sam Booka on 2007-04-15
Is it possible to put Ubuntu on an external HD, if it is only going to be used on one computer? I am almost out of room on my internal drive, but I have a bright, shiny new external (USB) drive.  Can I do this, or do I have to crack the case (once again)?

---

### Post by thirdrock on 2007-04-21
I am a nube. But I was able to install Ubuntu without a hitch. This is what I did: [http://ubuntu-thirdrock.blogspot.com/2007/04/installed-ubuntu-extremely-simple.html](http://ubuntu-thirdrock.blogspot.com/2007/04/installed-ubuntu-extremely-simple.html)

---

### Post by 1peter318 on 2007-04-23
Thanks for your info, but with me Ubutu will neither auto-mount IDE Fat32 drives as other distros do, nor will it recognize sata drives on my pc. So it is not much use.

---

### Post by machiner on 2007-07-13
Wow.  This is certainly a long-running thread.  I see hits to my tutorial site all the time from it.  That's pretty funny because this thread launched my site.

I've gottan a lot better at writing tutorials and I will actually write a dual-boot one for winxp and Debian next week.  I know where I am, but I'm all about Debian and any Ubuntu users could very easily follow along.

Happy Days

---

### Post by daniel1212av on 2007-07-14
[SIZE="2"]Improvised newbie install on a external drive..

After being unable, as a newbie, to get Ubuntu to only partition part of the large free space on a partition i had made,  and finding that some partitioning  software that i tried would not recognize the USB keyboard on this new Dell E520  (no PS/2), i unplugged my 2 Sata drives, and plugged in a USB pata eternal drive (no IDE pata ports on this mobo), and with Ubuntu in the CD drive i choose to boot from that (by pressing the F12 key during post). 

After loading the Live CD i choose to install to the external drive, which is where it places the boot. Afterwards, with all the drives plugged in, if i wanted to Ubuntu to boot, i would choose to boot from the USB drive. 

That worked well, as it recognized my sata drives (some Linux distro's do not), but i had a hard time getting permission to write to them, even with  ntfs-3g  installed ([http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009).). I was not about to keep  experimenting with  terminal commands, and really only needed Linux so i could back up my Windows OSes (i dual boot Vista and XP - which takes a procedure as well), so i got a good buy on a third sata drive, placed it below the DVD drive (you may have to set the bios to recognize it) and installed and run Ubuntu on that as per above (F12 and boot from that drive).  I found then i could write to an external drive no problem. That is where i am now, but i hope Linux will make it easier to gain permissions, which restrictive, default security i have had no need of so far (thank God - and i found a way to easily gain file ownership in Vista for this). 

Thanks for the good help that so many offer. 

[/SIZE]

---

### Post by vwm8534 on 2007-07-25
Machiner,

Those were the best set of instructions I have ever read. I usually get bored reading them. I like your style, very informative and entertaining. Good job!

---

### Post by Aesir09 on 2007-08-03
good plan but whatever you do **DO NOT USE NORTON PARTITION MAGIC IT IS A HORRIBLE PROGRAM THAT WILL MESS UP ALL YOUR HARDDRIVES AND BOTTING SETUPS**

---

