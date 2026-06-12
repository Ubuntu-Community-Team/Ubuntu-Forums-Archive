---
title: "no boot on dual boot (with WinXP) - after boot-repair - 2 HDD - please help"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by David_G._Butterwor on 2014-11-08
Greetings!  I'm new and relatively newb (but I'm learning - the hard way).

Currently - I am unable to boot the brick.  It was working for a while.  Most recently, after install of Mint 17 (64 bit), it would boot to Mint  straight up, but no WinXP.  After running boot-repair, it now boots to "Grub>" prompt only.

Here's the history (in part - I believe all the parts relevant to devining a solution):

[LIST]
[*]- Base system: WinXP (32 bit), two HD (processor: Intel Core2, dual processor - not original to machine, hence 64 bit capability) 
[*]- 1st Linux install (using DVD): Ubuntu 14.04 on 2d drive (sdb), using the whole drive (creating new partitions for Ubuntu, with 4Gb swap partition) - installed "boot loader on sdb1 (I realize this is wrong now (should have been sdb) - but this also probably irrelevant history).
[LIST]
[*]This system worked, with dual boot capability, using the BIOS boot menu and choosing which disk to boot from - never did see the GRUB menu. 
[/LIST]
  
[*]- 2nd (and current, but now non-functional) Linux install: Mint 17 - in the same partition/over the Ubuntu 14.04 (formatting the formerly Ubuntu partition) -
[LIST]
[*]NOTE: _installed boot loader on sda (the WinXP disk)_ (thinking this might allow for GRUB to work as expected - oops) 
[*]NOTE ALSO: on both Linux installs - WinXP was NOT recognized - I forget exact wording, but the option for a dual install was not offered.  I did the install using the "do something else option" - manually selecting/manipulating the drives/partitions. 
[*]This system booted straight to Linux Mint - no boot menu given.  I could not boot to WinXP. 
[/LIST]
  
[*]- Attempted repair: ran "boot-repair" using live session from DVD boot (following the excellent instructions at: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).
[LIST]
[*]Note for others that look at that this - I used the following repository to install boot-repair in the live session - noted as to be used for Ubuntu 14.04 and newer:
```
sudo add-apt-repository ppa:kranich/cubuntu
```
  instead of - for Ubuntu 12.04:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
``` 
[/LIST]
  
[/LIST]

[LIST]
[*]- Result: System now boots to GNU GRUB version 2.02~beta2-9ubuntu1 promt (noted as having "Minimal BASH-like line editing support): "grub>"
[LIST]
[*]It does this for attempts to boot from the sda or the sdb drive. 
[/LIST]
  
[*]boot-repair reports (I ran it twice):
[LIST]
[*][http://paste2.org/2KyNDCP1](http://paste2.org/2KyNDCP1) 
[*][http://paste2.org/BK5AJG9G](http://paste2.org/BK5AJG9G) 
[/LIST]
  
[*]- Request:  Please help!  It seems that boot-repair in advance mode has the tools to fix this problem, but I have resisted my natural tendancy to tinker and followed the advice in the boot-repair help page to ask for help before forging boldly ahead with this problem. 
[*]- Thanks in advance!! 
[/LIST]

dgbutterworth ~  If it ain't broke, your not trying hard enough to fix it ... try harder!!

---

### Post by yancek on 2014-11-08
You have installed the boot code for the Mint Grub2 in the master boot record of all three drives.  For some reason, there is no grub.cfg file in the /boot/grub/ directory.  That is the menu file you see on boot which of course you don't see as it doesn't exist.  I'm not sure how that happened.  I'm not familiar with boot repair so can't give you any specific instructions.  You might take a look at the link below which has detailed information for 'reinstalling' Grub on Ubuntu and derivatives.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2014-11-08
It does say grub reinstalled ok to MBR. error code 0 is no error.

But had issues, did you edit grub configuration file?
Syntax errors are detected in generated GRUB config file.
So you do not have a grub.cfg file to boot from. You may be able to manually boot or use supergrub.
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1](https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1)


But you do have proprietary Windows software managed by flexnet which writes into the same sectors as grub after the MBR. They used to overwrite each other but now grub just writes around it.
 grub-install: warning: Sector 32 is already in use by the program `FlexNet'

But better just to install grub to sdb, Windows boot loader to sda. Boot-Repair's auto fix just installs grub to every  drive's MBR. Better to use advanced mode and just reinstall grub to sdb, install a Windows boot loader to sda and set BIOS to boot from sdb.

Time to retire XP, I totally shut mine down two years ago when I got an SSD which needed AHCI which would have required reinstall and major work arounds to make it work.
You also have a 3TB drive using an odd 4K logical sector. That may be the only way to get it to work with Windows XP, but it really should be gpt partitioned.
Note: sector size is 4096 (not 512)

      
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

    
GPT Advantages (older but still valid)  see post#2 by srs5694:
 [http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


Not familiar with new ppa for Boot-Repair.

---

### Post by David_G._Butterwor on 2014-11-08
Thanks for the reply.  I looked at that page and may get back to it.  I'll let you know as things progress.  And yes, I believe I did try editing a file, so I may have messed things up that way.

---

### Post by David_G._Butterwor on 2014-11-10
Yancek and Oldfred - Thanks for your input.  The solution:  Following the guidance in [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) (as suggested by Yancek), with the input and observations from both of you fine people, I solved the problem using "boot-repair" - installed and run from a live session booted from the Mint 17 DVD.

I did not use the top button - "fix most common problems".  As noted, this installs grub on every hard drive.  This caused problems... obviously.  And why would you ever want to do that?  In my humble opinion, that option has significant danger.  (I think I have some remnants of grub installed on my sbc disk (which is  removable - usb drive ... when I started up windows, it appears an autorun file kicked in, and I was asked what I wanted to do with this newly inserted media.  A silly question ... in my context ... never asked before.  And I don't think that autorun file was there before, but no big deal.)

I have screen shots of the selections that I made and if anyone wants to see them (or would otherwise like to know more about the solution), I'd be happy to upload them and provide and guidance or guesses on specific methods for resolving similar problems.  With some basic understanding of what's going on, the selection of options is not that difficult.

I did have to run boot-repair twice, to get the complete fix.  I forget exactly why (my screen shots would remind me), but I think that the repair of the Windows XP MBR did not (or could) not be completed in the same run as the reinstall of grub.

Anyway - your comments and observations gave me the courage to forge ahead and complete that task.  Tinkering with the looming potential of darkness from a functional brick is somewhat unsettling.

So ... now on to my next "fix" ... I'll be back when I break it again ... because: If it ain't broke I gotta try harder to fix it.

dgbutterworth

---

### Post by oldfred on 2014-11-10
Glad you were able to resolve issue.

Did you use the full uninstall & reinstall of grub2? That is like or is a full chroot fix.

---

### Post by David_G._Butterwor on 2014-11-10
THANKS FOR YOUR INPUT - IT HELPED.  AND THANKS ALSO FOR LINKS TO INFO RE MY 3TB DRIVE CONFIGURATION. 
 
MY CURRENT CRISIS IS FIXED, AND ALL IS GOOD NOW.  I'LL HEAD OFF TO MY NEXT FIX IN JUST A MINUTE.  (I'M THINKING OF TRYING SOME OTHER DISTROS, BEFORE LOCKING IN.  CUBUNTU LOOKS COOL, BUT I CAN'T MAKE IT DO ENGLISH.  SURELY I CAN FIND A NEW WAY TO BREAK SOMETHING, BUT I'M READY FOR GRUB/BOOT ISSUES.)

BUT FIRST - I RESPOND TO YOUR HELPFUL COMMENTS, INCLUDING A MINOR DIGRESSION HERE OR THERE (FOLLOWING YOUR THOUGHTS).  [I'M NOT YELLING AT YOU ... BUT USING CAPS TO DISTINGUISH OUR TEXTS.  SURELY I'LL FIND A BETTER WAY, BUT I'M NEW :p)]

...

So you do not have a grub.cfg file to boot from. You may be able to manually boot or use supergrub.
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1](https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1)

BOOTING WAS NOT A PROBLEM (USED A DVD/LIVE SESSION).  (BEFORE I BROKE THE BOOT LOADER, I WAS BOOTING INTO MINT (JUST NOT XP).  IF I KNEW THEN WHAT I KNOW NOW, PERHAPS I COULD HAVE FIXED IT FASTER FROM THERE.  AND NOW I KNOW SOOOOO MUCH MORE THAN I DID BEFORE.  (LEARNING IS GOOD, LEARNING IF FUN.)  

THE LINK TO SUPERGRUBDISK IS INTERESTING  ... SHOWING SEVERAL POSSIBLY USEFUL PROGRAMS.  "RUSKATUX" (WHICH APPEARS TO INCLUDE  "SUPER GRUB2" MAY WELL BE AN EXCELLENT ALTHERNATIVE TO BOOT-REPAIR, BUT I WAS ALREADY FAMILIAR WITH "BOOT-REPAIR" AND ... IT WORKED.  NEXT TIME, I MAY GIVE RUSKATUX A TRY.


But you do have proprietary Windows software managed by flexnet which writes into the same sectors as grub after the MBR. They used to overwrite each other but now grub just writes around it.
 grub-install: warning: Sector 32 is already in use by the program `FlexNet'

THIS IS AMUSING ... ALMOST.  KEEPING WINDOWS (XP AND BEFORE) WORKING HAS BEEN A LONG-TIME CHALLENGE.  I PUSH THE ENVELOPE OF FUNCTIONALITY, AND THE COMP SOMETIMES OBJECTS TO THE OVERLOAD.  (I HAVE TWO COMPS ON THE DESK, BECAUSE SOME WINDOWS PROGRAMS JUST WON'T PLAY WELL TOGETHER.)  I'VE SEEN FLEXNET (I THINK IT RUNS AS A SERVICE) AND I ALSO THINK (VAGUELY REMEMBER) THAT IS SERVES AS A LICENSE BROKER FOR SOME PROPRIETARY PACKAGE THAT I THOUGHT I NEEDED AT THE TIME).  

AS YOU SUGGEST, THE PLAN IS TO RETIRE XP, AND MIGRATE FROM WINDOWS.  EVEN THOUGH I KNOW MY WAY AROUND WINDOWS  (A CONTINUAL CLIMB UP THE LEARNING CURVE THAT NEVER GOES FLAT), KEEP WINXP RUNNING WAS BECOMING NEAR IMPOSSIBLE, AND UPGRADING WOULD BE DIFFICULT AND PROBABLY WOULD NOT HELP WITHOUT MORE UPGRADES FOR THE COMP.  (MY WIFE USES WIN 8.1 (64 BIT)  WITH SIMILAR SYSTEM RESOURCES (4GB RAM) ... AND I FIND IT UNSATIFACTORY ... IT SEEMS THAT AT LEAST 8GB RAMS (OR MORE, PROBABLY FOR MY USAGE) IS REQUIRED.  ON MY WINXP, THE WEB BROWSERS ALONE CHEW UP ALL OF MY RESOURCES ... WHICH THEN MAKES IT DIFFICULT TO DO RESEARCH IN THE BROWSER AND WRITE IN LIBREOFFICE.)

But better just to install grub to sdb,  [I KNEW THIS, BUT I NEEDED SOME AFFIRMATION/HAND HOLDING - THANKS]. Windows boot loader to sda. [YUP ... THERE IS AN OPTION TO EFFECTIVELY DO THIS IN BOOT-REPAIR ... I FORGET WHAT THEY CALL IT ... SOMETHING LIKE RESTORE WINDOWS MBR :p]. Boot-Repair's auto fix just installs grub to every  drive's MBR. [DIDN'T KNOW THIS THEN - OUCH!!!.  AND IT ALSO SEEMS A LITTLE CRAZY.  WHY WOULD YOU WANT TO DO THAT?  (I'M NOT REALLY LOOKING FOR AN ANSWER TO THAT ... I JUST WON'T DO IT.)  Better to use advanced mode and just reinstall grub to sdb, install a Windows boot loader to sda and set BIOS to boot from sdb.  [WHICH IS EXACTLY WHAT I DID, IN SO MANY "WORDS" (READ - SELECTING BOOT-REPAIR OPTIONS ACCORDINGLY ... THEY USE SLIGHTLY DIFFERECT WORDS, BUT IT ALL DOES MAKE SENSE, WITH THE BACKGROUND PLAN OF ACTION.]

[INTERSTING POINT, BTW:  I DID INSTALL GRUB TO SDB, AND RESTORED SDA MBR FOR WINXP.  BUT IT DOES NOT MATTER WHICH DRIVE I BOOT FROM ... BOOTING FROM BOTH SDA AND SDB ENDS UP WITH THE GRUB LOADER ... GO FIGURE.]

Time to retire XP, I totally shut mine down two years ago when I got an SSD which needed AHCI which would have required reinstall and major work arounds to make it work.
[OBSOLUTELY CORRECT ... AND NONE TOO SOON.  IT'S AMAZING THE DIFFERENCE IN PERFORMANCE ON MY MACHINE RUNNING LINUX (64BIT) VS. WINXP (32BIT).  WHAT A RELIEF.  AND IT'S NOT JUST THE 64 BIT OPERATING SYSTEM THAT WORKS BETTER.  EARLY OBSERVATIONS SHOW THE WHOLE SYSTEM WORKS BETTER AT ALLOCATING RESOURCES.  INACTIVE PROGRAMS ARE ACTUALLY ... INACTIVE!  WOW... WHAT A CONCEPT!  (ALTHOUGH, IN FAIRNESS, IN MY EARLY DEALINGS WITH WIN8, IT SEEMS BETTER AT RESOURCE MANAGEMENT, BUT STILL NOT AS GOOD AS LINUX, AND SEEMS CLEAR THAT MORE RESOURCES (RAM) ARE REQUIRED.  AS CHIEF INFO HONEY, I'LL BE LEARNING MORE ABOUT WIN8 AS TIME GOES ON.  LEARNING IS GOOD.  LEARNING IS FUN.) 

NOW ... AN SSD ... MMMM ... SOUNDS NICE.   MAY NEED TO ADD ONE OF THOSE SOON.  I GOT ROOM FOR IT.  AND I GUESS I NOW HAVE THE OPERATING SYSTEM READY TO GO TOO :D!

You also have a 3TB drive using an odd 4K logical sector. That may be the only way to get it to work with Windows XP, but it really should be gpt partitioned.
Note: sector size is 4096 (not 512)
[ THE 3TB DRIVE IS A USB DRIVE, RECENTLY ADDED WITH THE INTENDED USE BEING PRIMARILY STORAGE.  I *BELIEVIE* THAT I SELECTED/SETUP THE DRIVE WITH THAT SECTOR SIZE BASED UPON INFORMATION OR BELIEF OR WILD ASSUMPTION THAT I'D GET MORE ROOM ON THE DRIVE USING SMALLER SECTORS (LESS WASTED SPACE FOLLOWING FILES THAT DON'T FILL SECTORS? ... OR AM I WRONG?.  WHILE INTENDED FOR STORAGE, THE DRIVE IS NOW GETTING USED MORE ACTIVELY  (E.G. EDITING LARGE PHOTO FILES (RAW FORMAT) LOCATED ON THE DRIVE).  SO IMPROVING PERFORMANCE MAY BE WORTHWHILE.

I'LL TAKE YOUR SOURCES FOR SOME BEDTIME READING.  

IF YOU KNOW OF THE TOP:
CAN I GET BETTER PERFORMANCE BY RECONFIGURING THAT DRIVE?
IS IT WORTH IMPROVING (OR, HOW MUCH BETTER)?
AND, LESS IMPORTANT, CAN I DO IT WITHOUT MOVING/DESTROYING THE EXISTING DATA?  (SEEMS LIKELY THAT ONE WAY WOULD BE TO MAKE A NEW PARTITION IN EMPTY SPACE, THEN MOVE DATA TO THE NEW PARTITION, THEN REFORMAT THE OLD SPACE, BUT IF IT'S WORTH IT, I'LL READ UP.)


      
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

    
GPT Advantages (older but still valid)  see post#2 by srs5694:
 [http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


Not familiar with new ppa for Boot-Repair.[/QUOTE]
THE OLD PPA DOES NOT WORK WITH 14.04, AND THE BOOT-REPAIR DISK (WHICH SEEMS ASSOCIATED WITH THE OLD PPA) ALSO DOES NOT WORK WITH 14.04.

AND, THANKS.  AND CHEERS.  I'M OFF TO FIND A NEW WAY TO BREAK SOMETHING. :d

DGBUTTERWORTH

---

### Post by oldfred on 2014-11-10
You can use quotes rather than CAPS. :)

Since some of the external drives use proprietary bits to make it work that way, I doubt that you can easily convert it to gpt now. Full backup would be required at the minimum. Since gpt is the partitioning not the format, it is the entire drive or nothing. MBR was designed back when the first IBM hard drive was created in the 1980's. A TB size drive was not really a consideration and allowing 2TiB drives was so large, I doubt they thought it would ever be used.

The entire Linux partitioning & formatting is so different from NTFS, I do not know how it compares. Seen comparisons on various Linux based formats, where usually ext4 is the general purpose best format.

It just is if using Linux, then having NTFS is slower than native Linux formats, as it is translating thru a conversion layer.

I think Yann is still working on Boot-Repair, but needs some updates for it to work better with the new grub2 and Ubuntu. The new ppa is just a copy of the older boot-Repair version with the correct Ubuntu version for update.

You could file a bug report or wish list to not have Boot-Repair update all MBR. I think it is done just that many users do not know to change BIOS/UEFI to boot from another drive and maybe do not know how. Grub then just works since whatever drive you use it will boot grub.
[https://bugs.launchpad.net/boot-repair](https://bugs.launchpad.net/boot-repair)

---

