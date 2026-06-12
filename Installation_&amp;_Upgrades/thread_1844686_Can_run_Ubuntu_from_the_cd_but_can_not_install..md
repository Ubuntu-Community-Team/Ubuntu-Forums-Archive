---
title: "Can run Ubuntu from the cd but can not install."
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by Neomus on 2011-09-15
Ill start from the beginning.  I was playing a game called Age of Conan and accidentally ran a program in the game folder called system tweaker.  This program is not meant for Windows 7 (what I was running) and it does something to memory usage (have not been able to get much more info than that on it).  I started getting blue screens after the computer was booted up and running for maybe 5 minutes or so.

The first thing I tried was a system restore but this did not solve my issue.  I decided to just reinstall Windows (something I have done in the past with success).  I used some backup cds for the reinstall.  It would copy all the files it needed from the cds and then try to write the files to the hard disk.  I would then get the error: C:\RM\Image\TempBASE.WIM was not found.

I tried using a kill disk I had to completely wipe the hard drive in case that was the problem but it did not fix anything.  

I then decided I would install Ubuntu and see if I could get the problem solved from that end.  Again I kept getting an error when it tried to write files to the hard disk (Errno 5 I think was the error).  I am able to run Ubuntu from the disk (as I am doing right now) but I can not seem to install it.

I have run the hard drive and memory tests I can get to before my laptop tries to load any OS as well as a test in Ubuntu and they all come back saying everything is ok.  I am also able to download files like text files and such and save them somewhere on the computer but of course they are gone when I restart my computer and "try" Ubuntu again.  I also forgot to mention that I ordered new Windows 7 recovery disks and they had the same issues as the old ones.

I am trying to install Ubuntu 11.04.  I am not sure what system specs will be needed to solve the problem but ask and I will provide them.  I really appreciate any help with solving this as I have exhausted my limited bag of tricks and have not been able to find any other post with the answers I need.

---

### Post by MAFoElffen on 2011-09-15
> **Neomus said:**
> Editted- (Broke Windows)

...I tried was a system restore  (still broke)

...I tried using a kill disk... but it did not fix anything.  

...I tried to install Ubuntu... Again I kept getting an hard disk error.

I have run the hard drive and memory tests // saying everything is ok. 

I am trying to install Ubuntu 11.04.  I am not sure what system specs will be needed to solve the problem but ask and I will provide them.  I really appreciate any help with solving this as I have exhausted my limited bag of tricks and have not been able to find any other post with the answers I need.
Hard Disk problems?  So you said that when you do copy files onto the hard disk, that after you reboot, those files are not there?  If you use an Ultimate Boot LiveCD Disk to use a hard disk utitlty to test your Hard Disk... does it show any errors?  The first thing would be to verify that the hard disk is okay,  writable and can hold data-- Which seems to be a problem with your  laptop(?)

I see you are probably at the point now where a fresh install would be an easy task (if it actually worked.)  I guess at the moment, you are probably trying to figure out a plan to get "any" OS to load...

---

### Post by Neomus on 2011-09-15
> **MAFoElffen said:**
> Hard Disk problems?  So you said that when you do copy files onto the hard disk, that after you reboot, those files are not there?  If you use an Ultimate Boot LiveCD Disk to use a hard disk utitlty to test your Hard Disk... does it show any errors?  The first thing would be to verify that the hard disk is okay,  writable and can hold data-- Which seems to be a problem with your  laptop(?)

I see you are probably at the point now where a fresh install would be an easy task (if it actually worked.)  I guess at the moment, you are probably trying to figure out a plan to get "any" OS to load...

I think the files are going away because I am just using the "try Ubuntu" option.  I will try to get a hold of a Ultimate Boot LiveCD Disk and see what the test says.

---

### Post by MAFoElffen on 2011-09-15
> **Neomus said:**
> I think the files are going away because I am just using the "try Ubuntu" option.  I will try to get a hold of a Ultimate Boot LiveCD Disk and see what the test says.
Will wait for your results... Have lots of ideas for you, but all hinge on if the hard disk is good.

---

### Post by Neomus on 2011-09-17
Sorry it has taken me so long to get back to you I have been really busy.  I downloaded that program and ran a HDD test and also one for memory.  I ran GWSCAN 5.12 (I hope that was the right one to run) and there were no errors found.  I ran Memtest 86+ V4.2 and a Windows memory diagnostics test and both of those tests failed really bad.  I am not sure if those were the correct tests to run though.

---

### Post by jocko on 2011-09-17
> **Neomus said:**
> Sorry it has taken me so long to get back to you I have been really busy.  I downloaded that program and ran a HDD test and also one for memory.  I ran GWSCAN 5.12 (I hope that was the right one to run) and there were no errors found.  I ran Memtest 86+ V4.2 and a Windows memory diagnostics test and both of those tests failed really bad.  I am not sure if those were the correct tests to run though.
I'd say the probability of a connection between the install error, windows bluescreens and memtest failures is about 100%... 
Not sure if the "system tweaker" you ran could have caused some hardware damage, or if it managed to change some bios setting or if it's just a coincidence that it happened when it happened.

Check if your bios have any performance settings (cpu or memory overclocking, memory type/latency etc.) that could have been altered (but you'll probably need to know the specs of your cpu and ram to see if anything is wrong).
Otherwise your bios probably have some function to reset to some default settings, or load some failsafe settings that you could try.

If you have more than one ram stick installed you can try removing all but one ram stick and run a memtest. Then remove that stick and install another, run memtest again and so on. If it fails on all sticks, the problem is probably somewhere else (cpu or motherboard), but if it fails only with one specific ram stick, that one is damaged and needs to be replaced.

---

### Post by MAFoElffen on 2011-09-17
> **Neomus said:**
> Sorry it has taken me so long to get back to you I have been really busy.  I downloaded that program and ran a HDD test and also one for memory.  I ran GWSCAN 5.12 (I hope that was the right one to run) and there were no errors found.  I ran Memtest 86+ V4.2 and a Windows memory diagnostics test and both of those tests failed really bad.  I am not sure if those were the correct tests to run though.
So what "I would do" now is to prep the drive and try installs.

- Reboot PC and go into your BIOS... Ensure the points jocko mentioned are kosher- But ensure the hard disk is coming up correctly.

- Boot from the Ultimate Boot LiveCD, do a low level format and verify it... let it mark out any errors.  This will take everything off that drive including the partition table!!!  That is as clean as anyone can get.

-  Boot from a GParted LiveCD, create a partition table and portition your drive.  
 -- Make the first partition NTFS for WIN7 and format it..  "Important"When you create it, move back the start sector one unit and leave that previous sector unallocated.  All the docs on multi=boot sys'es don't say anything about this, but it seems to prevent a lot of problems down the road.  Put this Win partition first, as win OS'es do strange quirky stuff when they are not...
 -- Make an EXT4 and swap partition for Ubuntu and select format.

*** What the above steps do are overkill, but they will prep your drive for a clean install, with steps that will also prevent future problems associated with multi-boot systems.

- Try to install WIN7 in the first partition.

- Try to install Ubuntu in the second partition.  When it gets to the partition menu. Use manual using the partitions you created, using the mount points of / and swap for the respective partitions and selecting the format boxes to reformat the partitions. I know this is a second format, but this will verify that that file system is correct for what is installed..  
 -- Use the try menu item of the LiveCD... then install.  On any error, doing it this way will give you the ability to read/post the syslog (in the /var/log directory) to find where it errored out.

- Tell us how it goes.

---

