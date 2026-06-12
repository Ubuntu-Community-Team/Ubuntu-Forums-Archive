---
title: "two disk dual-booting problems and confusions"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by dgaretz on 2008-08-15
Ok forgive me if this thread is searchable and I'm just a high *** and cant find it but I just spent all night messing w/ my grub menu.lst and trying just about everything I could find that actually seemed like good information. 

Heres the situation: I have 2 HD's, a 160gb master and 13gb slave, both formatted clean no partitions. I installed Windows XP first on my slave IDE drive booted everything is fine. Put in my LiveCD and continue to install Ubuntu on the 160gb drive. Everything on my ubuntu installation goes nice and dandy (hardy just to clarify). Now according to ubuntu grub should auto recognize my windows partition and put it in the menu.lst, well it didn't. So i tried pretty much every variation I could find some examples include

title Windows XP
root (hd1,0)
makeactive
chainloader +1
savedefault

title Windows XP
rootnoverify (hd1,0)
chainloader +1
map (hd1) (hd0)
map (hd0) (hd1)

blablabla so on and so forth. With map I get the error NTLDR is missing, Ctrl+alt+del to reboot and w/o it the computer hangs at Starting up... _  _ _ _ _ _

It is my understanding that its possible that my boot.ini is pooched in that it still thinks its c: but it should be d: or something. But on my mounted 13 gb media on Linux shows no boot.ini anywhere. Im sure there is someone out there that that encountered a similar situation. Any help would be great. Thanks in advance

---

### Post by Pumalite on 2008-08-15
This will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by dgaretz on 2008-08-15
Mmmm thanks but I think all of those solutions I've tried. I think I'm going to use win cd and do fixboot and fixmbr and then reinstall grub. hopefully it will work. will post soon.

---

### Post by Pumalite on 2008-08-15
You can also switch the boot order in BIOS and then reinstall Grub.

---

### Post by kflorek on 2008-08-16
Yeh I've done this, but not in a while and not with Vista. From memory...

This is wrong:

title Windows XP
root (hd1,0)
makeactive
chainloader +1

 
 Here's what goes wrong with this one. Windows only boots from a partition that is made active. You would think that means the partition Windows is on, but that's wrong. Yes the OS files are there, but Windows always puts the actual boot files (just a few) on the first hard disk as numbered by the BIOS and the first active primary partition on that disk. That partition is the one that needs to be made active

makeactive (hd0,0)

Linux doesn't care about "active" and doesn't need it or change it. So you actually only need to make a partition active once, not every time you boot, but it doesn't hurt.

Also the Windows installer is liable to create the Windows partition on a second hard drive as a logical partition if you also have it partition the hard drive. (But not if you chose a pre-existing partition.) Then grub numbers _logical_ partitions starting from 4, in which case, you would have

root(hd1,4)


If you have switched where the disk is AFTER Windows was installed, your headaches have just begun. Although I have sometimes gotten Windows to work like this, it is so screwed up you'd need a special reason to make it worth while. You didn't move the disk, so DO NOT use map. The drives are in the right place according to what Windows wants.

 Windows XP would only screw up the drive letters if you add a Windows style partition (FAT or NTFS) to the first hard drive (and normally not then if XP has been booted correctly once.) But if you ever reinstall windows over itself to fix something, all bets are off about the letters. If you do, hide the Windows style partitions added before you do, to prevent total screw up. (Windows 9x is another thing. It always changes the letters when partitions are added before its original position.) If you add a partition to the same drive BEFORE where XP thinks it is, boot.ini needs the partitions upped by 1, but XP should still keep its own drive letter internally the same.

---

### Post by caljohnsmith on 2008-08-16
> **dgaretz said:**
> It is my understanding that its possible that my boot.ini is pooched in that it still thinks its c: but it should be d: or something. But on my mounted 13 gb media on [COLOR="Blue"]Linux shows no boot.ini anywhere[/COLOR]. Im sure there is someone out there that that encountered a similar situation. Any help would be great. Thanks in advance
To boot Windows XP I believe you need the following three files:
```
ntldr
NTDETECT.COM
boot.ini

```
So if you are missing them, you won't be able to boot Windows. Since you installed Windows to your slave drive, I suppose it is possible that it could have tried to put its boot files on your master HDD; but that won't matter now that you've installed Ubuntu on that HDD and have overwritten anything that might have been there anyway. 

Try booting your Windows Install CD, go to the recovery console, and run the command "fixboot". I think that may recreate the boot files you need. Make sure you don't run "fixmbr" though as that is not going to help, because you don't want Windows possibly overwriting the MBR of your master HDD. 

If you still don't have your boot files back after running fixboot, I can attach a copy of mine and you can just use those. They should work without any modification since my Win XP is also installed on the first partition.

---

### Post by dgaretz on 2008-08-16
OK figured out how to get to recovery console from XP cd :D lol duhhhh. anyway. fixboot c: didn't solve anything. i have yet to logon to linux tocheck the drive to see if the boot files are there but fixboot c: still yields a ntldr is missing using the map function and it hangs at Starting up... otherwise. 

Is it possible that my XP installation is pooched? If so what are my options for reinstalling windows on it. My linux drive has no space on it to create another partition and windows wont install w/o a windows compatible partition on the master. I dont want to open up my computer and switch the cable around. But this seems like the solution right now because I've tried everything.

---

### Post by Pumalite on 2008-08-16
Try Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It can boot your Windows if it's bootable.

---

### Post by caljohnsmith on 2008-08-16
Before you give up on your Windows partition, try downloading the attached zip file to this post. Just unzip the file and put the three boot files in it in your Windows root directory, reboot, and see if it works.

---

### Post by kflorek on 2008-08-16
>i have yet to logon to linux to check the drive to see if the boot files are there...

The boot files have to be on a Windows type partition, so if you actually had the Ubuntu installer take over the whole disk, rather than add a partition, then the boot files can't be there on a linux partition. (Windows can't recognize linux partitions, which use a completely different file system.) I don't know what was done.

 fixboot puts a secondary boot loader on the first primary partition on the first hard drive, as Windows see it through the BIOS.

 The first boot loader is not on a partition, but is the first sector of the hard drive which contains the partition table also. Recovery console puts that on the disk with fixmbr. In Windows, the function of the first boot loader is just to find and load the second one. (Grub can do that (using chainload +1) or do something else.)

 Both of these loaders exist outside any file system and don't need one, so they can be changed without damaging Window or Linux files themselves.

ntldr and ntdetect.com need to copied from somewhere if they are gone. They are in the i386 directory of the Windows CD and can be copied from there using the recovery console copy command. They actually are files in a file system.

bootcfg is the recovery console command that can find Windows installations and create a boot.ini for you. help bootcfg at the recovery console explains it, if you can make it out.

There are linux programs that will resize partitions, so you could put a Windows type partition on the first disk, if you want. You also have to format that partition before files can be copied to it.

 However, even though I have done stuff like that -mostly to see if it could be made to work- the amount of time and learning that goes into it is large. If you don't enjoy this sort of thing, if you haven't got a lot of time put into whatever is on your drives, and nothing too important to lose, it may save time to cut your losses and start all over.

 One thing I overlooked is that, since Windows did boot once, there was a Windows partition on the first hard drive originally, which would get drive letter C, and therefore Windows thinks of itself as on D. If you switch hard drives on the cable, Windows should still think of itself as D. If not, it may die of drive letter confusion.

---

### Post by caljohnsmith on 2008-08-17
> **kflorek said:**
> fixboot puts a secondary boot loader on the first primary partition on the first hard drive, as Windows see it through the BIOS.
Thanks for clarifying about that command, but what you say is true if dgaretz doesn't specify a drive name with the command, correct? I mean he could specify a different drive other than C: to have fixboot install a Windows boot loader into the boot sector of another partition, true?

I've never read about or researched exactly what happens during the Windows boot process, so which of those three files (boot.ini, ntdetect.com, ntldr) is considered the "stage 2" file in the Windows boot process? Also, instead of the Windows MBR specifying the boot files directly like Grub does with Linux and its "kernel" "initrd" method, does the Windows MBR do a hand-off to the boot sector in the Windows partition, and then the boot sector of the Windows partition points to one of those three boot files to continue the boot process? Because if it didn't work that way, why would Windows need anything at all in the boot sector of its own partition? Certainly there are no technical reasons why the Windows MBR couldn't work similar to Grub, and boot the Windows partition by directly specifying the boot files, correct? 

Also, if you have any web references (e.g. from the microsoft.com website or similar) that explain the Windows boot process in detail I would sure like to read it. Thanks for your explanations. :)

---

### Post by Pumalite on 2008-08-17
[http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/](http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/)

---

