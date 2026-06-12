---
title: "Install Ubuntu 11.04 64 bit and Lose Win 7"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by windjammer66 on 2011-04-25
[SIZE=2]I have a 64 bit Emachine 2 weeks old.  It has a 250GB HDD with 4GB memory and speed is 3.1 GHz.  I tried the live 11.04 64 bit version.  I like Ubuntu as I have had several earlier 32 bit versions.  On my old 32 bit computer I installed the OS without problem.  So I went ahead and did the install of the 64 bit on my new computer.  It installed in about 12 minutes.  I was expecting the install to be longer based on previous installs[/SIZE].

[SIZE=2]I chose to install Ubuntu side-by-side and made my partition sizes and the other information asked at the beginning.  When the install was done the program said to reboot which I did.  What I saw when it started to boot up again is a window that moves around and says in the window "Input not Supported".  This lasted a few seconds and then Ubuntu starts up.  I don't get the Grub boot loader.

So I have lost my windows partition or can't access it for some reason and I have no boot loader.  I hope someone can help me.  I really like Ubuntu but I wasn't ready to lose Windows 7  either.

Thank you
[/SIZE]

---

### Post by Bucky Ball on 2011-04-25
Welcome.

If you hit shift (might be escape) at boot does that bring up grub?

Also, 10.04 LTS is the current, stable long-term support release. If you are going for 11.04 I would try 10.04 instead. Smoother ride for a newcomer. ;)

---

### Post by windjammer66 on 2011-04-25
> **Bucky Ball said:**
> Welcome.

If you hit shift (might be escape) at boot does that bring up grub?

Also, 10.04 LTS is the current, stable long-term support release. If you are going for 11.04 I would try 10.04 instead. Smoother ride for a newcomer. ;)

Thanks Bucky Ball,  All that happened is that after the window traveled around the screen for a few and pushing Esc several times it finally did something and went to the login screen.

How can I go back to an older version?  Will that help restore my windows?  Is there a 64 bit 10.04?  The last version I used was 10.10 32 bit.  As you can tell I am not an expert.  I guess I know enough to get me in trouble.  Although I wasn't expecting problems.  I've used beta programs before but did not have problems.

---

### Post by Bucky Ball on 2011-04-25
Choose 10.04 LTS 64bit from here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Torrent is the most reliable but there seems to be no AMD64bit Desktop there (which is odd):

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

That is not really a problem. You can torrent down the alternate 64bit installer (top of list), the only difference is that it's a text based installer rather than the colourful desktop disco installer. ;)

Also, if you boot from the desktop CD you already have, choose 'Try Ubuntu' without installing, get to a desktop, select System>Administration>Partition Editor (or Gparted if it's called that) and have a look at your partitions. If you still have and NTFS partition then Windows is still there.

---

### Post by Mark Phelps on 2011-04-26
> **windjammer66 said:**
> [SIZE=2][SIZE=2]I chose to install Ubuntu side-by-side and made my partition sizes and the other information asked at the beginning.
Unfortunately, that can lead to Win7 OS filesystem corruption when the Ubuntu installer resizes the Win7 OS partition.  You should have used the Disk Management utility in Win7 to shrink the Win7 OS partition.

>   When the install was done the program said to reboot which I did.  What I saw when it started to boot up again is a window that moves around and says in the window "Input not Supported".  This lasted a few seconds and then Ubuntu starts up.  I don't get the Grub boot loader. Haven't seen this, sorry.

> So I have lost my windows partition or can't access it for some reason and I have no boot loader.  I hope someone can help me.  I really like Ubuntu but I wasn't ready to lose Windows 7  either.
As Bucky Ball has already said, check your partitions to ensure that NTFS partition(s) are still in place.  My guess is that they are.

Since you probably did NOT use the Win7 Backup feature to create and burn a Win7 Repair CD before you installed Ubuntu, go to the link below, select the proper Win7 version, download and burn a Win7 Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

You can then boot from that and run Startup Repair (may have to run it three times) to get Win7 booting again.

Also, once back into Win7, I would run chkdsk to clean up the filesystem.

---

### Post by windjammer66 on 2011-04-26
Ok I will follow your advice, Mark.  Thank you for your help.  I am going to wait for the final release of 11.04 which is this Thursday.  I could not boot from the CD after I burned it when I was in Windows.  I had to install files per directions from Ubuntu.  So I will get the final release and hopefully it will boot on its own so I can check the partitions.

---

### Post by Bucky Ball on 2011-04-26
> **windjammer66 said:**
> Ok I will follow your advice, Mark.  Thank you for your help.  I am going to wait for the final release of 11.04 which is this Thursday.  I could not boot from the CD after I burned it when I was in Windows.  I had to install files per directions from Ubuntu.  So I will get the final release and hopefully it will boot on its own so I can check the partitions.

Not sure if your problem will be fixed in the final release (as it is tomorrow my time). As suggested, I'd wait a couple of months. ;)

---

### Post by windjammer66 on 2011-04-27
> **Bucky Ball said:**
> Not sure if your problem will be fixed in the final release (as it is tomorrow my time). As suggested, I'd wait a couple of months. ;)

Hi Bucky, I went into bios and made the cd drive boot first.  I made the Repair Disc per Mark Phelps but it did not help. The first time Startup Repair did detect win 7 and it seemed like it was doing something but the second time I ran it it quickly said that it could not find a problem.  I tried System Restore, too.  No effect.  So I put the Ubuntu CD in the drive and went to the Live setup.  I went to G-parted and I do have my partitions and there are smaller partitions, it looks like, which might be swap files.

I have been doing more research and I found that there is a problem with Grub 2 in WUBI?  If it is updated too soon it can screw things up.  Something like that.  The install should be a manual one, maybe.  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

This leads up to a question that I was wondering about: Can the Ubuntu OS be installed over the Ubuntu OS already on the computer to maybe fix a problem like this? 

I remember selecting to update the OS as it was being installed with current packages, I think.  
Anyway, waiting 2 or 3 months is a good idea.

Thanks for your help,

---

### Post by Bucky Ball on 2011-04-28
Wubi? I thought you were attempting to get your dual-boot working with Ubuntu on its own partition, NOT inside Windows.

Wubi is really not designed for long term use; it is more about trying about Ubuntu for awhile to see if you like.

---

### Post by Mark Phelps on 2011-04-28
> **windjammer66 said:**
> I made the Repair Disc per Mark Phelps but it did not help. The first time Startup Repair did detect win 7 and it seemed like it was doing something but the second time I ran it it quickly said that it could not find a problem.
Sorry to hear that; unfortunately, the MS solution does not always work.  If you still want to repair Win7, suggest you check the Windows 7 forums (sevenforums.com), their Installation section, where they have tutorials with stuff you can try in Command Mode, to repair your Win7 boot.

>   I tried System Restore, too.  No effect. 
Not surprised because that's not really designed to fix boot problems -- especially if the boot files are in a separate partition (the default in preinstalled Win7 PCs). 
> So I put the Ubuntu CD in the drive and went to the Live setup.  I went to G-parted and I do have my partitions and there are smaller partitions, it looks like, which might be swap files.
You should go into an Ubuntu terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results here.  Without seeing your partition setup, it's hard to offer specific advice.

> I have been doing more research and I found that there is a problem with Grub 2 in WUBI?  
Where did Wubi come from?  Didn;'t see anything in your earlier posts about Wubi!  A Wubi install does NOT use its own partition, does NOT install GRUB, and creates a file that exists entirely within a Windows NTFS partition.

> This leads up to a question that I was wondering about: Can the Ubuntu OS be installed over the Ubuntu OS already on the computer to maybe fix a problem like this? 
Having avoided Wubi like the plague, I'm not the best person to answer the question.

> I remember selecting to update the OS as it was being installed with current packages, I think. If I had a dollar for every thread I've read over the years in which updating a Wubi install trashed the PC and/or Ubuntu, I could have retired long ago!  So, if it WAS working and you did an update -- that could have been the cause of all of your troubles.  

> Anyway, waiting 2 or 3 months is a good idea.

Yes , it is -- as it gives you a chance to monitor the forums about NEW problems resulting from 11.04 installation.  And, as you can see, they're starting to pour in!

---

### Post by chrisandlouise on 2011-04-28
i had this problem with my desktop, there are directions on how to edit grub loader to bring back windows,  boy was i happy when i figured it out, it only happens on 64 bit system, i cant remember where in the forums the info is but it is there, i hope this helps
some guy made a small piece of code that you run that fixes the broblem

---

### Post by windjammer66 on 2011-04-30
> **Mark Phelps said:**
> Sorry to hear that; unfortunately, the MS solution does not always work.  If you still want to repair Win7, suggest you check the Windows 7 forums (sevenforums.com), their Installation section, where they have tutorials with stuff you can try in Command Mode, to repair your Win7 boot.


Not surprised because that's not really designed to fix boot problems -- especially if the boot files are in a separate partition (the default in preinstalled Win7 PCs). 

You should go into an Ubuntu terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results here.  Without seeing your partition setup, it's hard to offer specific advice.


Where did Wubi come from?  Didn;'t see anything in your earlier posts about Wubi!  A Wubi install does NOT use its own partition, does NOT install GRUB, and creates a file that exists entirely within a Windows NTFS partition.


Having avoided Wubi like the plague, I'm not the best person to answer the question.

 If I had a dollar for every thread I've read over the years in which updating a Wubi install trashed the PC and/or Ubuntu, I could have retired long ago!  So, if it WAS working and you did an update -- that could have been the cause of all of your troubles.

**Thank you all for your help!!!**  There may be ways to undo the mess I made and hearing about what a little check box can do makes me realize that Hey! I AM using Ubuntu 11.04 AND I have just updated my driver for the graphics card and I now have Ubuntu 3D and that is really cool.  I am staying with Ubuntu full time.  It's about time I left Windows.  I love the security of Ubuntu and hated the constant updating of Windows and the virus checkers and malware checkers...ad nauseum.   :D 


Yes , it is -- as it gives you a chance to monitor the forums about NEW problems resulting from 11.04 installation.  And, as you can see, they're starting to pour in!
k

---

