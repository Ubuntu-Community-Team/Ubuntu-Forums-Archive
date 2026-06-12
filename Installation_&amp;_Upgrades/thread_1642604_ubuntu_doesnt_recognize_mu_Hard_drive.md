---
title: "ubuntu doesnt recognize mu Hard drive"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by coyotemk on 2010-12-10
Hi everyone, 
I've bought new PC, and installed win 7 first. Then i've resized my disc and left the half of it unallocated for my ubuntu. But the ubuntu installer doesnt see my hard disk. when i run fdisc -l, the only thing that i see is my usb from wich i'm booting. I know that this is a common problem, searched for help on the web for hours and nothing worked. I've tried to remove dmraid, i saw that this could be a source of my pb, but i have errors and it is still here.  

Any ideas???
edit: 
i've just tryed the bootinfo script, same results. .... i've eve event tested to connect my HD to diff sata ports... no results.

---

### Post by Quackers on 2010-12-10
How many primary partitions are there on your machine and how did you resize the partition(s)?

---

### Post by coyotemk on 2010-12-10
I've used Magic Partition, and there is 2 ntfs partions. One is with the OS, and the other one win 7 made it by him self, a backup partition.

---

### Post by lmarmisa on 2010-12-10
Try to access to the BIOS menu and check if some RAID controller is enabled.

---

### Post by coyotemk on 2010-12-10
Checked since the star :)

---

### Post by Quackers on 2010-12-10
If you are not using raid, or the disc has never been part of a raid array,
I would suggest that you have a look at the site below and run chkdsk on the C: drive until no errors are reported.

[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

If that runs ok, would you please post a screenshot of your Windows Disk Management screen (Start > right-click Computer and select Manage > select disk management)
Thanks.

---

### Post by coyotemk on 2010-12-10
The test went ok. here are the results.
Only one thing, i used Minitools Partition Wizard Home Editio and not Magic Partition

---

### Post by Quackers on 2010-12-10
That's good :-)
Can you post a screenshot of your Windows disk management screen please?

---

### Post by coyotemk on 2010-12-10
Windows disk management? what do u mean by that? 
sorry it's been a long time since i used windows :)

---

### Post by Quackers on 2010-12-10
Start > right-click Computer and select Manage > select disk management

---

### Post by coyotemk on 2010-12-10
here it is. 
I saw something unusual with Minit tool Partition. In the second screenshot using mini tools, on my drive B, as status he has Active and Boot. Is it normal?

---

### Post by Quackers on 2010-12-10
Yes, that's fine. 2 of Windows' boot files will be in there.

As I'm not sure you have seen my earlier post I would ask you to confirm that you are not using a raid array, and that your main hard drive has never been part of a raid array. Also that you have just one hard drive approximately 1TB.

---

### Post by coyotemk on 2010-12-10
as i said i bought my computer few days ago, and it is my only disk ,1T, that i bought at the same time. I've double checked in the bios and the raid mode is IDE. 
My disk is plugged in on 6Gb/s controller, and i thought that if i change it to a 3Gb/s controller i wont have this pb. But when i did that, my system couldnt detect my disk... dont know why.... if that can help

---

### Post by Quackers on 2010-12-10
Ok thanks.
I know it is a pain, but could you try the installer again and see if your drive is now recognised. Sometimes a chkdsk run on the Windows drive can fix it.
Did you choose IDE? I would have thought that most modern hardware uses AHCI now. Don't change it though!

---

### Post by coyotemk on 2010-12-10
yeaaahh it is a pain :) i've spent my last 10H on this :), but i'm used to things like this:)
No, it wasnt me that chose the IDE, it was set by default; and i have the option AHCI. 
With the installer nothing  has changed

---

### Post by Quackers on 2010-12-10
I'm sorry but I am having serious problems navigating around the forum tonight. I've lost posts and can't get to some threads at all. I'm about to give up for tonight.
My more recent machines have all used AHCI.
BUT changing from IDE to AHCI can lose you your oparating system (or it could do at one time). I'm going to have to leave this to someone else for tonight. What you can do is Google around looking for confirmation about changing to AHCI (in case you decide to do that). 
There are many knowledgable people here that will help you. In fact one or two may be along shortly.
Good luck :-)

---

### Post by Quackers on 2010-12-10
I'm back :-) Trying IE to see if my problems are caused by Firefox.
There is some interesting reading here 
[http://www.sevenforums.com/installation-setup/29089-change-ide-ahci-bios-much-better-performance-3.html](http://www.sevenforums.com/installation-setup/29089-change-ide-ahci-bios-much-better-performance-3.html)

---

### Post by coyotemk on 2010-12-10
if u want to switch to ACHI mode, here is a usefull link:
[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)
and it works !

... but it didnt solve my problem ....

---

### Post by Quackers on 2010-12-10
That's basically the same thing as post #7 in the link I gave.
But it didn't solve your problem? Did you change to AHCI in your bios too?
I have asked another member to take a look at your problem, but I don't think he is online at the moment.

---

### Post by coyotemk on 2010-12-10
It's ok, my problem is solved :)
I've pluged in my HD to an other PC, and reformated it to ext4. plugged in to my new PC and it worked :). F**k windows ... it gives u only troubles :)
I think that the problem was something with the partition table (.. i cant see nothing else)

Anyway 10x a lot man, i appreciate your help. 
have a good night

---

### Post by Quackers on 2010-12-10
That's good news :-)
Sometimes when a Windows partition is resized by a non-Windows partition program Windows baulks at it. I was hoping the chkdsk would have worked it out, but apparantly not. It may well have been a partition table problem.
Nice one :-)

---

