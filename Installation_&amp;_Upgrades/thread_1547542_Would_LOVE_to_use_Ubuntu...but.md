---
title: "Would LOVE to use Ubuntu...but"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by NEW to 10.04 on 2010-08-06
Hi everybody, I need help.
I own a [Gateway GM5643e]("http://support.gateway.com/s/PC/R/1014859R/1014859Rsp3.shtml") that just had its HDD die, and Vista died with it.
I have no backup or recovery disc for Vista, so the system is now without an OS.
I was hoping I could just buy a new HDD, throw it in, and boot from the 10.04 install CD.
That hasn't worked.  I downloaded the alternate install disc, and am having almost the same issues.  I am prompted to pick a language, then choose what to do.
After choosing install though, I am either given a "Kernel panic - attempted to kill init" message then some more text, then its frozen, or (with the regular CD) it will give me what looks like an install screen with Ubuntu 10.04 listed above a loading bar of white and red alternating dots.  I let that screen run for 4 hours in hopes of it installing, but nothing.
I have tried all the available "boot parameters" that I can find online, and have tried just deleting the "--quiet splash" (regular disc) and the "--quiet" text from the listed boot parameter text shown when "install Ubuntu" is highlighted on the menu screen.
There is a message before the "kernel panic" message that tells me that the softreset of the ATA failed, then it goes on to say that it is limiting the upload speed to 1GPS.
The new HDD I am trying to install to is a Seagate Barracuda 320G SATA drive.  From everything I can tell, the HDD is fine and compatible. 
I can't seem to find much help on installing Ubuntu when there is no OS on the computer at all.  Can this be done?  Do I need a different boot parameter?  Any help would be extremely appreciated, I just have no idea what to do from here. 
Plus, I am not familiar with Ubuntu so everything seems so foreign.
Help me Ubuntu community, you're my only hope...

---

### Post by TBABill on 2010-08-06
I came to Ubuntu under the same circumstances. I lost Vista and hated it anyway so I looked for an alternative. 

Anyway, no you do not need to have anything on the HD to get it to work. The LiveCD "should" get you going with no issue, assuming hardware compatibility exists.

Before going into a panic, did you perform a md5sum verification of the file you downloaded to make the liveCD from? There is a very long string of numbers and letters on the download page where you got the file from (or in another file normally identified as md5sum or something like that). That series of characters is what you then verify your download against. If they match then you know your download is error free. Errors will bork an install in a hurry.

If verified, did you burn the disk at the SLOWEST speed possible? Burning fast is another sure fire way to get errors, thus borking the install.

If you did all that and know for certain the disk is ok, the rest is to just boot and install from the LiveCD, following its instructions to partition (use the whole disk probably), setup your username, etc. If you can't get that far you most likely have an issue with hardware compatibility during install.

Question - did it boot and run fine from LiveCD? If it ran ok from the CD then the problem is probably not the disk. Start with simple and move toward more difficult things after verifying the obvious first. And post your progress and questions with specific info to get further help.

---

### Post by NEW to 10.04 on 2010-08-06
Thank you SOO much for taking the time to respond, I really appreciate it.
I really want this to work, I love everything Ubuntu stands for...
Yes, I ran through the download just as recommended through their home page, I downloaded Infra Recorder (all of this was done at work, I am using a tiny netbook to reply right now), and made sure that the disc contained all the appropriate folders.  I did not change the burn speed though... is it auto set to fastest?  If so, that's what I used.  I will try re-burning it on Monday, but is there anything I can do in the meantime?  I tried just running through it again, and its currently showing that screen with the red and white dot loading bar.  I read that Ubuntu install takes a long time, but I waited 4 hours yesterday with this screen and nothing...
To answer your question, it is strange with how the disc loads, there are two symbols at the bottom center of the screen before I can get to the disc menu (some sort of distorted keyboard next to a figure in the shape of a man, there is a hyphen between the two symbols.)  I hit the delete key, and up comes the disc menu.  Does this sound like a bad disc?
Thank you again, I really appreciate all your help/knowledge.

---

### Post by NE Key on 2010-08-06
This may be a silly question - but are sure you are trying to boot from the CD ?

In the BIOS, is "boot from CD " the first option ? 

(Those symbols you describe don't sound like an Ubuntu disc - is it trying to boot from your hard drive?)

Then, when the options come up, run from the disc CD without installing - this is a chance to check everything works.

Installation should take about 15 minutes.

---

### Post by NEW to 10.04 on 2010-08-06
Yes, in the BIOS I have the "Boot Device Priority" set as;
CD/DVD-ROM Drive
Hard Disc drive
Removable drive
Ethernet
Now, this order was already set up like that- I didn't change anything.
Does this all sound alright?
The disc eventually gets recognized after the F2/F10 screen, and then goes into that odd screen with the two symbols at the bottom.
I can't seem to get the F10 (Boot Menu) screen to open- only the F2 BIOS screen comes up when prompted.
Thanks again.

---

### Post by NEW to 10.04 on 2010-08-06
Okay, trying to run without installing and the load screen with the dots is going.  Should I give it a while, or try it again.  I feel so silly for waiting 4 hours yesterday...
Thanks for letting me know how quick it is.

---

### Post by oldfred on 2010-08-07
It should not take 4 hours unless you have very small memory. Several years ago I installed the then current version on a laptop with only 128MB. It actually did install but did take the 4 hours & then another 4 hours to update. (I am not even sure about that as I let it run overnite).

You may have a video compatability issue. What video do you have? Try f6 on install boot of LiveCD to let you add boot parameters like nomodeset. 

Also review BIOS settings. IDE compatiblity mode, USB mouse & keyboard on etc.

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by NEW to 10.04 on 2010-08-07
Thanks for the info Fred,
I have tried all of the available boot parameters through F6, nothing seems to help.
I was running my video out through a ATi Radeon 2400XT card, but I have since removed it, and am trying to boot from the integrated video (VGA).
The comp has some good stuff (I put a link in the original post of this thread)
There are 3 gigs of RAM, I know now that waiting 4 hours was just me being stupid.  The links you sent are great, but a bit confusing.  It would be better if the were able to show exactly what to add where, it is not written for a newbie like myself.
I understand "boot parameters" (see above threads), but the X/Kernel mode settings is just too vague to be helpful to me.  Example;


If you need to manually adjust mode settings, the video= boot parameter is used. For example, 

 video=LVDS-1:d -- Disables the LVDS
 video=VGA-1:e -- Enables VGA-1

Great!...where do you do this?  
On the boot parameters line when install is highlighted? 
Do you add it just at the end?  Do I need to delete anything,
like the quiet splash?  Is this even the place they are talking about?
Unfortunately, it seems I need a little more basic assistance.
Some of this help seems to be geared towards though who actually are
able to install the software, which as of yet,I am not.

Thanks again everybody, I really appreciate any help you can offer.
Still stuck...  :(

---

### Post by oldfred on 2010-08-07
I guess the first link I gave was the most complex one. I have nvidia and this is what I did at either f6 on liveCd or first boot menu by editing kernel line:

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by NEW to 10.04 on 2010-08-07
Thanks Fred!
Unfortunately, the problem is that I cannot install at all.
I have tried selecting the nomodeset option from the F6 menu,
and all of the other available boot parameters as well- still nothing.
The best I can do is get the program to hang on the Ubuntu Loading screen
with the alternating red and white dots.  Even when selecting the
run Ubuntu without installing option.
From what I understand,
your instructions say to do things after the "first boot after install".
I cannot get to that point yet, and is what I am trying to remedy.
Any suggestions on how to get Ubuntu to install?
You obviously know the program better than most,
thanks again for your expertise.
Are there any quirks with this machine [GM5643E]("http://support.gateway.com/s/PC/R/1014859R/1014859Rsp3.shtml")?
I've hyperlinked the specs, all of which are what I am using.
I have taken out all added hardware (other than the new HDD listed previously),
so I am only using what is shown on this specs list.
Can't wait to try Ubuntu, thanks again for helping me 
with this stuff.

---

### Post by oldfred on 2010-08-07
Some have had success with the alternate installer. It is text only so video issues are not a problem. It is not really much different that the regular installer, more like the way it was years ago, but still the same questions.

Can you boot to the liveCD with the f6 but choose run not install?

Also has links to alternative install, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I am accumulating a list of install issues, see if any of these may apply:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS should be set for IDE compatibility mode
BIOS not set to boot CD or USB first
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happend to set it on)
NTFS partition needs chkdsk, gparted will not see drive if flag set, is set on resize
Other Drive errors - Partitions errors, corruption etc
CD or USB not written as bootable, just copied, DVD or RW (not just R only) sometimes an issue
Mixed MBR (msdos) & gpt partitions (either does work)
Video issues - use f6 to set nomodeset or other options
Computer is older and does not meet minimum install standards
Install stops at partitions or only full disk install - (All four primary partitions used)

---

### Post by NEW to 10.04 on 2010-08-07
Thanks again Fred.
Unfortunately, as I have listed above, I have tried the alternated disc (and verified the disc), to the same results.  Seems I must have an odd quirk or something,
I have tried all of these options, and none of them seem to help.
Any other suggestions would be greatly appreciated.

---

### Post by oldfred on 2010-08-07
Try adding this in place of quiet splash. Not sure if it is a choice on f6 or can you edit the boot line like a regular grub boot.

all_generic_ide

---

### Post by presence1960 on 2010-08-07
On boot when the ubuntu menu appears hit F4 and choose Safe Graphics

---

### Post by corrytonapple on 2010-08-07
Sounds like a bad disc. Be sure to use CD-R high quality discs. As noted, burn at the lowest speed. Ubuntu shouldn't be doing that.

---

### Post by viper250 on 2010-08-07
on your hdd there is a jumper that is usually set at the higher speed for windows 7
you need to set it to the lower speed setting or it will not install linux
2nd check the bios setting for the hdd it should be set to ide mode
these 2 things can prevent linux from loading.

you should also review the distros hcl(hardware compatibility list) you can find this at their website

---

### Post by NEW to 10.04 on 2010-08-09
Thanks for all the input!
I will try adding all_generic_ide to the boot as soon as I get home,
also I will try the F4 safe graphics mode.  Thanks again
As far as the speed of the HDD, I don't think that's right.
The "new" HDD is an older HDD, designed before Win. 7.
I will re-check the BIOS, but I believe everything is alright with the IDE settings.
The HCL list I know is important, I'm having trouble verifying everything is compatible.
Any suggestions?
Also, isn't it true that where you position the drive on the ATA cable will determine it's
role?  (i.e. slave/master)  
How can you tell which is which?
Is the closest spot to the board on the cable always the "Master" spot?

I know its not the install disc, 
it loaded fine on my old Compaq.

Ubuntu's forum here really kicks ***, 
I really appreciate everyone's time/know-how.
Thanks.

---

### Post by cascade9 on 2010-08-09
> **viper250 said:**
> on your hdd there is a jumper that is usually set at the higher speed for windows 7
you need to set it to the lower speed setting or it will not install linux


Whcih jumper? LOL. Most all SATA drives have jumpers to limit sopeed to SATAI, turn of NCQ, etc.. Its pretty rare that you would need to play with jumpers, and if you did, it wont matter if its Win7, Vista, XP, or linux. 

There HDDs with a jumper for XP, the WD 'Advanced format' drives. The jumper is only for use if the drive is going to be used in a WinXP computer, and is going to have only 1 partition on the drive. 

You dont have to use the jumper, even with WinXP, its more than possible to setup a advanced format drive without the jumper. You just have to set up the partitions, d/l the 'alignment' tool, run it and off you go. 

As for use with linux, thats also possible. You just have to stuff around with fdisk for a while. Even if you dont align the partitons, the WD advanced format drive will still install linux, its just a bad idea (speed problems, possible shortening of the lifespan, etc.)  

NEW to 10.04 wont be using an advanced format drive, so it doesnt really matter here anyway.......

> **NEW to 10.04 said:**
> 
Also, isn't it true that where you position the drive on the ATA cable will determine it's
role?  (i.e. slave/master)  
How can you tell which is which?
Is the closest spot to the board on the cable always the "Master" spot?


If you have a PATA drive, with the jumper set to 'cable select' then yes, the position on the cable will determine if its 'slave' or 'master'. 

I never use 'cable select' myself, I perfer to set one drive as master, and  the other drive as slave with the jumpers on the drive.

---

### Post by Shompol on 2010-08-09
""kernel panic" message that tells me that the softreset of the ATA failed,"


New HD -- ATA failed? How do you know the HD is compartible and the bios settings are correct? Here's what I would try:

1. Vista -- you own the key -- you own the license. Borrow a disk from friend, download it from internet and use ur key, or call Microsoft and demand they ship it to you.  Once you have it, verify that VISTA installs. 

2. Does ubuntu boot from CD, without install? If it does not, then it's either a problem with CD or your system does not play well with it.

3. Download the oldest safe version: 8.02, 32 bit, see if that works. I have seen similar problems introduced by 10.04, where as the previous version (9.10) installed OK.

---

### Post by CPL2010 on 2010-08-09
Put it on a USB thumb drive, install takes like...maybe 15 minutes.  I gave up on CD's after my first USB install.  Just make sure you pop the bios to boot from USB device (or whatever the bios offers as a USB option)

---

### Post by oldfred on 2010-08-09
If it is a PATA/IDE drive

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

Jumpers on drive must be set to cable select.

If you have the old kind of IDE ribbon cables (40 conductor) , check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable. Some also have a master with slave jumper.

---

### Post by RJB10 on 2010-08-09
Hi there i have been reading this thread with interest and could i suggest to you that you totally discard for now that disk and start again choosing a different varient of ubuntu to see  if you have a repeat of the problems you mention.
Also could i suggest you dont discard your old hdd until you have tried your new linux disk to see if that reconises it or ideally a ubd4w cd would be best to see if it has in fact died as in my experience that is very unlikely as hard drives dont just one day be working fine with no issues and then be unreconised by the bios and not working.
Have you tried giving the disk to a friend to try for you on their machine as that would be a good idea and could i suggest that you always where possible only use a single drive on your ide 1 channel as the master.
Please dont ashume that if ubuntu 9.10 works for you then 10.04 will also as i can ashure you that will not always be the case so please discard the disk and see about trying another version using some of the suggestions made earlier.

---

### Post by NEW to 10.04 on 2010-08-09
Wow...
There is a lot of different advice here...
I've noticed that some of the questions coming up have been answered,
I'm not complaining, thank you for spending your time,
I just feel like we could avoid some redundant info.
But once again, thank you for trying at all.
Like I said earlier, the install CD is fine-
it installed without hiccup on an old Compaq.
The new HDD I am using is;
Specifications                                         
                                                                                                                                                       Model Number                                         ST3320620AS                                                                                                                                                        Interface                                         SATA 3Gb/s                                                                                                                                                        Cache                                         16MB                                                                                                                                                        Capacity                                         320GB                                                                                                                                                        Guaranteed Sectors                                         625,142,448                                                                                                                                                                                                                                    PHYSICAL                                         
                                                                                                                                                       Height                                         26.1mm (1.028 in)                                                                                                                                                        Width                                         101.6mm (4.010 in)                                                                                                                                                        Length                                         146.99mm (5.787 in)                                                                                                                                                        Weight (typical)                                         635g (1.40 lb)                                                                                                                                                                                                                                    PERFORMANCE                                         
                                                                                                                                                       Spin Speed                                         7,200 RPM                                                                                                                                                        Average latency                                         4.16ms                                                                                                                                                        Random read seek time                                         <8.5ms                                                                                                                                                        Random write seek time                                         <10.0ms                                                                                                                                                                                                                                    RELIABILITY                                         
                                                                                                                                                       MTBF                                         700,000 hours                                                                                                                                                        Annual Failure Rate                                         0.34 %                                                                                                                                                                                                                                    POWER                                         
                                                                                                                                                       Maximum start current, DC                                         2.80

Shompol,
Good idea, I hadn't really thought of trying it that way.
To be honest, I was hoping I could leave Vista for good
But I do have the COA on the tower.
Can you just donwload the install CD online?
I thought Micro$oft only sold those...
I will look, thanks.

Maybe I am wrong RJB, but I do believe my old drive is a goner.
It won't boot and I heard the skid...
I think the platter has slipped somehow.
Have you really not had HDD's go bad on you?
This is the 2nd time in 2 years for me (different computers).
Maybe you have very good luck with HDDs,
or maybe I am just wrong- though Gilware
had to extract the info via cleanroom due to
no retrieval software being able to access the other drive.
I will recheck the drive, thanks.
I am a little nervous about using older Ubuntu...
Is the GUI on those versions easy enough for a newbie like me to use?
Also, can those older versions handle my hardware?
(It is a Q6600 chip).

THANKS AGAIN, ALL YOU EXPERTS!
DON'T KNOW WHAT I'D DO WITHOUT YOU!

---

### Post by RJB10 on 2010-08-09
Hi again i was just wondering if you have had the 2 hdd fail on the same board then it might be time to upgrade the motherboard especially now you have a new hard drive.
Ubuntu works with i386 architechure processors where as fedora will not so always check for compatibility with your intended distros so you will hopefully in the future avoid these troubles you have had lately.
Could i suggest you buy a copy of linux format magazine as each issue comes with a dvd and they normally have 2 or more distros for you to try and that is the perfect way to know which distros will work with your hardware.
I sell hard drives with ubuntu,linux mint etc already on them and they are perfect for testing hard drives and diagnosing your system or just getting a older pc to boot up if someone does`nt have a means of getting it to run or another good way to test your machine is to get a hard drive with maybe win 98 or win millenium edition on it and again you can test your hardware that way.
Im thinking this way for you incase you have anymore trouble with another distro you try also it is always a good idea when you get ubuntu freezing or not getting any further than the screen you mention to flash your bios to the latest available as i have done this in the past to solve the same issue. ok mate!

---

### Post by NEW to 10.04 on 2010-08-09
Thanks RJB
No, different computers with the HDD deaths.
Thanks for the recommendation,
I will have to examine the other versions of Ubuntu.
I'd prefer to have 10.04, b/c it looks like the best release yet.
And my hardware is only a couple years old, so it should be
able to handle whatever Ubuntu throws at it.
Can you look at these specs and tell me what you think?
[GM5643E]("http://support.gateway.com/s/PC/R/1014859R/1014859Rsp3.shtml")
I can't find anyone who has put Ubuntu on a machine like this.
It's not my install discs (I have both the regular and alternate downloads)
they are both working.
I can't run without installing, it just hangs.
I'm guessing I need some boot parameter that has yet to be mentioned.
Or, I am wondering if my SATA port on my MOBO is out.
I have tried 2, but have like 8 in total- one of which is red colored (don't know why yet).
Would a dead SATA port stop the disc from running without installing too though?
I know that doesn't make sense, but I do receive that ATA3 softreset error
during every attempt to install. 
Sigh....

Thanks again.

---

### Post by pbpersson on 2010-08-09
I looked at the specs for your computer and the specs for the HD, they are both SATA II and it **should** just work.

Have you tried completely unplugging the new HD and then tried booting from the live CD to see if you can run it that way?  I mean....forget the hard drive, trying running Ubuntu from the live CD first to see if you can get that running.

Have you seen [this thread]("http://forums.cnet.com/5208-7813_102-0.html?messageID=2797213") concerning your computer?

Do you have the latest BIOS installed?

---

### Post by NEW to 10.04 on 2010-08-09
Thanks Persson,
Yes I have read that thread, I was hoping since it was a different model #, that it would not have the same issues, I can see that it is a related model # though...
I have not tried with no HDD, but I have tried just running it without installing, and have had no luck.  Wouldn't that be basically the same thing?
If not, I will try it with no HDD.
I'm not sure about the latest BIOS, but I have no idea, considering it's current state, how I would update it though.  Any ideas?
Thanks again.

---

### Post by pbpersson on 2010-08-11
> **NEW to 10.04 said:**
> 
I'm not sure about the latest BIOS, but I have no idea, considering it's current state, how I would update it though.  Any ideas?.

You would go to the tech support area of the Gateway web site and follow the instructions to determine the current release of your BIOS and update it if needed.  It is different for every motherboard, depending upon the BIOS type and the update mechanism they use.

---

### Post by NEW to 10.04 on 2010-08-11
Thanks again,
Not sure how I can go online with it though...
There is no OS, and Ubuntu is not installing
or allowing for me to run without install.
If I go online with a different PC,
can I install the update to a flash and install
to BIOS from there?
If I boot from USB, will I be able
to install an update?

---

### Post by corrytonapple on 2010-08-11
Yes

---

### Post by NEW to 10.04 on 2010-08-11
Ho do you install an update to the BIOS when you can't get past a message saying;
"A disk read error occurred Press Ctrl+Alrt+Del to restart" message?
I can get to BIOS, I just don't know how I upgrade inside BIOS.
I can save the update for BIOS (if there even is one) on a disc or flash,
but how/where would you install that?
Any ideas on how to fix a computer that keeps cycling through to that message?
("A disk read error occurred Press Ctrl+Alrt+Del to restart")
I am wondering if it is just a bad SATA cable...
is that uncommon?
The drive worked fine until a couple weeks ago.

---

### Post by NEW to 10.04 on 2010-08-11
how?

---

### Post by RJB10 on 2010-08-15
Hi there!
I have had a few issues my self so have ben busy lately.
Whats happened with anything in the last few days?
I know you were wondering about updating your bios as when ive had trouble with ubuntu locking up it`s been due to something missing from the bios.Only due to it being a oldish machine id installed it on and once id flashed the bios it all stopped.
I have not checked but does your gateway have a floppy drive?
It would probably be the easiest way for you to do it as you`d use a boot disk floppy at first to get to the a/ prompt then exchange that disk with the floppy with the updated version.
It is so simple to do once you have the correct version downloaded so that is why you will have to take a note of your version on there at the moment.
It will say something like this A5182GS V1.1 210198 and it should be on the first screen you see (after any daft logo) so pause it so you can take down the details.
Also make sure you write down the correct board details including version number and skt in use just to make sure once you find your update you can check it`s definetly for your board.
Dont always think you will find a update from gateway so you might have to search for one so just check for (obviosly) bios update for gm5643e or something simular.
Using your version details look for a higher version so i had v1.1 and i updated it with a v1.5.
Try gateway first because even if you can not find what you are looking for im sure it will have somewhere on there a list you can print off giving the exact proceedure they expect you to follow with one of there boards
Also once you have downloaded the update it should contain a read me.exe or something very simular giving the exact proceedure.
Once you have the update it is just about getting to a A:/ prompt preferably by a boot disk or even safemode.
Let me know if you get stuck or can not find the correct update and ill try looking for it for you.
good luck!
ps. if you have any doubts do not try it as you will possibly ruin your pc ok mate.

---

### Post by NEW to 10.04 on 2010-08-15
Thanks RJB!
Literally just got this problem solved tonight!
I am currently using Ubuntu and it kicks ***!
So quick...
The culprit was a bad SATA cable...
Everything seem to go away once I addressed that problem.
Thanks again for all your knowledge and expertise.
Now I need to figure out how to get comfortable with Ubuntu-
like installing things.
Any suggestions on where to look?
THANKS AGAIN EVERYBODY!!!!!!!!!!!!

---

### Post by mörgæs on 2010-08-15
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by RJB10 on 2010-08-15
Hi there!
very good news mate i had not checked your board out so did`nt know anything about it but i was thinking it might be something wrong with your ide channels with it saying disk problems and it`s turned out to be a simular problem but with sata.
Could i suggest ubuntu 10.04 netbook edition as it has a very nice gui what i think you would like very much.
It says it is a ultra fast and light-the perfect linux flavour for mini laptops or older pc,s.
Obviosly you can use it on any pc and it is available on the dvd what comes with the linux magazine this month,as i advised you to buy before as they always have different distro`s on the dvd for you every month and you obviosly always get the latest version.
Im using the lts version here now which is supported for 3 years i think which is always good but only as ive had to add some utilitys to it so my 3g dongle works on it or else id be using the netbook version.
Basically with this version the menu is in the top left of the screen and you click on them and they expand so you can choose what you want simular to how xp start menu works.
With the netbook version all the options are already scattered over the screen so is much easier to see what is avaiulable with a picture and the writing under each one saying what they are simular to what windows desktop looks like once you have added your programs.
So if it is ubuntu 10.04 you want to start with then check the netbook version out and once you are up and running click on update manager and configure it to search for updates regular and it should say that there is 300 available so have a good look at them unticking the ones you dont want and then click update.
Then you can set it up how you want it to search for updates for you and where it gets them from etc
That is the first thing i think you should do if you are totally happy with it and intend on stoping with it.
ok mate!

---

### Post by NEW to 10.04 on 2010-08-15
> **mörgæs said:**
> [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Many thanks!

---

### Post by NEW to 10.04 on 2010-08-15
> **RJB10 said:**
> Hi there!
very good news mate i had not checked your board out so did`nt know anything about it but i was thinking it might be something wrong with your ide channels with it saying disk problems and it`s turned out to be a simular problem but with sata.
Could i suggest ubuntu 10.04 netbook edition as it has a very nice gui what i think you would like very much.
It says it is a ultra fast and light-the perfect linux flavour for mini laptops or older pc,s.
Obviosly you can use it on any pc and it is available on the dvd what comes with the linux magazine this month,as i advised you to buy before as they always have different distro`s on the dvd for you every month and you obviosly always get the latest version.
Im using the lts version here now which is supported for 3 years i think which is always good but only as ive had to add some utilitys to it so my 3g dongle works on it or else id be using the netbook version.
Basically with this version the menu is in the top left of the screen and you click on them and they expand so you can choose what you want simular to how xp start menu works.
With the netbook version all the options are already scattered over the screen so is much easier to see what is avaiulable with a picture and the writing under each one saying what they are simular to what windows desktop looks like once you have added your programs.
So if it is ubuntu 10.04 you want to start with then check the netbook version out and once you are up and running click on update manager and configure it to search for updates regular and it should say that there is 300 available so have a good look at them unticking the ones you dont want and then click update.
Then you can set it up how you want it to search for updates for you and where it gets them from etc
That is the first thing i think you should do if you are totally happy with it and intend on stoping with it.
ok mate!
Thanks again for your valuable input, I really appreciate it!

---

### Post by NEW to 10.04 on 2010-08-15
[size=7][color=blue]ubuntu rocks!!![/color][/size]

---

