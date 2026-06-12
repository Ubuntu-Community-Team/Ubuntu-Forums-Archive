---
title: "Installed Gutsy on an XP PC for Dual Boot - Lost All of My XP settings"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by brewbob on 2007-12-09
I defragged my HD yesterday
I set a restore point this morning before initiating a Ubuntu 7.10 installation in dual boot mode.
I followed the instructions exactly as laid out by APC on how to do it.

***********************************************************************8
I started the install from the Gutsy Live CD that I burned earlier.

After Gutsy did the dual boot partition routine, the next screen asked if I wanted to migrate documents and settings.  After staring at the screen for a while (this wasn't in the guide) I decided to migrate the XP, thinking that it was part of the dual boot process.  

The install continued without a problem, but then I got a WIN XP screen called System Recovery and it directed me to insert my WIN XP recovery CD.  This gave me a bad feeling.  When I did the recovery, I chose Full System Restore With Backup rather than the Destructive one.

As it did its thing,I noted references to files being copied from "restore point".  I assumed that was the point I did this morning.

After going through a lot of recovery, the system rebooted and the GRUB appeared with all the right selection choices, including WIN XP Home Edition which is what I have.

I clicked on WIN XP to make sure it was stable and operating, and it went through another lengthy consistency check.  While I was away from the PC, it rebooted into Gutsy as it timed out.

I checked everything on Gutsy and was extremely pleased with the install of it.  Everything seemed to work fine, including my internet connection and sound, etc.

Then when I rebooted to get into WIN XP, I discovered the damn thing had gone back to when I bought it two years ago.  It wanted to start from the beginning and all of my data, bookmarks, email, etc., are gone.

I then went into system restore and when I did, it showed a restore point that wasn't the one I put in earlier.  It seems that also was deleted during the recovery.

Now I'm not pleased at all with the dual boot of this OS.  I fully expected to have to tweak Ubuntu somewhat, but NOT lose my entire WIN OS in the process.

Before I throw the freaking PC out of my 2nd story window, please tell me that I can still retrieve my WIN XP!   :mad:

---

### Post by brewbob on 2007-12-09
I would REALLY appreciate help on this.

Thanks,
Bob

---

### Post by nateperson on 2007-12-09
Is the "UNDO Restore" option available when you relaunch System Restore?

---

### Post by brewbob on 2007-12-10
I don't remember seeing the "undo restore" option when I tried to do the restore point I had set.  But, at this point, I don't want to touch the WIN XP side until I get info on how to restore it.  Some of the threads mentioned don't do anything to it as it can overwrite and lose the data for good.  Thanks for replying.  I'm somewhat disappointed with the lack of help on the board.  Surely someone has seen this before and can tell me whether or not my data is gone for good.

---

### Post by mozetti on 2007-12-10
Ok, this is what happened (I'm pretty sure): There is a difference between a "Restore Point" in XP, and a "System Recovery." A system recovery CD is generally what PC manufacturers (Dell, HP, etc) provide instead of the plain Windows installation disc. The system recovery disc is generally used if the system becomes unusable or if you just want to "format and re-install" windows because it's become so cluttered with adware/spyware/virii/etc.

So, when it prompted you to do a System Recovery for Windows and you put the System Recovery CD in, you told the computer to reset Windows to it's condition directly from the manufacturer. Why it did this, I'm not sure -- but that's what happened. In my experience, however, the System Recovery CD doesn't delete any data (My Documents, etc) or programs you installed after the fact -- those should still be there. 

But, it will probably reset any user-specific settings like configuration settings and (unfortunately) bookmarks. Regarding the bookmarks, this is because Windows integrates IE into the OS and doesn't manage IE user settings separately from Windows user settings. You might have some luck looking in C:\Documents and Settings\-your username-\ for a bookmarks backup file, but I can't remember if IE does this.

Finally, you received a reply about a Windows problem in less than 24 hours from a Linux forum. Not too shabby, so I'm taken aback by your comment that you're disappointed with the lack of help. Out of curiosity, how quickly did your PC manufacturer or Microsoft get back to you about this problem?

---

### Post by brewbob on 2007-12-10
Mozetti,

Thanks for the recap on what WIN recovery actually does to the data.  I had hoped that would be the case.  And yes, I don't know why the Gutsy install prompted me to insert my WIN system recovery CD.  It was after the "migrate documents and settings" and the subsequent reboot. 

BTW, when the install routine got to the partition process, I went with the default size of 58% as indicated on the slider.  I let it do its thing. 

If all I lost were the configs and bookmarks, I would be pleased.  It's all the photos, files, etc., that I really want to recapture.

Regarding my frustration in getting help, the keyword was "somewhat" disappointed.  I noticed many other posts getting responses within minutes and mine was going for hours without a reply, getting shoved down onto page 3.  My apologies if I insulted anyone with my remarks.  When you lose your primary OS data, it's a critical event and I was totally frustrated with the Ubuntu install routine and the aftermath.

Gutsy works really well, and the only thing I tweaked since the install yesterday was the screen resolution.  No biggie at all and I will be tweaking things for some time to come.  That part about Linux I understand.

Thanks again for the explanation.  Now, I'll try to find those files on the WIN side.

Cheers,

Bob

---

### Post by mozetti on 2007-12-10
No worries, and perhaps you're somewhat knew to using support forums. It's general forum etiquette to only post something related to the subject at hand -- if no one had an idea about your problem (or didn't feel like taking the time -- it's all voluntary, after all) then they wouldn't reply. Especially here, we have users from all over the world, so the right person to answer the question may be in a timezone 12 hours off from you.

You could try mounting your Windows partition in Ubuntu and browsing the files there to see if they still exist.

Final tip -- another forum etiquette regarding getting help. If you post a request for help and it starts falling down the page(s) because of no replies, it's perfectly acceptable for you to reply to your own topic so it goes back to the top of the page -- this is called "bumping" your thread. Feel free to do this a few times, but wait 24 hours from your original post and previous "bumps" before bumping again.

---

### Post by gfg on 2007-12-10
Hi! If you did the XP migration, and it worked, it would have copied your windows My Documents folder to your /home directory. Have you checked if this folder exists? If it does then at least you have the contents of that folder, and can transfer it back to your XP install, if you want to. 
Hope you figure something out.

---

### Post by brewbob on 2007-12-10
> **gfg said:**
> Hi! If you did the XP migration, and it worked, it would have copied your windows My Documents folder to your /home directory. Have you checked if this folder exists? If it does then at least you have the contents of that folder, and can transfer it back to your XP install, if you want to. 
Hope you figure something out.

Thanks.  Problem is, I'm learning Gutsy at the same time trying to fix my WIN OS and data.

I went to the GG File Browser and clicked on the "Home Folder".  It showed some of my WIN files in there but not the "My Documents" folder which would contain 99% of what I'm looking for.

When you mention going to the "/home directory", is that the same thing that I'm seeing in the File Browser?  Or do I need to go into the Terminal and call up the "/home directory"?

The learning experience with GG is good, although I would have preferred not to do it under these circumstances!  :)

Another big question is whether or not I should have done the migration routine during the GG install.  It didn't mention that it was necessary for the dual boot, but I thought if I didn't do it, then all I would wind up with was the GG OS and lose the WIN entirely.  

Thanks again for the suggestion.  I really appreciate it.

Bob

---

### Post by nateperson on 2007-12-10
The "undo restore" option in xp its supposed to undo taking the system back to a previous restore point.  I understand your trepidation about doing anything with the system though.  You should be able to log onto the system to check it without much risk of completely lossing anything.

One option for getting your data back is (I don't know a FOSS option) would be to use Norton Disk utilities.  You used to be able to download a trial version for free for use for a month, if not its pretty expensive.  Install it on a diffrent system and make a boot disk with the recovery software on it.  It will scan your sectors and pull everything it can off your hard drive.

---

### Post by gfg on 2007-12-10
> **brewbob said:**
> Thanks.  Problem is, I'm learning Gutsy at the same time trying to fix my WIN OS and data.

I went to the GG File Browser and clicked on the "Home Folder".  It showed some of my WIN files in there but not the "My Documents" folder which would contain 99% of what I'm looking for.

When you mention going to the "/home directory", is that the same thing that I'm seeing in the File Browser?  Or do I need to go into the Terminal and call up the "/home directory"?

The learning experience with GG is good, although I would have preferred not to do it under these circumstances!  :)

Another big question is whether or not I should have done the migration routine during the GG install.  It didn't mention that it was necessary for the dual boot, but I thought if I didn't do it, then all I would wind up with was the GG OS and lose the WIN entirely.  

Thanks again for the suggestion.  I really appreciate it.

Bob
Yes you can go to the home folder with the filebrowser, or in the terminal to check, it dosen't matter. As far as I know the migration thing should not have harmed your windows install, as it in my understanding just copies the my documents folder from your other OS. I'm sorry that I can't be of more help. Best of luck with sovling your problem.

---

### Post by brewbob on 2007-12-10
Good news!  I went into Windows and found all my data on the C: drive.  It's a subfolder under "MyBackup 09-12-07" (yesterday, when I installed Gutsy).

When I tried to look at the contents of MyBackup folder, I got an "access denied" message.  

So now I'll try to put the data back into Windows.  I also checked the restore routine under the Start menu, but it did the same thing as last night.  It only showed a system checkpoint at the time I installed GG, and my earlier restore point of 9:15 AM doesn't appear. 

I did find Firefox on the drive, and hope the bookmarks are still in there.  I haven't used IE7 for a long time and switched to Firefox and Thunderbird for WIN XP.

Thanks to all who have helped me!

Bob

---

