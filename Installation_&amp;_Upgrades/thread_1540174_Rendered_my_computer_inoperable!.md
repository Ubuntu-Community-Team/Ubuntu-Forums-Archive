---
title: "Rendered my computer inoperable!"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by nc10user on 2010-07-27
Hey everyone, I could really appreciate some advice.

A few months ago I installed Ubuntu Netbook 10 on my Samsung NC10, creating a dual-boot setup with Win XP. Due to the fact that I use linux more on my desktop and the fact that I had a problem with Windows, I decided to use Samsung's restore to just bring the netbook back to its original state.

I first noticed a problem when pushing "f4" during the BIOS didn't bring up the restore program as usual. Instead, to run the restore I had to choose it from the list of options I'm usually presented when booting up (Ubuntu, the memtest, XP, etc). I will admit right here that it was probably a bad idea to continue with the restore at this point.

I was, however, able to execute the restore program and it fully completed its work before asking for a restart. On restart, however, the BIOS screen comes up as usual but afterward goes to a blinking cursor in the top left for about 5 seconds before restarting automatically. It continuously does this in a loop.

Meanwhile, hitting F2 at the BIOS screen will bring up the setup but F4 still does nothing (I figured maybe i just had to restore again).

If anyone has ANY suggestions, I would REALLY appreciate it!!!

NC10user

---

### Post by wilee-nilee on 2010-07-27
Post the bootscript in my signature in code tags as described. You can also get the code tags by highlighting the text in a reply and clicking on the # in the reply panel.

Do you have a external cd/dvd writer and do you have a XP install cd?

---

### Post by nc10user on 2010-07-27
thanks for the quick reply. I don't have an external, and while I have a samsung restore disk, I'm hoping i can get the backedup image on the partition. 

I will try to use the boot script and report back in a bit.

---

### Post by AshRice on 2010-07-27
Hey, I'd try this if you don't have a windows disk handy:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

pretty self explanatory

---

### Post by Mark Phelps on 2010-07-27
> **nc10user said:**
> ... A few months ago I installed Ubuntu Netbook 10 on my Samsung NC10, creating a dual-boot setup with Win XP. 
When you did that, did you blow away the restore image partition present on the drive to make room for Ubuntu?  Asking because, all to often, folks here say you CAN do that if you have a restore CD, not knowing that (in many cases) the restore CD is nothing more than an OEM-customized version of WinPE that merely boots the machine and starts the restore -- looking for the saved OEM image file.

What it then should do, if it does NOT find the image file, is error out with a message indicating that it can't locate the image file.  But, it seems that in some cases, it quietly exits -- leaving you to believe it DID do the restore, when in fact, it did Not.
> I first noticed a problem when pushing "f4" during the BIOS didn't bring up the restore program as usual. 
In this case, maybe F4 did the same thing as the Restore CD, and if there is no restore image on the drive, it will not work.
> I was, however, able to execute the restore program and it fully completed its work before asking for a restart. 
But how long did it run? 5 minutes? 30 minutes? An hour or more?  Asking because the last time I did a factory restore on an HP desktop, it took several HOURS to complete.  So, if your finished in a few minutes, it probably didn't actually restore the OS.

Running the script that was mentioned will provide us a detailed list of what's still present on your machine, and perhaps you'll be lucky in that the restore DID work, it's just the boot loader that is hosed.

But, if the restore partition is gone, and you want the full OS partition back, you will have to contact Toshiba to see if they will provide you a full-restore set of disks (or maybe, just a single DVD).

---

### Post by nc10user on 2010-07-27
An update:

First, thanks for the additional help. I'm not going to answer your questions directly because I think this changes things a bit.

Basically, I have access to my machine again. I just reinstalled Ubuntu via flash drive again. When I did, I found a couple of things out:

- The restore process did bring back my XP to factory state
- The previous ubuntu installation is still there, totally intact and functional.

I'm obviously not an expert but I assume restoring the computer messed up the boot process somehow, and the reinstallation of Ubuntu restored it again. 

Now all I want to do is remove the two Ubuntu installations, leaving just the Windows. Any thoughts on how to accomplish this without killing my computer again?

Thanks for all the help.

---

### Post by wilee-nilee on 2010-07-27
So if you can get a external cd reader you can download this legit XP ISO burn it and use it to follow the second link on putting the MS bootloader in the MBR with the fixmbr command.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

You would just be booting MS with it's bootloader, then you would just remove the Ubuntu partitions with gparted from a live Ubuntu cd and expand XP into it's former area if you wanted.

I kind of surprised that the recovery which left you unbootable just didn't boot straight into XP.

---

### Post by AshRice on 2010-07-28
I hate to bring it up again, but you can do what I mentioned earlier to restore the Microsoft boot loader, and then from windows you can format the Ubuntu partitions. 

At that point you can either try to expand your XP partition to fill the new space using one of the free tools (I'd search lifehacker.com), or you could just format the free space into another NTFS drive.

---

### Post by wilee-nilee on 2010-07-28
> **AshRice said:**
> I hate to bring it up again, but you can do what I mentioned earlier to restore the Microsoft boot loader, and then from windows you can format the Ubuntu partitions. 

At that point you can either try to expand your XP partition to fill the new space using one of the free tools (I'd search lifehacker.com), or you could just format the free space into another NTFS drive.

If I might point out the date of your link, 

Tue, Jan 15, **2008**

If a person wanted a MS reading bootloader from Linux it would be lilo. I think this person will best be served by having the MS bootloader back in place it is easy it just requires a external cd reader in this case.

---

### Post by nc10user on 2010-07-28
> **wilee-nilee said:**
> If I might point out the date of your link, 

Tue, Jan 15, **2008**

If a person wanted a MS reading bootloader from Linux it would be lilo. I think this person will best be served by having the MS bootloader back in place it is easy it just requires a external cd reader in this case.

I'm going to follow up on both of these suggestions. Off hand, do you think either of these solutions are possible using a liveUSB instead? I currently do NOT have access to a external drive, but could rip an ISO using my desktop computer and load that to a flash. Just a thought.

Also, I'm surprised there is no easy uninstaller for Ubuntu, and even more surprised that an uninstallation wouldn't replace the original MBR.

Thanks,
nc10usah

---

### Post by nc10user on 2010-08-03
My computer has been restored to factory condition, thanks to advice from people on this forum as well as some additional  research. Fixing it was actually pretty easy. First, I reinstalled Ubuntu. **It's a big mistake to think that simply deleting the partitions constitutes a true uninstall. That was the mistake that cost me.**

After that, I had my windows installation back but still wanted to take off ubuntu. The problem is the boot record and that can be fixed by the instructions detailed here:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

This tells you how to use the 'fixmbr' command in the Recovery Console to fix your boot record. At the bottom is a link to the overview for the recovery console where one can download it.

After that, it was merely a matter of choosing the recovery console on startup, choosing my windows installation, and using the fixmbr command. Then I deleted the Linux partitions. 

Thanks to everyone who helped!!

---

