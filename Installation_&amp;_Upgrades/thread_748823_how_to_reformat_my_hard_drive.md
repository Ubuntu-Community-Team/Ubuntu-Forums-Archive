---
title: "how to reformat my hard drive"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by X_CheshireCat_x on 2008-04-07
tried to install ubuntu to dual boot with XP. Ubuntu has removed xp... when i try to log into ubuntu it says my username or password are incorrect...
 since i have now lost xp  (my laptop didnt come with a disk) and Ubuntu is not working, i see no point in the leftover partitions (4) on my hard drive. 
im using the live CD but and have tried using "partitions editior" but that crashes before i can do anything... 
how can i wipe the locked sections and stop gpartition from crashing? also tried to reinstall Ubuntu from the live cd but the installer freezes...

---

### Post by Pumalite on 2008-04-07
You can try Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and see if you can boot from it.
If not, try DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
If successful, use Gparted after DBan.

---

### Post by TinSoldier on 2008-04-07
First a question, I have WinXp MCE on a HP ZD8430ca laptop.
Its Hard drive is 80G partitioned into 3 parts (30G approx each)
all where NTFS. 
I did a reformat of E: to FAT32 and installed UBUN 7.10 to it from the live CD.
? Does the C: boot partition need to be FAT32 ?, it's NTFS now !( cause im thinking that that mite be why my install didn't work as expected)
( C: is the boot partition, XP is installed on D: and UBUNTU is installed on E:)

Problem was i started the install and left to take a shower, when i got back the install seemed to have finished, i saw the normal desktop and nothing else.

So i rebooted only to find ( like X_CheshireCat_x) a blinking cursor in the top left corner and nothing else, 3 reboots, same result.

I decided to re-install UBUN ( is there a shorter name here for UBUNTU ? :) without offending) but this time waited and watched.

Some screens popped up for personal info input etc, all went well the second time :) , i rebooted and UBUN popped up, happy,happy,joy,joy.

After a bit i tried to connect with wireless ..... NO GO, it seems i need to install a driver for the broadcom wireless, unfortunately at home i only have a wireless internet connection to a nabour buddy's  router.

So from the boot menu i tried to boot XP, NOGO there either, XP reports that "HAL.DLL" is damaged or missing, i checked, its there.....

Sort of panicking now that ubun wont connect Wirelessly and XP wont boot now, i decided to reinstall XP.

Im using XP now and looking for a broadcom linux driver and the proper way to setup / (partition if needed) to do a dual boot with XP and UBUNTU. 

Keep in mind that UBUNTU was already installed ( twice :sad: and should still be there even though it doesn't boot anymore and only XP seems to be there now.

Funny thing is that with XP when i look at my E: FAT32 partition where UBUN is installed it apears to be blank ( no files) i know there are a couple of other small partitions there somewhere .

I want re-install or fix UBUN but i already expect to be put back to the original "UBUN booting an XP damaged again".

Soooo.... whats the proper Hard disk configuration to dual boot XP and UBUN ( XP is only for a back up till UBUN's wireless is working than its a process of setting up software and leaving Windoze$ behind ). 

PS If ubuntu wireless would have worked right out of the box i dont think XP would have been reinstalled, but now.... I know XP will work, UBUNTU did look to be functional except for the wireless, so im not ready to get rid of XP for UBUNTU just yet, i need the wireless internet connection which iv seen a few messages posted about especially with HP's involved.

I'm sort of guessing that this is a weak spot for the two...

Sorry for such a long message beening my first one here and all....

---

### Post by TinSoldier on 2008-04-08
Well, interesting development, after trying to install Ubuntu 7.10 at home AGAIN it once more messed up my fresh XP install, i did find info about how to fix the "hal.dll" problem..

Dont you know i didnt write it down, so ..... it involved "fixmbr" .....

So i decided to take my laptop to work where we have high speed internet either net lan.

I figured since the lan drivers were installed and seemed to be working ( even though i didn't try them before) i would try installing UBANTU at work...

Big SUCCESS, it went flawlessly ..... after the install and reboot a window poped up about "restricted" drivers and options to enable / install them ( my ATI card, the broadcom wireless :)  , and one other were on the list, i enabled all of them) , rebooted and now my wireless seems to be working cause its listing some local signals that iv seem before at work.

Also i got a pop-up about system updates ( 205 of the, one was 18M alone ) i installed all of them cause i just dont know enough about LINUX and its flavours to decide if any shouldn't be installed or not needed........ lets hope everything continues to work well...

Now i cant wait to get home and test out the wireless ......

Soooo, i wont be fixing or re-installing XP....

PS  Can anyone give me a quick `how-to` to create a back-up of my newly installed and updated OS....

---

### Post by Pumalite on 2008-04-08
Take your pick:
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by TinSoldier on 2008-04-21
For more on my wireless situation see here.

[http://ubuntuforums.org/showthread.php?t=756049](http://ubuntuforums.org/showthread.php?t=756049)

---

