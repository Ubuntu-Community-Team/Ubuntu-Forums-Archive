---
title: "Operating System (still) not found"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by maxwinter2001 on 2010-01-16
[LEFT](Please bear with me through the first 2 paragraphs.  I WILL get to my Ubuntu question.)
  
 
  
My laptop recently caught the Rogue Internet Security 2010 malware bug.   While trying to get rid of it I rebooted a couple of times.  The second time I could not log in.   The bug had taken away my ability to do so.  I have no money and could not take the machine to be wiped and the software (Windows 2000 Professional, Office 2003), so I decided to wipe the drive myself by installing a Windows XP disc I had. 3/4 of the way through it got to the product key question, and for some reason insisted that the key I have is invalid, (maybe because it’s been used before on another computer?  I don’t know).  
  
 
  
Since, as mentioned above, I am broke, I got to looking up free OS’s and ran across Ubuntu.  It sounded ideal so I downloaded it on a friend’s computer, burned a Live CD, and inserted the disc into my laptop. **I did the memory test: it passed. I had it check the disc for defects: it found none.** So I told it to install.  It got 34% done and then froze.  I was told by someone in the **_[[B]Absolute Beginner Talk**]("http://ubuntuforums.org/forumdisplay.php?f=326")_ [/B]forum to try 

"Alt-PrintScreen" followed by inputting the letters R-E-I-S-U-B.  That did not do anything so the same person told me to unplug and try again.  I not only did that, but over the last few days I have (1) Burned another Live CD and tried it; (2) made one for Kubuntu and tried it, and (3) messed around with various settings in the Setup Center, (they're all back at default now).
  
 
  
That first 34% was the closest I ever got to getting Ubuntu loaded -- until 2 days ago.  During most of the last few days of attempting to load it would not even get to the desktop to start installing.  Usually it would stick at one point or another in the setup? DOS?  whatever, screen, (black screen & white writing).  I saw multiple times " Error on device sr0”  something something "logical block" something something, and a bunch of numbers.  There would be two of these messages repeated multiple times, each followed by the same two (one each) six or seven digit numbers,  before it would quit, presumably waiting for me to give it a command.  Not knowing what to  do I would reboot and try it again.  Sometimes I'd wind up with that screen again, sometimes with the same kind of screen, but which said "Error, defect in disk," something something.  I don't know for sure, but since the hard drive was replaced with a new one a year ago, I'm assuming any defects came from the Rogue Internet Security 2010 bug.
  
 
  
Each time I'd try the Live CD again I would have to start from scratch.  2 days ago I made it to the desktop and startsd the "install" process again.  This time though, when it asked about partitioning, I had it partition off one third of the disk for the parts of Ubuntu that had previously been loaded.  I had previously -- the only other 2 times I made it this far -- been telling it to erase and use the whole disc.  Sure enough this worked (did it avoid the defect in the disk this way?  I don't know), it finally loaded 100%.  
  
 
  
HOWEVER, once I, following it's instructions, removed the CD for the reboot, all I got, (and continue to get), is "Operating System not found."  HELP PLEASE![/LEFT]

---

### Post by sgosnell on 2010-01-16
You seem to have the same problem with installing Windows and Ubuntu.  That would seem to point to a problem with your BIOS, RAM or your HDD.  One is probably bad, and you may need to replace it.  I know you don't want to hear about a hardware problem that is difficult and expensive to fix, but that's my first guess.

Try booting from the Ubuntu CD, and selecting to try Ubuntu without making any changes.  Just boot to Ubuntu, and if you can, then run the partition editor and remove all the partitions from your HDD, then add a new one.  After you apply the changes, try installing Ubuntu.  There is an install icon on the desktop, and I always use this method to install, because it's possible to make sure everything works before doing the install, and if there are problems it's not hard to re-run the install program.  The partition changes might make the HDD usable if it's the problem.

---

### Post by maxwinter2001 on 2010-01-16
sgosnell: I will try the suggestion in your second paragraph.  Thanks.  As for your first paragraph:  I had no trouble installing Windows, I just didn't have a product key for it when it got to that part;  "¾ of the way through it got to the product key question, and for some reason insisted that the key I have is invalid, (maybe because it’s been used before on another computer?  I don’t know)."

---

### Post by maxwinter2001 on 2010-01-16
Correction:  I would have tried your suggestion except (1)  there are 47 files in there (I've just discovered) with the word partition in their names, and none of them are named partition editior, and (2) if I manage to do this, where do I put the partition?  The only time I got Ubuntu to load 100% was when I partitioned off 1/3 and had it install on the remaining 2/3 of the disk.  And finally, since I DID manage to get it to install 100% on that 2/3 of the disk, I'm really reluctant to screw that up by doing it all over again.  Still, I WILL try it if you can tell me which is the partition editor and how much do I partition off?

For the record, we have: autopartition, autopartitiion-loop, active_partition, automatically_partition, etc., all the way to partition.h.

---

### Post by sgosnell on 2010-01-16
Just boot from the LiveUSB disk, and when you have the Ubuntu desktop, click on System, then Administration, then Partition Editor, and it will run.  You have to boot from the USB drive before you can do anything with the HDD partitions.

---

### Post by maxwinter2001 on 2010-01-16
OK.  In reverse order: There is nothing under System-->Administration called Partition Editor.  There is only one item on that System-->Administration list that even starts with a P, and that is Printing.  There is nothing on the list with the word Partition in it.  Are you running 9.10?  If not, maybe our System-->Administration lists are different.

Second, why are you now calling it a LiveUSB disk?  I'm not using a USB stick.

---

### Post by sgosnell on 2010-01-16
OK, LiveCD.  The partition editor may be called GParted in Karmic.  I removed it long ago, and reverted to 9.04.  9.10 has, shall we say, issues with a number of PC models, especially laptops.

---

### Post by maxwinter2001 on 2010-01-16
OK, I see GParted, but now that you tell me about 9.10's trouble with some laptops, (which is what I'm trying to get going here), maybe I should try 9.04.  Where can I get that?  Ubuntu home page only mentions downloading 9.10.

---

### Post by sgosnell on 2010-01-16
You can get Jaunty Jackalope [here](http://releases.ubuntu.com/9.04/), just pick the version you need, either 32- or 64-bit.

GParted is indeed what you need to handle the partitioning.  If you can't boot, and the bootloader can't find the OS, you have a borked installation and you may as well do it right from the start.  If the repartitioning fixes your possible HDD problems, you should be good, if it doesn't then you may have deeper problems, it's hard to tell from here.

---

### Post by maxwinter2001 on 2010-01-16
I found 9.04 and am downloading it on this machine, while the other one is reinstalling 9.10.  I did use GParted to get rid of the partition.  I then rebooted without the disc, and still got "Operating System not found."  So I rebooted again WITH the disc, and it eventually went to the desktop.  And as I said, I am now reinstalling.  By the way, the desktop is black.  I have not seen the orange color on it since the times it would crash at 34% of having the software installed.  Even when it finally installed 100% (when I had it partition off the first 1/3 of the disc), it did so from a black desktop.  Only the top and bottom silver/gray panels, or bars, show.

---

### Post by sgosnell on 2010-01-16
Well, yes, if you remove all the partitions from the HDD, there will be no operating system.  I assume you did add a new partition, or two.  It's your choice, and you can repartition during the install.  I like a separate partition for /home, so I can reinstall the OS, or install a new OS, and keep my settings and data intact.  Not everyone does this.

You should see a brown desktop in Jaunty, when you boot to the LiveCD.  The install screens are different than the regular OS screens.

BTW, what are you using to burn the .iso to the CD?

---

### Post by maxwinter2001 on 2010-01-16
THE 9.10 INSTALL JUST PASSED 35%!!!  WHOOHOO!!! 

Excuse me, but I've been f-----g with this s--t all week and this is a good sign.  Still downloading 9.04, though, just in case.

---

### Post by maxwinter2001 on 2010-01-16
I believe my problems with the machine not finding an OS has to do with it looking in the wrong place when I power it up.  I think it's been looking at the 1/3 of the disk  that only had 34% of Ubuntu installed, and was not looking any further.  So, no, I did not keep any partitions this time.  Told it to use the whole disc.  Hope it works.  If not I'll try 9.04.  

I'm burning the CDs with a Windows 7 pgm that's on this machine I've borrowed to do the downloads and forum messages with.

---

### Post by sgosnell on 2010-01-16
OK, good luck.

---

