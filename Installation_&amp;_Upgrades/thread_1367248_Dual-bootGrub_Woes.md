---
title: "Dual-boot/Grub Woes"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by slimpickens142 on 2009-12-29
Hi All--  Looking for some guidance on a relatively complex issue I'm having. I recently reimaged my ThinkPad and installed Windows XP as the primary OS. Then I installed Ubuntu 9.04 but in my haste I accidentally installed Ubuntu to an external hard drive I had connected to the computer. This mistake resulted in a Grub error unless I had my external HD connected when I booted. 

 I was living like this for a week or two but asked a knowledgeable Ubuntu user at work what the best avenue to remedy would be. He suggested reinstalling Ubuntu to my primary hard drive which should then reinstall Grub to the that hard drive as well. 

 This method didn't go as easy as planned. When I get to the &quot;Prepare Disk Space&quot; of the 9.04 Install and choose my native hard drive, the utility wants to overwrite the whole disk for Ubuntu. I think I could do the manual portion, but really don't want to damage Windows XP. This is what I see when I go to &quot;Manual&quot;: 

 SCSI (0,0,0)(sda) - 120 GB ATA HITACHI HTS54321 
  -Microsoft Windows XP (/dev/sda1) 107.2GB 
  -Windows NT/2000/XP (/dev/sda2) 4.5 GB 

 SCSI7 (0,0,0)(sdb) - 250.1 GB WD 2500 BEV External 
  -/dev/sdb1 - 230.4 GB 
  -Ubuntu 9.04 (9.04) (/dev/sdb5) - 2.3 GB 
  -swap (/dev/sdble) - 172.5 GB 

 (the Windows NT/2000/XP entry is an IBM Rescue & Recovery partition)

 On top of all this, in screwing around with the install CD and booting to Ubuntu from the CD, I must have corrupted the Grub Bootloader because when I tried to boot from my External I get ERROR 21 on loading Grub. 

 Long story short, my machine is a mess. I'm looking for the best avenue to take to get to the end result of an XP/Ubuntu dual boot machine. Do I just format the hard drive and start over by installing XP then Ubuntu? Can I repair and relocate Grub? Should I reinstall Ubuntu and use the manual partition utility? 

 I know there is a lot going on here, I apologize - lot of in's, lot of out's, lot of what-have-you's. But, the dude abides.

   Note: I've already tried #6 in this help doc
 [http://ubuntuforums.org/showthread.php?t=285638](http://ubuntuforums.org/showthread.php?t=285638)

 Note2: I'm a Ubuntu novice, in case that isn't evident enough already, so be gentle...

---

### Post by raymondh on 2009-12-29
> **slimpickens142 said:**
> Hi All--  Looking for some guidance on a relatively complex issue I'm having. I recently reimaged my ThinkPad and installed Windows XP as the primary OS. Then I installed Ubuntu 9.04 but in my haste I accidentally installed Ubuntu to an external hard drive I had connected to the computer. This mistake resulted in a Grub error unless I had my external HD connected when I booted. 

 I was living like this for a week or two but asked a knowledgeable Ubuntu user at work what the best avenue to remedy would be. He suggested reinstalling Ubuntu to my primary hard drive which should then reinstall Grub to the that hard drive as well. 

 This method didn't go as easy as planned. When I get to the &quot;Prepare Disk Space&quot; of the 9.04 Install and choose my native hard drive, the utility wants to overwrite the whole disk for Ubuntu. I think I could do the manual portion, but really don't want to damage Windows XP. This is what I see when I go to &quot;Manual&quot;: 

 SCSI (0,0,0)(sda) - 120 GB ATA HITACHI HTS54321 
  -Microsoft Windows XP (/dev/sda1) 107.2GB 
  -Windows NT/2000/XP (/dev/sda2) 4.5 GB 

 SCSI7 (0,0,0)(sdb) - 250.1 GB WD 2500 BEV External 
  -/dev/sdb1 - 230.4 GB 
  -Ubuntu 9.04 (9.04) (/dev/sdb5) - 2.3 GB 
  -swap (/dev/sdble) - 172.5 GB 

 (the Windows NT/2000/XP entry is an IBM Rescue & Recovery partition)

 On top of all this, in screwing around with the install CD and booting to Ubuntu from the CD, I must have corrupted the Grub Bootloader because when I tried to boot from my External I get ERROR 21 on loading Grub. 

 Long story short, my machine is a mess. I'm looking for the best avenue to take to get to the end result of an XP/Ubuntu dual boot machine. Do I just format the hard drive and start over by installing XP then Ubuntu? Can I repair and relocate Grub? Should I reinstall Ubuntu and use the manual partition utility? 

 I know there is a lot going on here, I apologize - lot of in's, lot of out's, lot of what-have-you's. But, the dude abides.

   Note: I've already tried #6 in this help doc
 [http://ubuntuforums.org/showthread.php?t=285638](http://ubuntuforums.org/showthread.php?t=285638)

 Note2: I'm a Ubuntu novice, in case that isn't evident enough already, so be gentle...


Do you want Ubuntu in the external or do you want it in the internal ... beside XP?

If you've tried to fix the error 21 and no joy, do you want to re-install Ubuntu?

What we'll do next will depend on your answer. 

Regards,

---

### Post by presence1960 on 2009-12-30
> **slimpickens142 said:**
> 

 SCSI (0,0,0)(sda) - 120 GB ATA HITACHI HTS54321 
  -Microsoft Windows XP (/dev/sda1) 107.2GB 
  -Windows NT/2000/XP (/dev/sda2) 4.5 GB 

 SCSI7 (0,0,0)(sdb) - 250.1 GB WD 2500 BEV External 
  -/dev/sdb1 - 230.4 GB 
  -Ubuntu 9.04 (9.04) (/dev/sdb5) - 2.3 GB 
  -swap (/dev/sdble) - 172.5 GB 

 

Your install is no good anyway. You only have 2.3 GB for the Ubuntu / (root) partition. You should make it 10 - 18 GB especially since with that size external disk you have plenty of room. 2.3 GB is not going to allow you to even download any updates as you are almost out of room with just the install on that partition. If you want to keep Ubuntu on the external disk you need to restore windows bootloader to MBR of the internal disk so you can boot windows anytime. Boot the Ubuntu Live CD & choose "try Ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```
Once installed run this command from terminal ```
sudo lilo -M /dev/sda mbr
```

When completed reboot without the Live CD and the external unplugged and you should then be able to boot into windows.

Now we can work on your ubuntu install. You have 2 choices: we can grow your Ubuntu root partition and then install GRUB to MBR of external disk. This will work good because if you boot without the external plugged in you go right to windows. If you boot with the external plugged in you get GRUB and can choose either to boot into Ubuntu or windows.

Or you can partition internal hard disk and install Ubuntu there.

Your choice. Let us know what you want to do and we'll guide you through it.

---

### Post by slimpickens142 on 2009-12-30
Thanks for the quick responses! <br><br>

My ideal setup is to have a dual-booting system using Grub as the bootloader, installed to my primary (internal) hard drive. I would like XP and Ubuntu installed on the primary as well (XP is obviously currently on the primary, I just can't boot to it). I agree about reinstalling Ubuntu; I can probably afford to give it ~20GB. Once installed correctly, I'm planning on using it the majority of the time. My external hard drive I try to use only for music and backup storage. <br><br>

Thanks for your help!

---

### Post by presence1960 on 2009-12-30
> **slimpickens142 said:**
> Thanks for the quick responses! <br><br>

My ideal setup is to have a dual-booting system using Grub as the bootloader, installed to my primary (internal) hard drive. I would like XP and Ubuntu installed on the primary as well (XP is obviously currently on the primary, I just can't boot to it). I agree about reinstalling Ubuntu; I can probably afford to give it ~20GB. Once installed correctly, I'm planning on using it the majority of the time. My external hard drive I try to use only for music and backup storage. <br><br>

Thanks for your help!

Based on your response this is what I would do. First you need to get XP booting. The reason for that is two fold. You don't want to have a non working windows after you install Ubuntu. Secondly you want to boot into XP and back up any files you do not want to lose to the external disk. Then you want to defrag XP at least once, twice would be better. Then you want to disable System Restore and page file until after Ubuntu is installed. This will make resizing XP go smoothly. 

So let's get XP booting first. Boot the Ubuntu Live CD, choose "try ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```

Once lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```
This will fix your MBR of the internal disk so that windows will be able to boot.

I remember you said you are real new. Don't be afraid of terminal. It is the most powerful tool in Linux. Some things can only be done in terminal, and this is one of them. When you type in the commands or better yet copy/paste them into terminal you have to hit Enter once commands are in terminal. Some people will tell you not to use terminal because you are new. That is bolderdash! There is no other way of doing this, other than booting from the windows install disk & runnig Repair- which drops you to a terminal like command prompt. If you are going to use Linux you may as well start learning about it on day one. You will be a more knowledgeable Linux user for doing so.

Once you get windows booting, defragged, System Restore and page file disabled post back and we'll help you install to your internal hard disk.

---

### Post by slimpickens142 on 2009-12-30
Great, thanks! I will try this as soon as I get home from work today. I'm very open to using the command line; I took Unix introduction at work so I have a relative sense of how useful and powerful a resource it can be.

---

### Post by presence1960 on 2009-12-30
> **slimpickens142 said:**
> Great, thanks! I will try this as soon as I get home from work today. I'm very open to using the command line; I took Unix introduction at work so I have a relative sense of how useful and powerful a resource it can be.

Ok, Raymondh or myself should be on here later today and will check back here. good luck!

---

### Post by raymondh on 2009-12-30
+1 on presence1960's suggestion to get windows booting first for 4 very important reasons:

-  back up your files.  Whenever we work on partitions, there are no guarantees
-  need to defrag XP.  *A long time ago, presence1960 taught me that EVEN a clean install of windows can be very fragmented*.  But I digress... this is to give Ubuntu some 'good' space
-  turn of system restore and page filing in order to facilitate the shrinking of XP's partition.  Remember to turn them back on after Ubuntu is installed and settled.
- safely eject the external as well.

Note : XP's disc utility does not shrink partition.  With this, I segue to a question:

Do you want a standard, straight-up, automated install or, do you want to learn/experience MANUAL partitioning/installation.?

**_If automated_** .... (9.04, right?)

-  Boot into the liveCD and proceed to install.
-  in step 4, verify that the proper HD is selected in the upper-right box.
-  Still in step 4, select "side-by-side"
-  Look a little below and [you'll see a slider]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874").  Grab that slider with your mouse and move it to appropriate partition sizes between XP and Ubuntu, noting the numerical changes in the box.  If you don't move that slider, you will end up with the 2.3gb install and your next post will be " how can I enlarge Ubuntu/" ;)
-  Proceed with the install.  GRUB-legacy will be installed in the MBR of that HD.  If you want to double-check, in step 7, click ADVANCED and note where GRUB will be installed.  It should be in the same HD as you had selected above.  You did eject the external, right?

**_If wanting to experience other install method_**s.....

-  Boot into the liveCD and go live session (try ubuntu...)
-  In live session, access gparted (system > admin > partition editor)
-  Double check that the partitions are indeed UNMOUNTED.  Right click on each of them and if given the option to unmount, do so.  For swap, select SWAPOFF.
-  Click to highlight  the XP partition.  It ought to be NTFS formatted.  Make sure you do not click-highlight the 'recovery' partition.
-  Once highlighted, select RESIZE.  Grab the right border and drag left to create a unallocated space (we're shrinking XP now).  How much is your choice but to suggest, give Ubuntu at least 15gb.
-  Review and click APPLY
-  Exit gparted (yes, leave it unallocated) and proceed to install.
-  In step 4 of the install process, select "largest continuous free space" which should be that recently created Unallocated space.
-  Again, GRUB ought to install in the MBR of the HD.   You did eject the external right?

**_If wanting to experience a full-manual install with a seprate /home_**.....

-  Boot into the liveCD and in live session, access gparted.
-  Shrink XP to give Ubuntu say 35GB, review and apply
-  Click on the unallocated space and select NEW (we're going to create 3 partitions and then install unto them).  Select EXTENDED .... Review and Apply.
-  Click on the newly created EXTENDED partitions and select NEW.  Choose LOGICAL. Make the size 2000mb (2gb).  Format LINUX SWAP FILESYSTEM.  Review and Apply.
-  Click again on the newly created EXTENDED partition and select NEW > LOGICAL > size about 10GB > Format Ext3 or Ext4 > select mountpoint **/** (which is known as root) > Review and Apply
-  Click, again, on the Extended partition > NEW > Use remaining space > format Ext3 or Ext4 > select mountpoint /home > Review and Apply.
-  You ought to have a EXTENDED partition which has 3 LOGICAL partitions inside it.  Exit gparted and proceed with the install.
-  In step 4, select Manual.
-  In the next window, click to highlight the 2gb partition.  Click EDIT button > USE AS > SWAP
-  Click to highlight the 10gb partition you created > EDIT > USE AS > format ext3 > scroll and select the mountpoint **/**
-  Click to highlight the remaining partition > EDIT > USE AS > FORMAT ext3 or Ext4 > mountpoint **/home**
-  Proceed with the install.

Whew.  Post back if you need further clarification.

Remember ... Get windows booting and back-up.

Regards

---

### Post by slimpickens142 on 2009-12-31
Thanks for all the information! 

Presence, your instructions worked like a charm!

So I have now defragged my primary hard drive twice and then made a full backup of my system, so I think I'm ready for the Ubuntu install. I will temporarily turn of system restore and page filing in XP as Raymondh has recommended. Should I just go ahead with Raymondh's instructions for the automated install?

Also, I booted without my external hard drive connected. Should I just format the Ubuntu 9.04 and swap partitions? What will be the easiest way to do so?

---

### Post by presence1960 on 2009-12-31
> **slimpickens142 said:**
> Thanks for all the information! 

Presence, your instructions worked like a charm!

So I have now defragged my primary hard drive twice and then made a full backup of my system, so I think I'm ready for the Ubuntu install. I will temporarily turn of system restore and page filing in XP as Raymondh has recommended. Should I just go ahead with Raymondh's instructions for the automated install?

Also, I booted without my external hard drive connected. Should I just format the Ubuntu 9.04 and swap partitions? What will be the easiest way to do so?

Glad that worked out for you.

My friend Raymond gave you excellent options for installing. I would proceed.

After Ubuntu is installed to internal then I would plug in the external and format & partition it as your needs dictate.

---

### Post by grubdude on 2009-12-31
**_Presence1960_**: I don't want to highjack this thread but would you be able to shed any light on my original post on a similar topic?
[SIZE=3][FONT=Calibri]Hi,[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Does anyone have reliable experience working with the new Linux grub version 2, at all? I am trying to dual boot opensolaris with Ubuntu 9.10 and it is more tricky to edit the new version Linux grub menu versus the old. I don't want to trash my install in the process....[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Unfortunately, I installed [COLOR=black]Opensolaris[/COLOR] first and then Linux, so the grub menu is showing from Linux and boots into Linux only. It might have been better to install [COLOR=black]opensolaris[/COLOR] second and modify its grub to see the Linux install. unfortunately ZFS and EXT4 file systems don't talk very well to each other....[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am fairly new to Linux/Unix so if you know a definite way to do this can you please put the exact lines etc. that need to be added to the grub2 menu to recognize [COLOR=black]opensolaris. Would prefer not having to reinstall both OSs.[/COLOR][/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Have 80gb hd on notebook split in half..First partition is [COLOR=black]opensolaris,[/COLOR] second is Ubuntu 9.10 with included swap file. Thanks.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Really don't want to hose either install with my lack of experience. Thanks in advance!:wink:[/FONT][/SIZE] 
 
[FONT=Calibri][SIZE=3]Alternatively, is there any way to use the opensolaris live cd to boot into the installed opensolaris 2009.06 on my hard drive? I would settle for this as a temporary texchnique too. Thanks and Happy New Year![/SIZE][/FONT]

---

### Post by raymondh on 2009-12-31
> **slimpickens142 said:**
>  What will be the easiest way to do so?

Using the slider is the easiest.  A Manual install may be daunting at first ... but the experience will be worth it :)

If you have an old, spare machine ... I recommend you download and burn a live gparted CD and use it on the 'old' machine.  Just see what it can do, etc, etc.

Best wishes ... happy new year.

---

### Post by raymondh on 2009-12-31
> **grubdude said:**
> **_Presense1960_**:  
 
[FONT=Calibri][SIZE=3]Alternatively, is there any way to use the opensolaris live cd to boot into the installed opensolaris 2009.06 on my hard drive? I would settle for this as a temporary texchnique too. Thanks and Happy New Year![/SIZE][/FONT]

Cannot say much about opensolaris vis-a-vis ubuntu so I hope this can help.

I am able to get my OSX to work with GRUB by installing the OSX bootloader in the OSX partition and GRUB in the MBR of the HD.  Grub controls the boot but, when you select OSX, it will segue into Darwin.

Maybe, just maybe, you can re-install opensoloaris' bootloader in the opensolaris partition and then .... chainload that to GRUB (since GRUB is already in the MBR).

Just a thought .... 

Happy New Year :)

---

### Post by grubdude on 2009-12-31
Raymondh,
 
Thanks for the response. I am fairly new to this(unix/linux) so I am a little hesitant to hose both installs....Right now it boots directly into Ubuntu 9.10 and does not even know Solaris exists on the first partition.
 
Probably would have been easier to install Ubuntu first, boot into opensolaris and modifu grub to see Ubuntu, but I didn't. Besides this will be more of a learning experience, if I can get someone with specific info on what to try....
 
Thanks for the feedback and Happy New Year!

---

