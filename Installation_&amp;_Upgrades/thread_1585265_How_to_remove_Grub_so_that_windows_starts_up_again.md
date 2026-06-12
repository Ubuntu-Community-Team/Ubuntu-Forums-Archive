---
title: "How to remove Grub so that windows starts up again?"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by anarchipur on 2010-09-30
:confused:Hi,
 
I have windows Vista and Ubuntu 9.04 on my asus laptop and use grub as boot manager. I tried to reinstall windows vista with the recovery CD delivered with my laptop in order to just get rid of the old installations. The Installation was OK, however when rebooting windows doesn't come up printing the error could not load GRUB Error 22.
 
Now I think I should remove grub from teh master boot record, and the system will supposedly work.
 
My question is is this a solution and how do I reformat the master boot record?
Can I do it with the Ubuntu instalation CD?
 
Please help!
 
Many thanks to the community!

---

### Post by marin123 on 2010-09-30
you need your windows installation cd. boot it up and select Repair system (something like that) and then open command prompt and when youre in command prompt, type "BootRec.exe/fixmbr" without quotes. this will fix windows and it will boot normally, but you wont be able to boot into linux anymore and you will have to reinstall grub from live cd... it's a pain in the ***, but its the easiest way to fix it...

edit: i think there's a way of adding ubuntu to windows bootloader (i think its called BCDedit)...

---

### Post by anarchipur on 2010-09-30
The problem is the WIndows Vista recovery CD I got the asus Pro55series laptop does not have the option to recover teh mbr; it does not have an option to start the console.
The only option is to install windows. So that's the reason I could not reformat the mbr with the vista recovery disk.
 
So can I do it otherwise?
I have an UBUntu Intsallation CD and I have a Windos XP instalaltion CD.
 
so my questions would be now:
1. What if I boot with the Wondows XP CD and use its possibilities to recover teh mbr and then install vista again?
 
2. How do I do it using the Ubuntu Installation CD?
 
3. Is there an alternative?
 
Thanks again!

---

### Post by marin123 on 2010-09-30
either download vista installation cd from internet, or you can reinstall grub...
here is the link that could help you:
[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]
[/URL][https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2010-09-30
From the liveCd you can download and install a windows style boot loader.
Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

You can download a windows repair CD and you should if you want to continue to use windows:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.

If you reinstall from your system disk it should have reinstalled the MBR, did it complete its install correctly?

---

### Post by anarchipur on 2010-10-01
Thank you!
 
I booted with a Windows XP CD. It showed me the mbr as a partition. I just formated the boot partition, and then rebootet. Windows Vista started working.
 
Many thanks for your ideas!

---

### Post by marin123 on 2010-10-01
> **anarchipur said:**
> Thank you!
 
I booted with a Windows XP CD. It showed me the mbr as a partition. I just formated the boot partition, and then rebootet. Windows Vista started working.
 
Many thanks for your ideas!

the xp cd actually worked? nice... i'm glad you got it to work :)

---

