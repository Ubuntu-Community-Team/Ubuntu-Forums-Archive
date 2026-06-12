---
title: "NooB help with grub"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Cougcoupe on 2009-12-09
Ok, So I installed Ubuntu on a seperate hard drive, dual bootinging Vista from one hard drive, and Ubuntu 9.10 from the other. Well, for the time being I decided to uninstall Ubuntu because I'm getting my toys in order for a new computer build later this month and I'm using the extra 750 GB that Ubuntu was on for the new comp.
 
So through windows disk manager I simply reformated the 750 GB. All was good til the next morning when I booted up my computer. Grub starts to load then gives me an error. I belive it says Grub Recovry or something like that but won't do anything(I'm at work right now and only had a few minutes to play with it this morning). It lets me use command prompt but I don't know what to type in. I tried exit C:\windows, run, startup, things I remembered from the days before before GUI. 
 
So....Is there anyway to boot into windows from here. (I have the windows vista install disk as I built the computer my self, no recovery disk).
 
If so....Once I'm there, how to I get ride of grub so I don't have this problem.
 
And...any other bits of knowledge on the situation would be helpful. 
 
If I'm leaving out any info yall might need let me know.
 
AMD Phenom QC
64 Bit Vista Home Basic
And had Ubuntu 9.10 32 Bit
 
Free six pack to the first person to help me. I'll fedex it right over. Thanks in advance.

---

### Post by darkod on 2009-12-09
Because from the description it's not clear whether grub2 was on your ubuntu or windows disk, first thing to do is go into BIOS and set the windows disk as first in boot order.
See if that boots vista. If yes, problem solved.
If not, leave that selection in BIOS, your windows disk should be first in boot order. But boot with the vista dvd and after the language selection screen on the next screen at the bottom there should be Repair This Computer. Follow the instructions and it should find and restore your vista bootloader on the MBR of the disk.
If that still doesn't work, there are manual commands to try that but lets wait for the automatic method results first.

---

### Post by phillw on 2009-12-09
> **Cougcoupe said:**
> Ok, So I installed Ubuntu on a seperate hard drive, dual bootinging Vista from one hard drive, and Ubuntu 9.10 from the other. Well, for the time being I decided to uninstall Ubuntu because I'm getting my toys in order for a new computer build later this month and I'm using the extra 750 GB that Ubuntu was on for the new comp.
 
So through windows disk manager I simply reformated the 750 GB. All was good til the next morning when I booted up my computer. Grub starts to load then gives me an error. I belive it says Grub Recovry or something like that but won't do anything(I'm at work right now and only had a few minutes to play with it this morning). It lets me use command prompt but I don't know what to type in. I tried exit C:\windows, run, startup, things I remembered from the days before before GUI. 
 
So....Is there anyway to boot into windows from here. (I have the windows vista install disk as I built the computer my self, no recovery disk).
 
If so....Once I'm there, how to I get ride of grub so I don't have this problem.
 
And...any other bits of knowledge on the situation would be helpful. 
 
If I'm leaving out any info yall might need let me know.
 
AMD Phenom QC
64 Bit Vista Home Basic
And had Ubuntu 9.10 32 Bit
 
Free six pack to the first person to help me. I'll fedex it right over. Thanks in advance.

Hi, as Ubuntu is no longer in charge - you want to revert the MBR back to Win control. Doing that is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You'll be wanting this bit

> [SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download").
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

 	Code:
 	bootrec.exe /fixboot 
 	Code:
 	bootrec.exe /fixmbr 
Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader. 		                   		  		  		 		 			 				

Regards,

Phill

---

### Post by Cougcoupe on 2009-12-09
> **darkod said:**
> Because from the description it's not clear whether grub2 was on your ubuntu or windows disk, first thing to do is go into BIOS and set the windows disk as first in boot order.
See if that boots vista. If yes, problem solved.
If not, leave that selection in BIOS, your windows disk should be first in boot order. But boot with the vista dvd and after the language selection screen on the next screen at the bottom there should be Repair This Computer. Follow the instructions and it should find and restore your vista bootloader on the MBR of the disk.
If that still doesn't work, there are manual commands to try that but lets wait for the automatic method results first.
 
 
I tried using BIOS to select my Windows harddrive to boot first but still went back to grub.  Haven't tried the repair yet.  I'll try that in a few hours when I get home then reply back.

---

### Post by Cougcoupe on 2009-12-09
> **phillw said:**
> Hi, as Ubuntu is no longer in charge - you want to revert the MBR back to Win control. Doing that is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
You'll be wanting this bit
 
 
 
Regards,
 
Phill
 
 
Thank you for the reply, I was sure the answer was probably somewhere around here.  Just couldn't see to find it.

---

### Post by Cougcoupe on 2009-12-09
Thank you for the tips, it worked.

---

### Post by phillw on 2009-12-09
> **Cougcoupe said:**
> Thank you for the tips, it worked.

>  Free six pack to the first person to help me. I'll fedex it right over. Thanks in advance.

3 for me and 3 for dark - lol

Yeah, they can take a bit of finding - when you come back to Ubuntu, set up a Ubuntu folder in bookmarks in your FFox & store those links in it. Handy for you & handy to pass onto others who ask.

Regards,

Phill.

---

