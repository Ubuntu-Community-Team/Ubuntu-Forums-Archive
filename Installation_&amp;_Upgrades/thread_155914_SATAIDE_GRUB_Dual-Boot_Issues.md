---
title: "SATA/IDE GRUB Dual-Boot Issues"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by Roger Mudd on 2006-04-06
I recently had some issues with an Ubuntu/XP dual boot install that required a fresh install of XP and removing Ubuntu from my system :-(
A little background:
I have two internal hard drives - a 160 GB SATA drive (C) and a 60 GB IDE drive  (F). I had installed Ubuntu on a 25 GB partition on C. Unfortunately, I was unable to boot into XP after installing Ubuntu and I was forced to start with a clean slate and wipe C altogether.
On my first attemp to reinstall XP it actually reassigned the SATA drive to F and the IDE drive to C. I believe this is because the IDE drive shows up first in the BIOS (which I don't believe I can change). In order to get the XP onto C, I had to disconnect the IDE drive and then install. That worked, XP is now on C :-)
Unfortunately, when I reconnect the IDE drive and attempt to reboot it presents a GRUB error and forces me into an endless cycle of manual reboots.
If at all possible, I would like to eradicate this problem without altering the existing data on the IDE drive (used for secondary backup previously). Any ideas as to how I can reconnect the IDE drive and successfully boot into XP without any intervention from GRUB? Is there a way to remove GRUB from my system altogether? I looked into editing XP's boot.ini file, but I don't want to get too far ahead of myself. That's what got me into this mess in the first place ;-)
Any help is greatly appreciated!

---

### Post by Herman on 2006-04-06
I suggest you try out GAG Boot Manager and install Lilo to your Ubuntu partition, or re-install GRUB to your Ubuntu partition or a boot partition, (but not to MBR), this time. For instructions, [click here]("http://users.bigpond.net.au/hermanzone/p12.htm").
Good luck, from herman :D

---

### Post by Roger Mudd on 2006-04-06
Thanks for the response Herman. I also wanted to thank you if the link you provided is one to your own web site. I used that extensively in setting up my original dual-boot installation. Needless to say, the problems were caused by user error and not your excellent advice.
As to your suggestion above... Unfortunately, Ubuntu is no longer installed on the system. C is now a single-partition NTFS drive housing my XP installation. F is a single-partition NTFS drive housing some old backup-data (if I could hook it up).
That's why I found the GRUB error message confounding. I no longer have Linux installed on my machine. Are you implying that GAG Boot Manager will help me rid myself of any reference to GRUB? It seems to me that GRUB or LILO is required to run GRUB. If that is the case, I'm not sure I want to go down that road. I would like to rid myself of anything but the default XPM BR if at all possible.

Roger

---

### Post by spandon on 2006-04-06
Hi Roger Mudd,
You will find that grub has taken over your mbr of your windows drive, to remedy this you need to re write your **mbr.**
to do this, put your Windows XP disk in your cd/dvd drive and reboot.
let the windows disk setup your system and come up with the screen asking you if you wish to install or repair.
Choose R (repair), choose the windows drive, then enter at the prompt** fixmbr**, you will now get a warning - ignore this and answer yes, you will then get a message stating that your **mbr** has been renewed.
This will alow you to boot up into XP as normal
Don

---

### Post by Roger Mudd on 2006-04-06
Thanks for the tip spandon! One quick question:
If I can boot into XP without the IDE drive connected doesn't that imply that the issue is on that IDE drive and not on the SATA drive (C/XP)? Shouldn't the MBR be stored on the SATA drive (C)? I wonder if these drives are sharing an address (for example - hd 0,0) and that they will boot independent of each other (well... at least the SATA drive with XP) but not when installed concurrently? Is that a possibility? If so, how would one go about diagnosing and fixing such an error?
Thanks again!

---

### Post by Herman on 2006-04-06
> On my first attemp to reinstall XP it actually reassigned the SATA drive to F and the IDE drive to C. I believe this is because the IDE drive shows up first in the BIOS (which I don't believe I can change). In order to get the XP onto C, I had to disconnect the IDE drive and then install. That worked, XP is now on C :smile:
Unfortunately, when I reconnect the IDE drive and attempt to reboot it presents a GRUB error and forces me into an endless cycle of manual reboots. 
Hello again, Roger, it wouldn't have anything to do with your hard drive's jumper settings would it? Your BIOS should be looking for a boot sector on the first track of the first hard disk, so whichever is jumpered as the first hard disk would be the one that gets booted. What is happening in your BIOS when you plug in or remove each hard drive/ (How are they listed each time?)
Sorry for the misunderstanding earlier, I thought you wanted to reinstall Ubuntu but didn't like GRUB and wanted to avoid editing  boot.ini too.  GAG would have worked for that, and/or for overwriting GRUB from your MBR as well, but if it isn't your preference then there's no point.
Regards, Herman :D

---

### Post by spandon on 2006-04-06
Hi Roger Mud
If you are still having trouble with your ide drive, then disconnect the sata drive and and leave the ide connected, repeat the mbr renewal as described ealier.
Then reconnect both drives and test again.
If the problem persists, then check your bios :
(a) to check if bios is reading both drives, if so
(b) check boot sequence, and if possible change the boot hd to the one with XP on,
Sorry, if this doesnt work, then it may be something else, I to had problems with my mixture of Sata and ide drives, but wasa able to resolve my problems as described above.
Hope this helps you?
Don

---

### Post by Vlatko on 2006-04-18
i have a similar situation. i have one sata drive with windows on it, one ide drive with all my personal stuff on it and i have just added a third drive with ubuntu on it. however i am having some problems.

1. after adding the new drive with linux the start up time is MUCH longer in windows. all programs load and i can click on the my computer icon but then i have to stare at the rotating flashlight for about 2 minutes till the system gets a hang on itself.

2. after it has loaded i can see my 2 drives, one with windows the other with all my personal stuff BUT i can't see the new third drive which has linux on it. i can see it is listed and working properly in the device manager but not in my computer.

3. i wanted to see if the slow startup is fixed after i unplug my new added drive but then windows will not boot. the GRUB thing starts but gets an error 17. i have to plug in my new hard drive and select windows from the grub option menu. 

is there a way to uninstall grub so windows loads itself properly? will the tip spandon posted in post nr.4 work in my case as well?

thanks in advance!!

---

### Post by Vlatko on 2006-04-19
anyone?

---

### Post by mozetti on 2006-04-19
I'll take a shot, since you haven't received any responses yet, Vlatko.

1) I'm assuming you used Ext3 as your filesystem on Linux, since it's the default for Ubuntu. Windows can't read/write Ext3 out of the box, and I think that's why it's taking so long - Windows is trying to read the drive. There is a driver DLL file you can install that will give Windows the ability to read Ext2/3 - Ext3 is just Ext2 with journaling. I don't have a link handy, but it's on the forums here - I've installed it and used it with no problems.

2) Same as #1 - Windows can't read the Ext3 file system, so it won't show up in "My Computer"

3) Not sure on this one, but my guess is that it's getting hung up because it's expecting a hard drive that isn't there. If you get #1 & #2 sorted out, then you shouldn't need to unplug your HDD and #3 will go away, too.

Good luck!

---

