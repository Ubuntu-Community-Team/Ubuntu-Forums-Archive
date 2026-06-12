---
title: "Cant duel boot windows 7 and ubuntu 11.04"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by thomas07vt on 2011-11-15
so here is my situation, 
 
i currently have Windows 7 on my computer and i want to set up a duel boot setup to ubuntu 11.04. I have a ubuntu installation dvd. I have actually tried this at least three times with no success.
 
I create a hdd partition using the standard windows partitioning tool and leave the partition as 'unused' so its not formatted.
 
i restart my comp with the ubuntu dvd and it loads ubuntu correctly, and i select install ubuntu 11.04.
 
so only once did i get the option of doing "install along side window"
 
how do i get that option to appear? i feel like it has to do with how you partition (or dont partition perhaps?)
 
thats not that important, as i can just do the other option that lets me install it along side windows manually... but i am just curious.
 
so i use the unallocated space, delete it so its free space, and then split up the free space (200 gigs about) and create a 16 gig swap and i split up the rest between the home partition and root partition. (not really sure what these are specifically used for so i just split it up)
 
and i install it correctly, 
 
so i reboot my computer and i can boot into ubuntu but i cannot boot into windows... it goes to the loading windows page (so i would think that its not an issue with the boot loader) but then it freezes or gets a blue screen of death.
 
any ideas?

---

### Post by thomas07vt on 2011-11-15
could it be that i do not create a partition at the beginning of my hdd for linux?

---

### Post by darkod on 2011-11-15
Because it doesn't sound that you were resizing your windows partition with ubuntu, it should be fine. Very strange that win7 doesn't boot.

Can you boot ubuntu and follow the link in my signature to download and run the bootinfoscript? Post the results here as explained in that link. That should show more information.

---

### Post by deltacomp on 2011-11-15
Sound to me as if some of the files got deleted from windows. In my experience with windows, windows tends to install files all over the place within the HD. 

Have you tried booting from the windows disk and going through the process of repairing the installation?

Another option would be to reinstall windows from the backup it makes of itself. 

Hope this helps. :)

---

### Post by Mark Phelps on 2011-11-16
You didn't mention having a Win7 DVD .. so I'm going to presume that you do NOT have a Windows disk with which you can do repairs, right?

From what you and others have said, it doesn't look like a simple boot failure, as it simply would not boot, and you wouldn't get far enough to get a Blue Screen.

Ordinarily, shrinking your Win7 OS partition using Win7 Disk Management will not result in problems, but I didn't see where you did that, and even if you did, you should then have rebooted into Win7 a couple of times to allow it to do any filesystem adjustments from the shrinkage.

If you want to experiment (this probably will not work, but it MIGHT), go to the link below, download and burn the Boot-Repair CD, boot from it, and see if it will repair Win7 enough to get it working:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I'm only suggesting this because, apart from a blank CD, this is basically a FREE option.

If that doesn't work, and you're willing to spend around $10 USD, then you can go to the link below, download and burn the appropriate Win7 Repair CD image, and try that:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Again, that might not work, and this time, you have to spend some money.

But, using that Repair CD, you can also boot into a command line.  Once there, enter the following:

> sfc /scannow 

That will run a file integrity check on your Win7 OS, and should repair or replace any missing or damaged system files.

If that doesn't work, then you're looking at a reinstall of Win7.  Presuming it came preloaded, there should be a key combination that you can use to Restore it to its original condition -- but be aware that will erase your hard drive, removing everything currently there.

So, another option is a Repair Installation of Win7 -- but you need a Win7 DVD for that (any version will do, you can "borrow" one from someone else) -- and the instructions for doing this are on the Win7 forum: sevenforums.com.

Good Luck

---

### Post by thomas07vt on 2011-11-16
so i have a system image of my harddrive on an external, and a windows 7 disk that allows me to use that image to restore my CPU, so currently I actually only have windows 7 on my machine, as i already did a restore from that image after windows would not start. So i cant try to repair windows at this time.
 
I just shrinked my c drive and have restarted several times and am planning on trying ubuntu tonight, so If i have the same issue then i will try some of the things listed here. I think before i just rebooted my computer once after shrinking my hdd, so maybe that was it. I just didnt give it enough time to remove all the files form the unallocated space. I also unchecked 'allow write cache' or something like that on the unallocated space, so maybe that make it truely unallowcated.
 
thanks for all the ideas,
Ill keep you posted if it continues to mess up.

---

### Post by Mark Phelps on 2011-11-16
OK, so BEFORE it messes up ... use the Win7 Backup feature to create and burn a Win7 Repair CD.  You can use this to repair boot problems and to run diagnostics on Win7.

With any luck, you won't need this -- but it is better to have it and not need it, than to need it and not have it.

---

