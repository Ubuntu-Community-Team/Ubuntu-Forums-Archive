---
title: "Windows partition not visible from Ubuntu"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2011-12-14
I have a triple boot setup on a desktop and my laptop. In each case I have a single drive, partitioned for DOS (FAT), Windows XP(FAT32), Windows Swap (FAT32), Ubuntu 10.10 (EXT4), and a data partition (NTFS). 

When I boot either machine into Ubuntu, I see all my partitions listed under the "places" pull down menu, EXCEPT the Windows partition on the desktop.  I looked for the partition with the Ubuntu Disk Utility, and it was missing.  I looked for the partition with GParted, and there it was.  Seemingly healthy.  Must not be too much wrong with it, because I can boot into Windows.

I really want my Windows partition to be visible from a Linux boot.  Can anyone here tell me how to fix this?

---

### Post by Mark Phelps on 2011-12-15
Let's first get a look at your partitions.  To do this, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions.  Please post the results back here.

---

### Post by Hakunka-Matata on 2011-12-15
Hi Engineeringtech:  Good to see you back..

**Ubuntu cannot read/write to FAT32 file systems.    CORRECTION:  VanillaMozilla CORRECTED ME ON THIS IN POST # 5 **
One solution to your setup would be to format your WindowsXP partition to NTFS.  XP installs w/o problems to NTFS partition type.

---

### Post by Mark Phelps on 2011-12-15
If you're interested in converting the FAT32 partition to NTFS, and doing that inside Win XP, then read the info below:

[http://aumha.org/win5/a/ntfscvt.php]("http://aumha.org/win5/a/ntfscvt.php")

---

### Post by VanillaMozilla on 2011-12-15
> **Hakunka-Matata said:**
> Ubuntu cannot read/write to FAT32 file systems.
Baloney.

I have a whole collection of FAT32 USB Flash drives.  They work perfectly under Ubuntu.  I have a 1 TB FAT32 USB hard drive that also works perfectly.

You can also mount a fat32 hard drive that's installed on the computer.  (Disclaimer:  I'm almost certain, but I haven't ever had to do it.)  OK, I'm stuck behind a Windows computer at the moment, and I don't remember how to mount it, but for a start, look in the /mnt/ directory.  (You may have to install a file system first, but probably not.  If you can see it but can't read it, right click on it and see if you get a "mount" menu.  Again, I don't think you will have to do this, but I'm not certain.)

Don't convert the drive to NTFS at this time.  There will be side effects.  You can't convert it back, and you don't need to add another problem.

---

### Post by Hakunka-Matata on 2011-12-15
> **VanillaMozilla said:**
> Baloney.

I have a whole collection of FAT32 USB Flash drives.  They work perfectly under Ubuntu.  I have a 1 TB FAT32 USB hard drive that also works perfectly.

I'm almost certain you can also mount a fat32 hard drive that's installed on the computer.  (Disclaimer:  I haven't actually done it.)  OK, I'm stuck behind a Windows computer at the moment, and I don't remember the fstab incantations, but you surely can mount it.  For a start, without mounting automatically, I think you will see it in the /mnt/ directory.  (I forget, you may have to install a file system or something to see this, but it will work.)

Don't convert the drive to NTFS at this time.  There will be side effects.  You can't convert it back, and you don't need to add another problem.

Right, I admit my error:  How did this happen to me, one who strives to put only accurate information out there?  
A.  Examine why it has happened to you in the past, maybe the cause is similar.  I say **Ubuntu won't write to FAT32 Partitions** because, as I now recall, the file size is limited to what is it?, 4GiB?  Anyway, why  would someone choose to use FAT32 when NTFS is available, w/o the restrictions of FAT32?, for **me** there is no good answer to that question.  Instead, I just never use FAT32, unless required to, e.g. [B].ISO files.

P.S. [/B]Baloney is bad for you, just like FAT32, AFAIC

---

### Post by BC59 on 2011-12-15
> **Engineeringtech said:**
> I really want my Windows partition to be visible from a Linux boot.  Can anyone here tell me how to fix this?

You can install Storage Device Manager and from there configure the partition.

---

### Post by VanillaMozilla on 2011-12-15
> **Hakunka-Matata said:**
> How did this happen to me, one who strives to put only accurate information out there?   ...Anyway, why  would someone choose to use FAT32 when NTFS is available, w/o the restrictions of FAT32?
:mrgreen:  Don't worry, it happens to me all the time.  Sometimes people have fat32 hanging around from an old version of Windows, and there's no particular reason to change it.  But once you change to NTFS, then suddenly you have file permission and ownership problems, and there are still other side effects in Windows.  That's not to say don't convert, but once you convert, there's no turning back.

To the original poster:  Mounting it automatically requires editing "fstab", as I recall -- unless they changed it.  And getting it on the Places menu (if you still have a Places menu) is something else again.  Sorry, that's not much to go on.  The Storage Device Manager is a GUI device that edits fstab for you.  I don't know anything about the Storage Device Manager.

---

### Post by Hakunka-Matata on 2011-12-15
> **VanillaMozilla said:**
> :mrgreen:  Don't worry, it happens to me all the time.  Sometimes people have fat32 hanging around from an old version of Windows, and there's no particular reason to change it.  But once you change to NTFS, then suddenly **you have file permission and ownership problems,** and there are still other side effects in Windows.  That's not to say don't convert, but once you convert, there's no turning back.

To the original poster:  Mounting it automatically requires editing "fstab", as I recall -- unless they changed it.  And getting it on the Places menu (if you still have a Places menu) is something else again.  Sorry, that's not much to go on.  The Storage Device Manager is a GUI device that edits fstab for you.  I don't know anything about it other than that.

eh?  Anyway, Windows XP is so yesterday, I don't even waste time learning anymore about it, I've spent too many years of my life making a living dealing with people's Microsoft headaches.  Wake up or enjoy your own soupy mess, I've had my fill Cheers!

@Engineeringtech:  Nothing personal you understand.  But it's kinda like giving up smoking, can't hang around with smokers if you're trying to quite.  Life is hard, Microsoft&BillGates and only small turds in the road.
.

---

### Post by VanillaMozilla on 2011-12-16
Hakunka-Matata,
1. This isn't a Windows problem.  It's a Linux question.

2. Changing from FAT32 to NTFS is not unreasonably difficult or problem-prone, but it is totally unnecessary in this case, to solve the user's problem.

3. The user has not yet reported that the problem is solved.

---

### Post by Hakunka-Matata on 2011-12-17
> **VanillaMozilla said:**
> Hakunka-Matata,
1. This isn't a Windows problem.  It's a Linux question.

2. Changing from FAT32 to NTFS is not unreasonably difficult or problem-prone, but it is totally unnecessary in this case, to solve the user's problem.

3. The user has not yet reported that the problem is solved.

Hi VanillaMozilla:

This will be the last post on the subject you seem interested in pursuing, but I do not share that sentiment.

When I post something stupid, or totally incorrect, I expect to be corrected, chastised a little bit, and then move on.  

I'm moving on.

background:  check other threads by OP Engineeringtech

---

### Post by Engineeringtech on 2011-12-22
My apologies to everyone for the delays in responding.  I've been having health problems.  Unfortunately a regular occurrence for me these days.  Thank you for being patient.

> **Mark Phelps said:**
> Let's first get a look at your partitions.  To do this, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  ......... Please post the results back here.

See atttached.

> **Mark Phelps said:**
> If you're interested in converting the FAT32 partition to NTFS, and doing that inside Win XP, then read the info below:
...

I know how to do the conversion from Windows, but I deliberately selected FAT32 for the Windows partitions on both the laptop and desktop, because in my experience, it is faster.  I also occasionally boot into DOS to use some very old engineering utilities.  I like to have access to my Windows partition when I do that.  Not easy when the Windows partition is NTFS.

> **BC59 said:**
> You can install Storage Device Manager and from there configure the partition.

Would you please elaborate how I do this?


> **Hakunka-Matata said:**
> eh?  Anyway, Windows XP is so yesterday,....  Wake up or enjoy your own soupy mess, I've had my fill Cheers! ...... it's kinda like giving up smoking, can't hang around with smokers if you're trying to quit.  Life is hard, Microsoft&BillGates and only small turds in the road.
.

I was trying to learn a 3D CAD package (Solid Edge).  There are no good 3D CAD packages available for Linux. (Not in my opinion.) And I occasionally need to run other engineering software that is not generally available under Linux.   As for XP, I like it much better than Windows 7, and I prefer not to get into that long subject. Windows 7 is a resource hog too, and my hardware is three years old, and not too fast.

> **Hakunka-Matata said:**
> Hi VanillaMozilla:

This will be the last post on the subject you seem interested in pursuing, but I do not share that sentiment....................
background:  check other threads by OP Engineeringtech

I don't know what you are implying about my other threads.  I have always been open and up front with people.  I've always admitted I'm a Linux novice.  I've always appreciated the advice I get from people in this forum, and thanked them for it.  Unfortuately, I can't do EVERYTHING people suggest, because my mentors do not always agree on a course of action.  And SOME of the advice I've gotten in the past, has been of a "slash and burn" nature.  

I had terrible problems getting my multi-boot system working.  I followed peoples' suggestions, but over a period of months I made very little progress.   As instructed, I re-formatted and reinstalled dozens of times.  That is VERY time consuming.  And still my triple boot did not work.  I resisted using GRUB as a boot manager for Windows, but only after it failed many times to locate my DOS and Windows installations.  For months all I saw was cryptic command line codes which didn't mean anything to me.  

Some posters even so much as called me a liar when I said it still wasn't working.  On top of that, I was trying to do all this while fighting this illness which still hasn't been diagnosed.  When I finally got my multi-boot to work using a tool called "Boot Repair", I was overjoyed.   So you should realize why I will be reluctant now to make drastic changes such as reformatting or repartitioning, just to solve this problem.

---

### Post by VanillaMozilla on 2011-12-28
Yes, I see, Hakunka-Matata.  Thanks.


EngineeringTech,
I think this will work.

To identify your partitions and choose the right one, in a Terminal type

sudo blkid

As an example, my Windows partition is /dev/sda2 (although it also has a much longer, random name).

Decide on a name for the partition.  Let's call it Windisk.  Then you need to create a directory 
/mnt/Windisk

Then edit file "fstab" with the following command:

gksudo gedit /etc/fstab

For my disk fstab has the following line:
/dev/sda2 /mnt/Windisk ntfs-3g defaults 0 0

For your disk it would be something like
/dev/<something> /mnt/Windisk fat32 defaults 0 0

(Substitute your partition for <something>.  Save and close the file, restart the computer, and I think that will do it.

---

### Post by Engineeringtech on 2012-01-31
> **VanillaMozilla said:**
> 

....identify your partition....   sudo blkid

As an example, my Windows partition is:  /dev/sda2 .....

Decide on a name for the partition. .... /mnt/Windisk

Then edit file "fstab" ...:  gksudo gedit /etc/fstab

.....something like:
/dev/<something> /mnt/Windisk fat32 defaults 0 0

...Save the file, restart ......


Thank you Mozilla.  I've been out of the forum since my last post.  Health problems as usual.  Neglected to log out.   Just got back to the forum today.  I apologize for this.  I do appreciate your efforts.

I did as you suggested.  My Windows partition is "/dev/sda5".  I made a folder  "/mnt/Windows".  I edited fstab, adding : "/dev/sd5 /mnt/windows fat32 defaults 0 0"  and rebooted.  Still no Windows partition shown in the places menu, and the Windows folder I created is empty.

I have noticed Gparted shows the Fat32 Windows partition, but Disk Utility shows the space as unallocated.   I was tempted to run Gparted's "check and repair" function on the partition, but I am worried about screwing up the files in the partition.  It IS a working Windows partition.

Any more ideas? Would you think it safe for me to run Gparted's "check and repair" on the partition?

---

### Post by ottosykora on 2012-02-01
@hakuna matata

>Instead, I just never use FAT32, unless required to,<

well there are well known reasons to use fat32 on multiboot systems.
As kind of 'exchange' partition between linux and windows.
Files on ntfs have ownership and permissions given, often this is a problem when such file should be used by linux.
Files stored there by linux may be only partially used by windows often.

Use fat32 in such case. Permissions are removed from all files automatically on fat32 and so you can use them on both systems.

Therefore on all multiboot system I ever had, I have at least one fat32 partition which is the most universal file format for current operating systems.

---

### Post by ottosykora on 2012-02-01
@engineeringtech

did you just try all the usual things like chkdsk/scandisk from windows, see if the partition showns any problems there?

---

### Post by Engineeringtech on 2012-02-01
> **ottosykora said:**
> @engineeringtech

did you just try all the usual things like chkdsk/scandisk from windows, see if the partition showns any problems there?

Yes, no problems found from the Windows side of thing.  I even tried my Windows based partitioning tool, and that reports no problems.   

As I said earlier, I find it unusual that GParted sees the formatted Fat32 Windows partition, but the "Disk Utility" found under the System Administration pulldown only sees 105 GB of unallocated space.   I am tempted to use the GParted tool to "check and repair" the Fat32 partition, but it warns me about loss of data.  This is a working multi-boot, and I don't want to start from scratch.

---

### Post by ottosykora on 2012-02-02
well then make an image from all partitions first, I use some commercial tools for that, you can take clonzilla if you want. Export those images to external drive or some dvd media etc. That means you have compete backup of all when something goes wrong.

I do not remember any failure of the  repair of the fat32 as this is rather stable thing.

---

### Post by Engineeringtech on 2012-02-02
> **ottosykora said:**
> well then make an image from all partitions first, I use some commercial tools for that, you can take clonzilla if you want. Export those images to external drive or some dvd media etc. That means you have compete backup of all when something goes wrong.

I do not remember any failure of the  repair of the fat32 as this is rather stable thing.

I have a tool to make drive images, but it is pitifully slow, and the only time I tried to do a restore, it didn't work.   So I will keep asking if anyone else has any ideas why this partition (Windows) shows up in Gparted, but I can't get to the files.

---

### Post by ottosykora on 2012-02-03
well we all use partition image tools and they are slow because they have to store and compress lot of data.
If you have no time to make backup, well then you better do not use any computers at all.

Take clonzilla live cd or the one partedmagic , there is clonzilla on it, make backup.
We all do this, so there is no reason why you should not do it as well.

If you do not want make backup, then fix the partition and if data lost, do not complain. Before ANY operations on system like changing something on file system or partitioning, a backup of all which has any importance to you is absolutely essential.

BTW: what backup tool are you using which does not work?

---

### Post by varunendra on 2012-02-03
Ahem...., just a tiny little question, sorry if it proves me ignorant (yes i didn't go through all the posts as most of them seem a bit 'off-track' to say the least). Is it a WUBI installation? If so, the 'host' windows partition can be found in **/host** directory.

---

### Post by ottosykora on 2012-02-03
> **varunendra said:**
> Ahem...., just a tiny little question, sorry if it proves me ignorant (yes i didn't go through all the posts as most of them seem a bit 'off-track' to say the least). Is it a WUBI installation? If so, the 'host' windows partition can be found in **/host** directory.

it seems to be an ordinary ext4 partition where the linux is on.
But thanks, very good point!

---

### Post by Engineeringtech on 2012-02-14
> **ottosykora said:**
> well we all use partition image tools and they are slow because they have to store and compress lot of data.
If you have no time to make backup, well then you better do not use any computers at all.

Take clonzilla live cd or the one partedmagic , there is clonzilla on it, make backup.
We all do this, so there is no reason why you should not do it as well.

If you do not want make backup, then fix the partition and if data lost, do not complain. Before ANY operations on system like changing something on file system or partitioning, a backup of all which has any importance to you is absolutely essential.

BTW: what backup tool are you using which does not work?

I don't ever try to backup my OS partitions any more, because I've never had a successful restore.   Regardless of the tool I used.    

I'll have to get back to you and this thread later.  Right now, I can't even get to the affected computer.   I am in and out of the hospital for tests.   Sorry to be such a pain.

---

### Post by Engineeringtech on 2012-02-14
> **ottosykora said:**
> it seems to be an ordinary ext4 partition where the linux is on.
But thanks, very good point!


My Ubuntu partition is on EXT4.  The Windows XP partition is on FAT 32.  I have separate partitions for the swap files for both OS's.

---

### Post by Engineeringtech on 2012-02-14
> **varunendra said:**
> Ahem...., just a tiny little question, sorry if it proves me ignorant (yes i didn't go through all the posts as most of them seem a bit 'off-track' to say the least). Is it a WUBI installation? If so, the 'host' windows partition can be found in **/host** directory.

Pretty sure this is not a "WUBI" installation, because I have no /host directory.   What IS a WUBI installation?

---

### Post by varunendra on 2012-02-14
> **Engineeringtech said:**
> What IS a WUBI installation?
It is the installer that runs from within windows (that is, you run it as an application while you are booted into windows), and installs ubuntu as an application in windows. It is a safe method to 'try' ubuntu, but not recommended for a long term use due to its limitations and inferior performance. Details here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
and
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But anyway, I was wondering about one more thing. In your first post, you said gparted can see the partition, while disk utility can not. Can we see the screenshots of both? I was also wondering (although doesn't seem relevant), what is that HFS partition (sda10) in the last, since you said you have only 'one' data partition that is ntfs.

Wish you good luck and good health!

---

### Post by Engineeringtech on 2012-12-29
I'm marking this thread (and others I opened on the same problem)  as "SOLVED" so people don't waste more time with it.  My solution is to go back to Windows.  I had hoped to stay with Ubuntu, but these problems have tormented me for a long time.   A computer is not very useful when you don't have any access to the drives.   Anyway, I want to apologize to the people here for my failure to respond promptly to their suggestions.  Whenever the advice started to dry up on a thread, I opened a new thread, pursuing a new approach to the same problem.  Eventually, I had so many threads opened, that I could not follow them all.    All the while I have been dealing with health and work problems, and that didn't help.   

I thank all the people who tried so hard to help me.

---

