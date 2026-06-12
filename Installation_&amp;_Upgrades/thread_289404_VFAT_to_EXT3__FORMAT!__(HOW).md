---
title: "VFAT to EXT3:  FORMAT!  (HOW?)"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Jack Jebedee on 2006-10-30
I made the jump from Dapper to Edgy and lost my two VFAT auto-mounted hard drives.  I'm not too upset yet because I find that I haven't used Windows in nearly a year, so I'd like to format the Windows drives to EXT3.  But there's a problem.

Drive 1 is EXT3, my boot drive.  Drive 2 is its VFAT twin and it's empty.  Drive 3 is my BIG VFAT drive and that's half full.

I'd like to EXT3-format Drive 2, then move files from Drive 3 to Drives 1 and 2 temporarily.  Then EXT3-format Drive 3 and move files from Drives 1 and 2 back to Drive 3.

Finally, I would like to mount EXT3 Drive 2 so that it's available to all users.  I would like to mount EXT3 Drive 3 so that only I can see it.  (I'm UID 1000.)

I'm desperately looking for hints in the Ubuntu Guide, but I can't find much there.  If you know of one or two good sources of information, would you please send a URL in my direction?

Thanks very much!

... JJ

Oh, here's a printout of the drive status right now:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        3649    29302560    f  W95 Ext'd (LBA)
/dev/hdb5               2        3649    29302528+   b  W95 FAT32

Disk /dev/hdd: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       12161    97683201    c  W95 FAT32 (LBA)

---

### Post by wieman01 on 2006-10-30
Honestly, the easiest & safest out of this situation is getting hold of a big backup device (external HD). When you are moving files & reformat the partitions, you need to make backups anyway... I would not recommend without properly securing your data.

So use an external driver, make a backup of your files & data, then reformat & copy all file over to the new (ext3) partition.

_**EDIT 1:**_
As for sharing partitions & making them read-only, etc. that's fairly simple by changing permissions & ownership (chmod, chown, chgrp). But that's one step ahead.

_**EDIT 2:**_
Reading your post again... Does your question only relate to the permission settings of the drives or also to the reformating issue? You seem to know how to reformat your drivers & move the files. Use "GParted" (= Gnome Partition Editor) to format your partitions.

---

### Post by MyAnda on 2006-10-30
dont know of a url right off but the man pages for the following should get you going

fdisk (have a look at your partitions)
mkfs.ext3 (to reformat)
fstab (getting it mounted/remounted at reboot)
chmod & chown (adjust perms for the right folks)

---

### Post by Jack Jebedee on 2006-10-31
Thanks for the pointers.  I found that I didn't have GPARTED, but Synaptic fixed that.  I formatted hdb1 in ext3 and then tried mounting it in FSTAB.  Nope.  Didn't mount.  I love the way DiskDrake (Mandrake Control Center) does GPARTED functions, but also mounts devices.

Dapper Drake mounted all hard drives automatically, which was very nice!  Edgy doesn't.  Is Edgy sacrificing functionality in a pursuit for more streamlined operation?

I probably need the new Ubuntu book.  Do you know if it has the entire lists of all possible SUID and UMASK entries?  I see people mentioning "UMASK=0007 does this and UMASK=0003 does that," but nowhere do I find a comprehensive list of all possible configurations.  If the new Ubuntu manual can offer that, I'm off to buy one!

... JJ

---

### Post by MyAnda on 2006-10-31
what were the errors when trying to mount? 
did you try to mount it manually?

---

### Post by Jack Jebedee on 2006-11-01
> **MyAnda said:**
> what were the errors when trying to mount? 
did you try to mount it manually?

Mount it manually?  You bet!  And I'm talking using a jack and a hand pump.  (If I knew how to mount it UNmanually, I'd have tried that first, but I haven't been able to find a clue.

Here's what my **fstab** looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7b88ddb2-d0d0-49ed-99a5-a41fa25bd594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d3a0a4ea-fa8c-4e24-bec8-c06245cf6d19 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb	/media/data	ext3	defaults	0	0
/dev/hdd	/media/archive	vfat	rw,user,umask=0000	0	0

If it looks like some bonehead noob made up the last two lines, you are right on target.  That was me.  Otherwise, everything in **fstab** is pure Ubuntu.

If you come up with a better way to do the last two lines, I'd dearly love to know where you found the documentation that covered the syntax.

Thanks _very_ much!

... JJ

---

### Post by MyAnda on 2006-11-01
you need the partition number for in the device portion

e.g.
/dev/hdb /media/data ext3 defaults 0 0  change to 
/dev/hdb1 /media/data ext3 defaults 0 0

I should have been more clear...what I meant by manually was
from a terminal type "sudo mount /dev/hdb1 /media/data" and see what happens...if it does not compalin...type "mount" and look for it in the list/ouput...the line should also give you an indication of the right stuff to put in fstab...other than the missing partition numbers what you have looks ok to me...but I am no fstab guru...

---

### Post by Jack Jebedee on 2006-11-01
> **wieman01 said:**
> 
Reading your post again... Does your question only relate to the permission settings of the drives or also to the reformating issue? You seem to know how to reformat your drivers & move the files. Use "GParted" (= Gnome Partition Editor) to format your partitions.

I can't believe it.  I actually got the drives both working thanks to a hint from MyAnda, but then I went back to correct something and the EXT3 drive disappeared.

GPARTED worked perfectly doing the EXT3 format.  I even mounted it and it showed up in Nautilus but unlike the VFAT drive, it didn't put its hard drive icon on the desktop.  Never mind.  I copied a few files to it, but I was abruptly stopped because I didn't have permission to do that.  So I removed the DEFAULT comment and inserted "RW, UMASK=0000 and whatever else I had on the same line for the VFAT drive.  Ubuntu didn't recognize the drive at all.  The only thing I have listed in Nautilus is the boot drive and the VFAT drive.  (VFAT lets me read and write, by the way.)

Then I had to leave for work, so my "upgrading" (if that's what I'm doing by trying to get my hard drives back) will have to wait until I return home.

I love Edgy's rounded corners and it seems to boot a bit faster than Dapper.

When I have this situation worked out, all 3 drives will be EXT3-formatted.  The score now is 2 down, one to go.  Drive 1, the boot drive, and drive 2, the data drive, will be available to anyone to read, write, execute (anything that doesn't require root access).  The third drive -- the archive -- is all mine.  That's where I store music, photos and documents that I don't want anyone to mess with.  When any user other than JJ logs onto my computer, they won't even see the third drive.  That one is just for me.

Excuse me now while I look for documentation.  And thanks!

... JJ

---

### Post by Jack Jebedee on 2006-11-01
> **MyAnda said:**
> you need the partition number for in the device portion

e.g.
/dev/hdb /media/data ext3 defaults 0 0  change to 
/dev/hdb1 /media/data ext3 defaults 0 0

[COLOR="Navy"]Good Heavens!  What the heck was I thinking?  This might have been my third or fourth FSTAB incarnation and I left the HDB number off.  I went back after reading this and found that I had no HDD number, either!  I corrected both mistakes and suddenly the hard drive icon for the VFAT drive (HDD1) appeared on the desktop, just as it used to be in Dapper.  Hallelujia!  The EXT3 drive didn't appear on the desktop, but I found it listed in Nautilus so I tried copying files to it.  No, sorry.  I don't have permission to do that.  Oops!  So I went back and changed the HDB1 line to match the HDD1 line (leaving EXT3, of course, but changing the options).  That that didn't work.

I had to leave for work then, but I'll take up the challenge again when I get home.

I explained in an earlier note how I'd like to arrange the drives and their permissions.  All drives will be EXT3, the first two drives will be for everyone's use (excluding only root functions) and the last drive will be for me only.  It won't ever be available to them.  They won't even know it's there.[/COLOR]

> I should have been more clear...what I meant by manually was from a terminal type "sudo mount /dev/hdb1 /media/data" and see what happens...if it does not complain...type "mount" and look for it in the list/ouput...the line should also give you an indication of the right stuff to put in fstab...other than the missing partition numbers what you have looks ok to me...but I am no fstab guru...

[COLOR="Navy"]This is terrific, MyAnda!  I didn't know we could do that.  I've been making changes to FSTAB, then I'd reboot the computer to see what difference the changes made.  Who knew that there was an easier way?  No, I mean ***_besides_*** you.  This is great news!  My troubleshooting just got a whole lot faster, thanks to your advice.

I think I need to sit down with a copy of the new Ubuntu book to see if it has a list of all the things I'd need to know to be able to configure FSTAB without much need for help in the forums.  (That includes all the other FSTABs in Gnu/Linux that go by different names but require the same table-specific knowledge and reference requirements.)

Then, when I get this housekeeping out of the way, I can start getting into deeper things, like putting various desktops on the sides of a cube and turning my screen into wall-to-wall eye candy.  I'm amazed at what some Ubuntu users are doing with their machines.  It's enough to make Wild Bill Gates turn green with envy.

Thanks very much for the help, MyAnda.  I appreciate it.

... JJ[/COLOR]

---

### Post by MyAnda on 2006-11-02
glad to hear that you are on track! good luck, it is certainly a fun and worth while ride! 
you probably already found this...but it looks like a good read
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Jack Jebedee on 2006-11-02
> **MyAnda said:**
> glad to hear that you are on track! good luck, it is certainly a fun and worth while ride! 
you probably already found this...but it looks like a good read
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Did I leave you thinking that I was on track?  Sorry...  Maybe I was just being optimistic.

Actually, I'm in **WAY** over my head, but I don't think I'd get particularly upset about it as long as I don't lose any data.  (I don't have enough CDs in the house to back everything up that's on the hard drives.)

I got home last night and printed out fstab:

> fstab:

/dev/hdb1	/media/data	ext3	rw,user	0	0
/dev/hdd1	/media/archive	vfat	rw,user,umask=0000	0	0

I thought I left it with DEFAULT in the HDB1 line, but maybe I typed it in this way when I found out that I couldn't actually write to HDB1.

Enter "mount" in terminal and read:

> mount:

/dev/hdb1 on /media/data type ext3 (rw,noexec,nosuid,nodev)
/dev/hdd1 on /media/archive type vfat (rw,noexec,nosuid,nodev,umask=0000)

Did I *_really_* mean to say all that?  Never mind...  I'm on full speed ahead and I'm not going to let that little problem trouble me.  I use gksudo to get back there and put it right, just because I read about the gk and it seemed awfully convenient.  [COLOR="DarkGreen"]Gnome[/COLOR] spoke:

> gksudo gedit /etc/fstab
(gedit:4983): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then I decide to change the properties of hdb1 so that it will let me write to it.  I mean, it says that [COLOR="Sienna"]root[/COLOR] owns the drive and everything on it (which, at the moment, is Lost & Found) and [COLOR="Sienna"]root[/COLOR] apparently doesn't like me copying files onto its turf.  I think I'll change the ownership (only because I can't think of an alternative) of hda1 from [COLOR="Sienna"]root[/COLOR] to [COLOR="DarkOrange"]jebedee[/COLOR].  If I own that drive, I'll be able to write to it as much as I like!  But then [COLOR="DarkGreen"]Gnome[/COLOR] speaks again:

> gksudo nautilus
(nautilus:7101): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:7101): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

Despite the dire warnings (that I don't understand in the slightest) from [COLOR="DarkGreen"]Gnome[/COLOR], I copy files from hdd1 to hdb1.  Then I move files from hdd1 to hda1.  It's a tight fit on hda and hdb drives, but it worked!  Then I fired up GPARTED to unmount and format hdd1 to EXT3.  Then I remounted hdd1 and tried moving files back to it.  Nope.  I'm not allowed to write anything to hdd1 now that it's ext3-formatted.  That's the very same thing that happened with hdb1.  Weird.  Then it was time to go back to work again.  I did a gksudo nautilus trick again as I was leaving, having Nautilus move hda1 files back to hdd1.  Tonight I'll have Nautilus move files from hdb1 back to hdd1 before I go to bed.  Then tomorrow I'll see if I can put something in FSTAB that means, "Root can own this drive, but I want to read/write/execute on it whenever I like."

Thanks for the heads-up about the good read, MyAnda.  But let me give you just a quick sample of what we can find there:

> umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
to set permissions of 700, umask=077

Is **any** of that supposed to make sense to me?  I suppose it's useful to someone who knows what permissions of 700 and 777 are, but to someone who just sat down with "How can I get two of my hard drives to be friendly with everybody and one of them to be friendly with only me?" on his mind, a discussion of 700 and 777 doesn't make interesting conversation.

Note:  I've never tried to do any of this in an operating system other than Ubuntu Gnu/Linux.

I think I need to put DEFAULT back in the ext3 lines of FSTAB when I get home tonight, then begin again from there.

Thanks for the help, MyAnda.

... JJ

---

### Post by MyAnda on 2006-11-03
some links about perms (chmod (change mode/permissions) and chown (change owner))
[http://www.december.com/unix/tutor/permissions.html](http://www.december.com/unix/tutor/permissions.html)
[http://www.opengroup.org/onlinepubs/009695399/utilities/chmod.html](http://www.opengroup.org/onlinepubs/009695399/utilities/chmod.html)
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

you could leave the fstab options at default and limit access at the directory level
e.g. 
```
sudo chown -R jebedee /media/data
``` (or whatever dir) ...means make the user jebedee the owner of the data directory and all the stuff inside it
```
sudo chmod -R 700 /media/data
``` ....means allow the owner (jebedee) of the data dir and everything under it to read,write,execute (7) anything and don't let anyone else (00 group or other) read,write or execute anything (of course, root still can)

don't know if you have come across it yet but you may find ```
df -h
``` handy for seeing how much space is being used on mounted file systems
if you don't mind, post the ouutput of df -h so I have an idea of what all is there

---

### Post by Jack Jebedee on 2006-11-03
> **MyAnda said:**
> some links about perms (chmod (change mode/permissions) and chown (change owner))

Reading it today makes a LOT more sense than it did yesterday!  I see the what and why behind the 700/777 values.

Last night was an adventure.  Turns out that I didn't have DEFAULTS listed in FSTAB for hdb1 and hdd1, so I changed those.  Forget any other options.  Let's start with a clean DEFAULTS and proceed from there.  I was reading yesterday about mounting a drive in the /home directory, so I did that with hdb1, then I mounted hdd1 in the /home/jebedee directory.  A few minutes later, Ubuntu forgot who I was:  "/home/jebedee doesn't exist."

Oops!  I couldn't get back to FSTAB to correct my mistake.  I couldn't get anywhere with the Ubuntu install CD.  I'd actually booted to the CD for a second time -- but had the BIOS set to boot from hda1 -- with an intent to re-install Ubuntu when I had a closer look at the boot options.  I'd already tried the third option that let me boot into recovery mode, but I couldn't do anything worthwhile there to get FSTAB back the way it should be.  But this time I saw the entry below it:  Boot into Terminal in recovery mode.  No way!  I did.  I fixed FSTAB and everything turned out fine after I put the mount points back to where they were.

Then sudo nautilus, right click on hdb1 and hdb2, then on the Properties button, let me change ownership back to root, but also allow the jebedee group (Who knew that there's a jebedee group?) and everyone else to r/w/e on hdb1.  The owner of hdd1 was already root, so I left it there and gave the jebedee group r/w/e privilege, but gave everyone else none/none.  Cool!  I then switched over to my good wife's account (that I put in so that she can play cool games that aren't available on her what's-it XP machine) and accessed hdb1.  No problem!  Read-write worked like a champ.  I deleted a directory.  It works!  I noticed that hdd1 isn't listed on her desktop as it is on mine.  So I went into Places and hunted down hdd1 with Nautilus.  Aha!  I found it!  I clicked on it and a warning came back telling me that I'm not authorized to access hdd1.  Perfect!  That's EXACTLY what I want it to do!  Life is good!

So this problem is solved, thanks to you, MyAnda.  I'm saving those CHOWN references you gave me so that this won't take NEARLY as long next time.

My next project:  Get my ATI 9200 to do 3D acceleration.  I know there's a driver that sounds like FGLRX that should do that, but the last time I used it, the Breezy desktop disappeared forever.  Rather than re-install Ubuntu, I waited six weeks and installed Dapper.  Then I followed directions for FGLRX as soon as that installation was done so that, if Ubuntu imploded, I wouldn't lose anything.  Nope.  The OS didn't implode.  The only thing that happened differently with the FGLRX driver installed was that I was able to see a string of errors when checking whether 3D acceleration was working.  Before FGLRX installation, I just got "No."

I wonder if there's a way to back up Ubuntu so that I don't lose any configuration settings the next time the boot drive turns into road kill.

Are we having fun yet?

... JJ

---

### Post by MyAnda on 2006-11-06
sounds like fun! glad to hear you are brave enough to bring your wife into it...my wife has been on a linux desktop now for about 2 years and does not want to go back! good luck!

---

