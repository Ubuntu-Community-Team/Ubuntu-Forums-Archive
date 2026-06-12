---
title: "Update (grub) broke my Win 7"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Bartcelona on 2010-05-06
-or how I followed ubuntu's help (blindly) to break my win 7 partition with the upgrade This is how I solved it in the last post.

 
...after being on 10.04 for 2 weeks or so I did an update today.
It went through the usual routine and during upgrade process it prompted me for Grub2 upgrade and if unsure I should check all partitions. 
Anyway seems to have worked well until I attempted to boot to windows 7 again.

In short for the last 7 hours I have read all the others post on this and have attempted to follow their advice. Clearly I should have kept a record of all my actions...
In short I have done Win & recovery attempts: automated, diskpart /all the varieties several times. Activated partitions, check with Super Grub, and parted magic. and looked and edited boot files. Nothing solved it for me.

I do still see windows files and can still boot 10:04.
Attached is my Bootinfo from the recommended bootinfo script. 

After 7 hour ( its 2 in the morning now ) I like to take a fresh shot at it is a systematic way.
Any advice on these systematic steps I should take greatly appreciated.

---

### Post by Bartcelona on 2010-05-06
Checked and followed advice from these threads:
[URL="http://ubuntuforums.org/showthread.php?t=1466230"]Dual Boot - Windows 7/Ubuntu 10.4 - No Windows now after upgrade
[/URL] 

[Online Update to 10.04: loss of Windows Boot]("http://ubuntuforums.org/showthread.php?t=1469763")


[Boot Problems:Boot Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

[Will not boot Windows 7 after 9.1 upgrade to 10.04]("http://ubuntuforums.org/showthread.php?t=1471640")

and many more

---

### Post by Bartcelona on 2010-05-07
New Day- time to summarize:

The problem JUST as has been defined in other threads.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But the real fix (as described in linke below) of reinstalling the win 7 bootloader fails.
**[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")**

I have the Win 7 disk and auto boot fix keeps telling me it fixed something and finds the windows install. Manual attempts to fix via bootrec.exe /fixboot,  /fixmbr, /rebuildbcd don't work even though they claim to be doing fixing some in their confirmation responses. (go mirosoft)

Also attempted to activate the partition as some thread recommended. Also removed another drive as some thread recommended. Also updated a the grub.cfg as some thread recommended. Also used super grub disk to get educated and posibly fix this. Also used reread all these threads and really start to feel stupid.

Why when I follow these simple directions can't I get this resolved?

Any help greatly appreciated. Normally I simply use the forum to solve my own problems, so this begging for help is new to me.

---

### Post by Bartcelona on 2010-05-07
Also attempted Microsofts instructions for rebuilding
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
And yes it confirms it rebuild but no results

still nothing

I can get boot back into the ubuntu partition and can still see the Windows partition with all the files.

Looking forward to any suggestions
there must be some way to force the right files to allow win 7 to boot Please any suggestions

---

### Post by Grandon on 2010-05-07
You haven't mentioned your hardware (HDDs) setup.
Is Win7 installed on a seperate disk or on the same?

Are you sure that you have selected the correct partition for booting @ GRUB?

Maybe something in the grub config has been overwritten due to the update.
Check your BIOS HDD boot settings as well.

Greetz,
GND

---

### Post by Bartcelona on 2010-05-07
Hi Grandon thank for trying to help me out.
I have attached a screenshot that explains my HDD config.
Yes all on one drive.
It first had Windows 7 factory installed I then did the Ubuntu install (previous version) that created the new partition (110 extended which is spit up for regular ubuntu use and for swap)

Once again thank you for reaching out to try to help.

Bart

---

### Post by Bartcelona on 2010-05-12
after more then 40 or 50 hours reading all the post about how one should be able to use bootrec.exe and related switches to rebuild or restore the Microsoft booting etc etc they all did not work.

truly I tried all the advice from over 50 threads, and even from other then ubuntu forums how to fix the damage that was done by the ubuntu 10.04 upgrade. And yes I was the idiot to follow blindly the advice from the ubuntu upgrade to install to all partitions if you were not sure where to install grub. I should have researched this more thoroughly. I simply was confused as to what partition this belonged, the windows or ubuntu partition...

anyway perhaps my saga helps others, but this is how I fixed it.
I used supergrub to boot into ubuntu and was able to see that the windows partition was still containing all files.
However in the end when all failed I attempted to rebuild windows via a reinstall. (last resort)
**But still no luck!**
After the attempted reinstall of Windows 7 it simply booted to the same problem. Starting and then showing a blinking cursor upper left corner.

Then I used parted magic to resize partitions and create a new one. Formatted NTFS and flagged boot.
Now installed the Windows 7 operating system with success.

then used ubuntu 10.04 to install grub again.

Then went on to reinstall each and every one of my applications in windows, and copy over files. Then resized the partitions again.

In short Ubuntu 10.04 upgrade with the adviced instuctions to install grub to all broke my windows partition. Oh and the recovery partitions from the pc manufacturer as well.

In short lesson learned. Never blindly follow the advice or help prompts in any upgrade, not even ubuntu. My advice wait a while to do the upgrade and see the fall out. Clearly many many had this issue. 
:(

---

### Post by Bartcelona on 2010-05-12
still if someone can point out that I did it wrong I and that I should have attempted something else to recover I am looking forward to their comments.

---

### Post by skawars on 2010-05-12
exact same problem, there must be a solution? i'm redownloading w7 and gonna burn it to CD and see if i can boot from it and restore windows or something. such a long process, and i'm not feeling too optimistic after your post.

---

### Post by ottosykora on 2010-05-12
exact same problem on my side too. 

Did simply upgrade from net from 9.10 to 10.04 and the only thing could be booted after the job was fedora on the same drive. (one drive, laptop)
There was also xp, w98, debian on that drive. All booted from separate partition containing grub legacy, grub legacy 1 in mbr.

I managed to update-grub in ubuntu, debian and also then w98 and xp started work. Fedoras only difference was that it uses ext4 by force, other linux are ext3 here.

With all advises and howtos I managed to read in one night, no way to restore w7. The MS repair tools told that they are repairing something, but what?? The command line bootrec with different switches (except the mbr one) and all other 'tricks' did simply nothing.
The repair tools did find the w7.

During the update to 10.04, I was not asked any question abt grub, the grub of ubuntu was allways installed in the / being chainloaded from the actual grub partition.

So I have no idea why should the upgrade precess search and modify anything in other partitions and even mbr. I think it should leave all booting as it was. If it was just a bootloader function in the / , then it should leave it this way.

True is: the last windows used before the upgrade of ubuntu, was the w7. Therefore the partition of the w7 was left unhidden and aktiv as it is a primary partition.
Assume that if my w98se was the last one, it the one screwed up.

Anyway the next time I will do some updates on ubuntu, I will try to remamber and have short boot to w98 so it the one which breaks and not the w7. What people with only one windows partition shoudl do, no clue.

BTW: I managed to restore from full image (acronis) the w7, and then all the repair tools did work and did fix the rest.
And for w7 users: it is not essential to download the whole windows DVD, when w7 still runs (or on collegues PC) you can create a boot disk there, this will do all the repai functions (if they work) too.

---

### Post by Bartcelona on 2010-05-12
**Skywars** good luck, and make sure you have a back up of your files via your bootable environment, before you continue anything. For me SuperGrubdisk and Parted Magic and Windows 7 disks were essential. I even had to buy an external CD drive as even the manufacturers recovery partition had been damaged. This was only only cost 50 much less than the 50 or so hours wasted on this in total... 

**ottosykora** I also to avoid headaches like this in the future am looking for some good image / cloning software. 
Found this- 
[http://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software](http://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software)
reviewing the list...
Would really like something that clones partitions as well

I already have my data on a separate disk that gets sync-ed on another drive.

---

### Post by oldfred on 2010-05-12
Bartcelona,

Your original results.txt showed the boot flag on sda1 which was the Dell utility partition. Did you boot thru that originally? I doubt that that partition had the backup boot sector that windows has and testdisk uses to repair the windows when the boot sector is overwriten. 

Your disk utility posting says sda3 is bootable so I assume you moved the boot flag or the windows repairs moved it. Can you now boot thru sda3? You may be missing the dell utility and recovery partitions? 

Grub only can boot a working windows system, so sometimes it is best just to revert to directly booting windows and repairing that. Then reinstalling grub.

---

### Post by Bartcelona on 2010-05-21
oldfred, I believe I originally booted through 3. the results.txt might have been after some point in time but I had tried 1 and 3.

anyway I am happily dual booting for a while now... still need to remove old windows partition and then grow the new one. next week ?

ciao

---

### Post by YellottYellott on 2010-06-08
Same problem here.  My Lucid Lynx CD wasn't installing right, so I loaded Karmic and then upgraded to Lucid.  When it updated grub I took the on screen advice (because I had no idea where I should put grub) and put it on everything that seemed applicable. 

I managed to stumble on a Microsoft thread that (almost) got me back into 7, I'll post it from Ubuntu when I get back in it (Writing this in Windows).  

From the Windows DVD Click next after selecting English and go to the command line.  There are 4 commands, not sure which one was the magic one, but type:

bootrec /fixMBR
bootrec /fixBoot
bootrec /rebuildBCD
bootrec /scanOS

(There's a white space before the slash, although not sure if it matters)

They report 0 Windows installations after executing for some reason, but it works.  This wipes out grub, and for me it wiped out my MBR I think.  On reboot I got a message similar to "Missing BootMGR".  After booting back into the Windows DVD, the Fix Startup or Startup Repair, whatever it is, actually rebuilds the MBR.  Rebooting got me back into Windows, thank God.  This is the second time this has happened to me.  I guess from here you can go about reinstalling grub from google. 


I think previous tries at the Startup Repair option in the Windows DVD were just moving the boot flag around.  That's why it would say it did something, but wouldn't actually work.  

Hope this helps someone.

---

### Post by Moonshield225 on 2010-06-16
Found an easy way out!

I had the same problem as everyone - 
I accidentally installed grub into the windows partition while updating. 
it made windows stop booting from grub, and when I entered update-grub
it said something about the boot folder in the windows partition being inaccessible.

so I opened the folder to which the windows partition was mounted to and found
two similar folders: "boot" and "Boot".
the capital B folder contained .exe's and stuff, and the other contained grub files which shouldn't be there.

I deleted "boot" and ran "sudo update-grub"
grub recognized the windows partition and now everything runs perfect.

REMEMBER TO BACK UP BEFORE DELETING ANYTHING!

---

