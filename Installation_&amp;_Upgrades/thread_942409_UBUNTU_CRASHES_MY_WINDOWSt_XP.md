---
title: "UBUNTU CRASHES MY WINDOWSt XP"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by itubaba on 2008-10-09
Had both XP and version 7.1 working great on my new PC. Decided to upgrade to 8.04 today.

After installing the grome refuses to load the Windows. The Ubuntu is working great but each time I go to the Windows it kicks me out.

Entered the partion software on the Ubuntu and discovered a problem showing on my XP partion on NTFS. Ubuntu claims it is is empty.

Got my XP CD and ran DISKPART. Got the message
C: Partion 1 [Unknown] 336844 MB  (correct size showing)

Ran CHKDSK C: and got the message:
The Volume appears to contain one or more nrecovable problems.

This is giving me a lot of concern. I hope my data is not lost. PLEASE HELP
:(

---

### Post by PocketDog on 2008-10-09
try CHKDSK /f

---

### Post by itubaba on 2008-10-09
No such option in Chkdsk. Only /R and /P

Got the same message for both: THE VOLUME APPEARS TO CONTAIN ONE OR MORE UNRECOVERABLE PROBLEMS

---

### Post by itubaba on 2008-10-09
No such option in Chkdsk. Only /R and /P

Got the same message for both: THE VOLUME APPEARS TO CONTAIN ONE OR MORE UNRECOVERABLE PROBLEMS

---

### Post by Mark Phelps on 2008-10-09
You said you "upgraded" but did you  upgrade through Upgrade Manager (i.e., installing the new packages from inside ubuntu) or did you insert a CD/DVD and install the new version ontop of 7.10?

---

### Post by PocketDog on 2008-10-09
/f (or /F) is definitely a chkdsk option, it means 'fix'.

---

### Post by lisati on 2008-10-09
> **itubaba said:**
> No such option in Chkdsk. Only /R and /P

Got the same message for both: THE VOLUME APPEARS TO CONTAIN ONE OR MORE UNRECOVERABLE PROBLEMS

<aside>Huh? All the machines I've used in recent years have the /f option. It's fairly standard, as is the /v option for "verbose" mode</aside>

EDIT: Is it possible that something nasty unrelated to Ubuntu (e.g. virus) has crept onto XP and replaced its chkdsk with something else?

---

### Post by cariboo on 2008-10-09
Here is a link on how to use chkdsk:

[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

You may not quite be using chkdsk properly.

Jim

---

### Post by Elfy on 2008-10-09
It's chkdsk /r or /p in recovery mode iirc


> &#8226;	Chkdsk The /p switch runs Chkdsk even if the drive is not flagged as dirty. The /r switch locates bad sectors and recovers readable information. This switch implies /p. Chkdsk requires Autochk. Chkdsk automatically looks for Autochk.exe in the startup folder. If Chkdsk cannot find the file in the startup folder, it looks for the Windows 2000 Setup CD-ROM. If Chkdsk cannot find the installation CD-ROM, Chkdsk prompts the user for the location of Autochk.exe.

---

### Post by lumilanis on 2008-10-10
Try to use Recovery console under XP Install menu
Type: fixmbr

It usually solves the problem. I used it many times.

---

### Post by itubaba on 2008-10-10
I installed by using the the Ubuntu CD to do the installation.

Latest is that I downloaded TestDisk as recommended and ran it using the hard disk as an external.

I got a log of TestDisk, but the bottom line is that:
1. Under the quick test, it shows 3 hard partitions
2. Under intensive test, it shows 7 partitions.
3. After doing a fix, it claims the partition can not be repaired.

Dont know what to do next

---

### Post by itubaba on 2008-10-10
I forgot to mention. After the intensive test I mentioned above, it said something like the sum of partitions is more than the hard disk size.

---

### Post by SeanHodges on 2008-10-10
> **itubaba said:**
> I forgot to mention. After the intensive test I mentioned above, it said something like the sum of partitions is more than the hard disk size.

Any chance you might have selected the Windows partition for installing 8.04 on?

If you use the CD instead of the upgrade manager you are performing a brand new installation, and not an upgrade.

Edit: Use a live CD (like the Ubuntu one you have) to look at both of the partitions. You should be able to mount them and look inside...

---

### Post by itubaba on 2008-10-10
do I need to reboot with the live CD ?

I know I did NOT install over the Windows as I can still see the begining and end of it but can not enter

---

### Post by Torgas Prim on 2008-10-10
If all else fails, boot into ubuntu and copy all of your data from the windows install into your ubuntu.
Then just reinstall XP...(IF you really want to ;) )

---

### Post by Mark Phelps on 2008-10-15
I asked you about how you "upgraded" because I had the suspicion that you actually overwrote either Ubuntu or XP when you did the "upgrade".

The default, when installing from the live CD, is to write GRUB to the MBR of the disk on which Ubuntu is being installed.  I didn't catch how you were booting before, either by selecting Windows from a GRUB menu, or by selecting Ubuntu from a Windows menu. But regardless, you most probably overwrote the MBR when you installed Ubuntu -- however, it should have found the XP installation and added a menu entry for it.

Can you successfully boot into Ubuntu (if so, which version?) or XP?

---

