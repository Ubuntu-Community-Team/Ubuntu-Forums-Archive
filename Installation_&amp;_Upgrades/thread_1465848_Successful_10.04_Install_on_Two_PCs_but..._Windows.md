---
title: "Successful 10.04 Install on Two PCs but... Windows 7 won't boot"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Cappy1 on 2010-04-29
Greetings,

I updated a PC and a laptop to 10.04 from 9.10 today.  Both installs seem to work well, as least from what I can tell so far.  

However, on the PC with a dual boot via Grub, I can no longer boot to Windows 7.  When I select the Windows 7 boot option from Grub the PC just reboots.

There was a Grub configuration window that popped up during the 10.04 install.  I thought I checked the correct device (/dev/sda1) but it is possible that Grub wanted one of the tiny partitions checked, not sure.  

I have two SSD in the PC, one with Windows 7, and one with Ubuntu.  I believe that Grub boots from the Windows 7 disk.

Any ideas on how to proceed with debugging this problem would be appreciated.

---

### Post by movieman on 2010-04-29
Isn't that a known bug with the initial 10.04 release? I think you need to run update-grub to detect the Windows partition?

---

### Post by Cappy1 on 2010-04-29
Movieman,

Thanks for responding.

It sure seems related but I looked at the critical bug report and it says that no Windows entry showed up in Grub.  In my case I did get a Windows entry, it just goes into outer space when selected.

I did try the update-grub but that didn't fix the problem.

So it's possible the critical fix wasn't complete, or maybe I'm experiencing something completely different, not sure...

---

### Post by lindsay7 on 2010-04-29
Take a look at this.  You should have installed grub to sda not sda1.


[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by bcbc on 2010-04-29
I've seen a few problems like this with 10.04. It appears that grub2 can install itself to the windows partition and interfere with Windows.

Here is a site that has detailed instructions to recover win7: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

It's the command 'bootsect.exe /nt60 all /force' that seems to get things working again. 

Note, once windows is working, you'll only be able to boot it, and not ubuntu. So have the live CD handy, boot it and then reinstall grub2 to the MBR afterwards. This post will show you how to do that: [http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by oldfred on 2010-04-30
I think bcbc command reinstalls the windows boot loader to the MBR.

Your install of grub2 to the sda1 boot sector requires a fixboot.

This is all the commands but you should only need fixboot:

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

[http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html](http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html)
Bootsect.exe updates the master boot code (BS) for hard disk partitions
in order to switch between BOOTMGR and NTLDR.
You can use this tool to restore the Boot_Sector (BS) on your computer.
When used with the /nt60 option, the Master Boot Record (MBR) is
*compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by lindsay7 on 2010-04-30
See My post above.  I made the same mistake you did and fixed it with what I gave you.  Try that first. If it does not work then do as the others suggest and re-do the mbr.  You may still need to do what I gave you in the first post to get dual booting.  As I said I made the same mistake as you on two different computers before I understood that the grub needs to be placed on sda or sdb not on one of the partitions i.e. sda1 or sdb1.  I think having grub on those partitions will not hurt you but you need to have it installed on sda or sdb or you will have problems.

As Oldfred points out. running bootrec and fixboot is quicker then doing the three repair startups.  So take your choice.

---

### Post by Cappy1 on 2010-04-30
Thanks Lindsay7, bcbc, and oldfred,
 
I was able to fix my Windows boot problem. I really appreciate the help of you guys.
 
First I moved the grub loader from the Windows 7 SSD to the Ubuntu SSD per lindsay7's information. I'm not sure why grub ended up on the Win 7 disk when I installed Ubuntu 9.10 a while ago -- but maybe that confused the 10.04 upgrade procedure such that I was no longer able to boot windows.  Grub really belongs on the Ubuntu disk.
 
As part of the grub move process I ran update-grub per linday's information. This added all the Ubuntu and memory testing entries, but it didn't add an entry for the Win 7 boot.
 
I then spent a few hours figuring out how to fix up the MBR on the Windows disk. Here bcbc's info was helpful. I did run the Win 7 recovery repair multiple times but that did not fix the boot record. I dicked around with the bootrec.exe commands and it wasn't until I did the bootrec.exe /fixboot that I got my MBR back successfully such that I could boot directly into the windows disk if that disk was selected first in the PC Bios.
 
By the way, for any others that have a similar problem, the bootsect.exe and bootrect.exe programs are in the x:\windows\system32 directory on the Win 7 Install disk.
 
I just came back to the forum here and noticed oldfred had documented the steps I had to follow, so this is great info if others have similar problems.
 
Now I just needed to get the Windows 7 entry back into grub over on the Ubuntu SSD. I ran update-grub again but got errors on the os probe. It turned out that grub was getting confused with the lower-case "boot" directory on the Windows drive. It was looking in there instead of the upper-case "Boot" directory. NTFS doesn't distinguish between upper and lower case. I renamed the lower-case "boot" directory to "bootx" (it contains a grub directory, I also could have deleted it), and reran update-grub. Now the probe found Windows 7 and added a grub boot entry. I set the PC Bios to boot the Ubuntu disk first. It all works and I can now still boot Windows directly if I ever want to remove the Ubuntu disk.

---

### Post by lindsay7 on 2010-04-30
Good work. Happy you got this figured out. Sounds like you have a nice setup with the ssd's.

---

### Post by Lazy-buntu on 2010-04-30
I'm having a similar problem over at: [http://ubuntuforums.org/showthread.php?p=9203584#post9203584](http://ubuntuforums.org/showthread.php?p=9203584#post9203584)

I'd appreciate any help!

---

