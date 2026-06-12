---
title: "Ubuntu 13.10 and Windows 8 - booted to windows no can't access my data"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2014-06-15
I have a dual boot with Ubuntu 13.10 as the primary and Windows 8 available to boot into. I have 3 partitions, one for Ubuntu, one for Windows and one for all my data. Everything was working fine in Ubuntu. I was "forced" to use Windows (GAWD how I hate it!) and booted into it. Now when I boot in Ubuntu, it can't mount my data drive. I get a (S)kip or (M)anual option. If I skip, the data drive isn't there. If I choose manual, I drop to a command prompt but don't know what to do. If I run gparted it shows the data drive. If I boot back to Windows, I can access the data drive. Windows must have done something to the data drive when I originally booted into it.

How do I  get ubuntu to see it again? I tried to manually mount it but the following message shows up:

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda8': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I booted back into Windows and made sure it shut down completely but problem continues

All help greatly appreciated! Help!!!

---

### Post by Bucky Ball on 2014-06-15
Was Win shut down correctly? I'd boot back into Win and do a total shutdown again as see if it makes any difference.

Please read this, from your output:

> Please resume and shutdown Windows fully (no hibernation or fast restarting)

---

### Post by PopsTheSailor on 2014-06-15
Yes. I even said in my original post that I restarted Windows and made sure it shut down OK. So I've already tried that. 

Thanks

---

### Post by Bucky Ball on 2014-06-15
Hmm. Apologies. Strange, because that seems to be what it is banging on about with that error message. :-k

---

### Post by yancek on 2014-06-15
When that error is show, it is generally the result of an unclean shutdown and it is usually necessary to run a filesystem check on windows.  I think the command is 'chkdsk' but I don't really use windows so can't be sure.  The Skip/Manual message is generally not a problem.  For whatever reason, I see that frequently and just hit the S key and if I want, I can then manually mount the partition after logging in.  Since manually mounting from ubuntu doesn't seem to work for you, I believe you will need to run chkdsk from windows.

---

### Post by oldfred on 2014-06-16
With Windows 8 standard shutdown is fast boot which is hibernation.
You have to leap thru several hoops to make sure fast boot is off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by PopsTheSailor on 2014-06-17
Well, thanks for the feedback. In trying to fix this, I've seemed to have dug myself further into the hole. I mistakenly tried to run boot repair thinking that would fix it. It didn't and now I can't boot into Windows any longer to do the full shut down routine. Before I take any further action and make things worse, is there a way to reload Windows 8 without totally ruining my configuration? I now have 3 lines in my grub menu relating to windows and EFI or something (unfortunately didn't write it down when I booted so can't give exact lines here). I tried all of them but I get a "file system" no found type of error message from Windows. I have my Windows recovery discs if someone can give me guidance.

---

### Post by oldfred on 2014-06-17
If you did this run the undo. This is for those systems that only boot Windows.

 Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by PopsTheSailor on 2014-06-17
Well, I had 2 problems but have fixed one in probably an unconventional way but I'm letting everyone know in case someone stumbles across this thread.

I fixed the issue with my Data partition not mounting because Windows was not fully shut down. 

First, BACKUP YOUR DATA. I also make no warranties that this will fix your problem or that it won't cause you more problems. USE AT YOUR OWN RISK

To fix it, I opened gparted (sudo gparted) and resized my data partition that wouldn't mount. After doing that, the drive must have been "fixed" somehow. I was going to copy all my data to a new partition so when I resized it, I took a pretty big chunk off of if. I would recommend you try the smallest allowable resizing because that would minimize how long the resizing takes. 

I'm off to work on the issue with windows not booting next.

---

### Post by Bucky Ball on 2014-06-17
Nice one. Now you might like to run Boot Repair ...

---

### Post by PopsTheSailor on 2014-06-18
OK. All fixed. I reran boot repair and restored the EFI backups. It left the names a bit odd still but one of the 3 for Windows will let me boot up Win 8. I've also turned off fast boot by going into the power options, going to advanced, scrolled down and unchecked the fast boot option.

---

