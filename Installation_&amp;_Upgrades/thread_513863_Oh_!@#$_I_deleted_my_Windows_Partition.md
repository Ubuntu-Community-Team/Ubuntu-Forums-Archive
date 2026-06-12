---
title: "Oh !@#$ I deleted my Windows Partition"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by thr33m on 2007-07-31
I'd really appreciate any help and please speak in lamemans terms for me..I'm new to all this.

Okay so this is mostly all my fault..I should have backed my stuff up and shouldn't have been doing these things on this computer :( 

So I had a perfectly running dual boot ubuntu/xp going on but I realized that I made the ubuntu partition size way too big and the xp size way to small...So I delete the ubuntu partition with Magic Partition

Next I go in to try to install ubuntu and dumb ol' me sets the ubuntu partition too small so that it can't fully install. 

So after I restart I see that nothing is working and it just gives me an error (I can't really recall the error at this moment, sorry).

So then I go and reinstall a 64 bit version of ubuntu to see if that will fix things and It works (I'm on it right now) but my windows partition is completely gone. 

I have extremely important documents on my windows machine but I can't afford to pay for a professional data recovery person.

Any suggestions are appreciated. I only really need a FEW folders from that computer and then I can reinstall XP. 

Any help what so ever is greatly appreciated,
Mike

---

### Post by HermanAB on 2007-07-31
Hmm, this is not a simple problem and writing to the disk will just make things worse.

I suggest that you retrieve your docs by emailing all the people that you may have ever emailed to and ask them nicely to email you all attachments you ever sent them back.

Next time you wish to experiment on a nice working system, use VMware - it is free.  Then you can experiment in a virtual machine without screwing up the real machine.

Cheers,

Herman

---

### Post by thr33m on 2007-07-31
That's the problem, these docs are created by me and the only copies are on this computer. 
I will not write any files to this computer until I fix this problem. I have noticed something that gives me a bit of hope...

I opened up Gnome and I can see my old windows partition but it reads "UNKNOWN" on the right of it and if I see the properties it says... 

Unadble to detect filesystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to Gparted
-There is no filesystem available (unformatted)

So it still seems like my partition is there but the computer doesn't know what to do with it. Is there any way I can go in and browse that partition (it doesn't show up in Places>Computer) so I can copy things to an external drive. Or better yet, how can I restore it to it's regular state? 
The windows partition isn't grouped with the rest of the partitions..

Sorry if I confused you...I don't really know what I'm talking about.

Any help is greatly appreciated

---

### Post by aquavitae on 2007-07-31
Are you sure you've actually delete the windows partition and not just the boot loader?  If you tried installing ubuntu and failed, chances are it overwrote the windows boot loader, but it shouldn't have touched the partition.  You can try to repair it using the windows installation disk or Super Grub Disk ([http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/)).  Give this a try.

---

### Post by thr33m on 2007-07-31
Hey aquavitae,
Thanks a lot for the help..It ALMOST worked (I think). I'm not really sure how to use that program but I did try to restore the file and then it actually *tried* to boot but it said Operating System not Found (or similar). But at least at tried!!

I am thinking that the operating system is actually gone (which is no biggy). I just really need those files...I know they are still on the HD. is there any way to browse those files through ubuntu or somthing like that?


Any tips on using super grub?

Any other suggestion are greatly appreciated.

---

### Post by HermanAB on 2007-07-31
If you can see the windoze partition, then it is still there, but just not mounted.  You have several options:

You can run 'fdisk /mbr' from a DOS/Windoze floppy/CD to fix the Master Boot Record. That will cause Windoze to boot and 'kill' Ubuntu, then you can re-install Ubuntu again: [http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

You could mount the Windoze partition using a Knoppix CD and backup all your schtuff to put your mind at ease.

You can manually figure out which is the unmounted partition and mount it manually:
Use 'ls /dev' to see the 'hda1..n' or 'sda1..n' partitions. 
Use 'mount' to see which of the above are mounted already.
Whatever isn't mounted (likely hda1) must be windoze.

Make a mount point for windoze:
mkdir /mnt/win

Mount the suspected Windoze partition (most probably hda1):
mount -t ntfs /dev/hda1 /mnt/win

Look at it to see what is there:
ls /mnt/win

'Hope that helps!

Herman

---

### Post by aysiu on 2007-07-31
One of these links might help:
[http://ubuntuforums.org/showpost.php?p=1988280&postcount=3](http://ubuntuforums.org/showpost.php?p=1988280&postcount=3)
[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

---

### Post by thr33m on 2007-07-31
Hey herman, thanks
I'm kind of confused where to insert those commands to though?? 


Thanks for all the help guys, I really appreciate anything more you could add

---

### Post by aquavitae on 2007-07-31
Open a terminal (from the ubuntu menu), type the following commands and post the output (it might ask for your password):
```
sudo fdisk -l
cat /etc/mtab

```

---

### Post by thr33m on 2007-07-31
Okay thanks,

I get this:
/dev/sda1   *           1       35728   286985128+  83  Linux
/dev/sda2           35729       35772      353430    5  Extended
/dev/sda3           35773       36481     5695042+  83  Linux
/dev/sda5           35729       35733       40131   82  Linux swap / Solaris
/dev/sda6           35734       35772      313236   82  Linux swap / Solaris

It is the one with the most blocks (/dev/sda1) but it says it is a linux OS. Is there any way (with the xp install disk) to install xp with that same data? I get the feeling my xp OS is lost because this is an HP machine and HP likes to partition a 10GB area in your hd for all the system files, I think that may have gotten deleted ...But i'm still not sure.

What to do next? (sorry for being such a newbie at this :mad:)

---

### Post by aquavitae on 2007-07-31
When you installed ubuntu the second time, how did you tell it to partition your disk, and what partitions were on it before?  It looks like xp partition is gone, sorry, but lets make completely sure.  Where are your partitions mounted? Can you post the output of cat /etc/mtab?  I asssume you do only have one hard drive?

---

### Post by thr33m on 2007-07-31
The results are this:

/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

And I'm 95% sure i'm runnning under one HD...

I have also attached a screenshot of my Gparted. 


Thank you so much for your help!

---

### Post by aquavitae on 2007-07-31
It doesn't look like you're actually using /dev/sda1 (which is good), but I see that gpart doesn't recognise the filesystem, although fdisk does.  It may be that fdisk is just makeing a guess, in which case it is possible that the fs id in the partition table is messed up, but that the partition is still ok.  To fix that, you'd have to change the filesystem type in the partition table without actually recreating the filesystem (which will just wipe everything).  I think this can be done with fdisk, but I'm not sure how.  Just having a look on google, I'll post again when I find out how.

---

### Post by stinger30au on 2007-07-31
in worst case scenerio you could take you hdd and plug it in to another pc as a slave hdd and acces it like that as well

---

### Post by aquavitae on 2007-07-31
Just had an idea - can you mount the partition as ntfs (I assume it was ntfs under windows, not fat?)  Open a terminal and enter the following, if there is any output before the last command, post it:
```
sudo mkdir /mnt/sda1
sudo mount -v -t ntfs /dev/sda1 /mnt/sda1
ls /mnt/sda1

```

---

### Post by aquavitae on 2007-07-31
> **stinger30au said:**
> in worst case scenerio you could take you hdd and plug it in to another pc as a slave hdd and acces it like that as wellDon't think that would help - it looks like the problem is on the hard drive, not the system.

---

### Post by thr33m on 2007-07-31
hey aquavitae,
when I type that into terminal I get this:

mike@desktop:~$ sudo mount -v -t ntfs /dev/sda1 /mnt/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have no clue what that means but i'm going to restart to see if anything happends and I will keep you updated.

Again, I appreciate your help!
Thanks

Edit: Nothing out of the ordinary happened when I restarted

---

### Post by AnRa on 2007-07-31
You can use Test-disk with [System Rescue CD](http://www.sysresccd.org/) to recover your files! ;)

---

### Post by aquavitae on 2007-07-31
> **thr33m said:**
> hey aquavitae,
when I type that into terminal I get this:

mike@desktop:~$ sudo mount -v -t ntfs /dev/sda1 /mnt/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have no clue what that means but i'm going to restart to see if anything happends and I will keep you updated.

Again, I appreciate your help!
Thanks

Edit: Nothing out of the ordinary happened when I restarted
All it means is that it won't mount as ntfs because the partition table says its something else.  I've found out that you can change the filesystem type without formating using fdisk, or cfdisk for a slighly nicer interface.  I haven't used cfdisk before so I'm not sure exactly how it works, but its a terminal app and should be fairly straight forward.  I suggest you open a terminal and type 'cfdisk' to start it.  Hopefully you'll be able to work it out yourself - I'm not at linux atm, so I can't check how it works.  You need to change the filesystem type.  If you get stuck post back and I'll see if I can help.  Be sure you're on the right partition thought!

---

### Post by Herman on 2007-07-31
[TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstrated
              [CENTER](Last Edited on Friday the 13th!)
[LEFT]Regards, Herman :)
[/LEFT]
[/CENTER]

---

### Post by thr33m on 2007-07-31
Hey thanks aquavitae and Herman..
I will try your suggestion tomorrow when I wake up (it's 4:30am GAH!).

herman, what exactly will testdisk allow me to do in my situation?

also, with the proper procedures, would it be possible to get my win xp running back as normal (of course with an xp disk)? Is it probable that doing this will delete my ubuntu install (which I want because I want to install the 32bit version instead of 64)?

Thanks for the help!!

---

### Post by aquavitae on 2007-07-31
> **Herman said:**
> [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstratedLook's good!  I must remember this :).

---

### Post by thr33m on 2007-07-31
After I completed the steps on the testdisk page, what should I do next and what affect will it have on my OS's?

Thanks!!

---

### Post by HermanAB on 2007-07-31
Hi (other Herman here!),

1. What we learned so far:
a. It looks like you identified the correct partition sda1.
b. Sda1 has the most blocks and it is the first one.
c. Sda1 won't mount as ntfs since the filesystem type is wrong (83).

2. What you should not do, since it will cause data loss:
a. Don't repartition the disk.
b. Don't format sda1.
c. Don't write to sda1.

3. What you need to do:
a. Try to read the data without modifying anything.
b.IIF the above fails, modify partition table to identify sda1 as ntfs.

Fixing the partition table is not a simple matter, since most tools will create a new file system for you, they won't fix a screwed up one.

So, I'm still of the opinion that you should try Knoppix and see if it magically figures it out and can read sda1. Knoppix is also based on Debian, just like Ubuntu, but it has very good hardware detection capabilities.
[http://www.knoppix.org/](http://www.knoppix.org/)

Failing that, you should try BartPE and see what it reports.  You need a working Windows XP PC and a WinXP CD to make a BartPE CD:  
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

The above CDs should be in *every* system administrator's tool box.

Failing the above, remove the disk drive (probably SATA), plug it into another PC running WinXP and see what it makes of it.

If and only if all the above passive methods fail to read the drive, should you try to repair the partition table.

'Cheers,

Herman

---

### Post by HermanAB on 2007-07-31
BTW, this is one of the best rescue CDs:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

BUT - it can cause a loss of data and I haven't used this CD.  So far, I always managed to copy data off a bad disk using Knoppix or PartPE.

Cheers,

Herman

---

### Post by HermanAB on 2007-07-31
Note that Gparted is NOT the same thing as GNU Parted.  You probably want to use GNU Parted.

Cheers,

Herman

---

### Post by Herman on 2007-07-31
Hello [thr33m]("http://ubuntuforums.org/member.php?u=352817"), [aquavitae]("http://ubuntuforums.org/member.php?u=266046"), and [HermanAB]("http://ubuntuforums.org/member.php?u=44990") and all,
Here's what I think (hope) is pretty close to the correct situation, briefly. 

The first sector of our hard disk, is the space reserved for our hard disk's MBR. All hard disks can have an MBR, when they are formatted, and so can floppy disks and bootable CDs, even USB flash drives. 
The MBR can be divided into three main sections, there is a 2 bytes 55aa signature to indicate it's a bootable disk, that leaves 500 bytes for the other stuff.
There is a partition table which has room for as many as four partition entries, which are allowed one sixteen byte space each, so the partition table has a 64 byte area reserved for it in the MBR.
The rest of the MBR is left over for bootloader code, there is 446 byts left, which is way to small for an actual bootloader to fit into, so they just use a small 'pointer' called a 'stage1' which looks at the partition table for info and 'points' to the actual bootloader itself, either GRUB and its files in your Ubuntu partition or NTLDR and its files in your Windows partition, or some other boot manager or loader. There are also some other assorted small bits and pieces of code that are also placed in the bootloader area.

'"fixing" the MBR', or 'installing GRUB to MBR', or installing the stage1 for any other bootloader or boot manager to MBR doesn't affect the partition table part of the MBR, it only affects the bootloader stage1 sections of the MBR. 

Using partition editing software doesn't touch the bootloader code area of the MBR, but it does write to the partition table, of course, as you might expect. The partition table contains the information about where each partition starts and ends, and what sort of file system to expect in each partition. This part of the code is called a 'partition descriptor', and here's a link to a list of them, by Andries E. Brouwer, Partition types: [List of partition identifiers for PCs]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-1.html").
Here's another very famous link on this subject, also by Andries E. Brouwer [Partition Types]("http://www.win.tue.nl/%7Eaeb/partitions/").

It's my guess that this [partition descriptor]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-2.html#ss2.3") in your partition table is what seems to be your problem here that we hope TestDisk will fix for you.
>  herman, what exactly will testdisk allow me to do in my situation?Most software looks at the partition table for information and depends on the correct information being in the partition table.
 
TestDisk looks at your partition table first and tells you what's there. Then you can use TestDisk to scan your hard disk for the sectors that it thinks resembles the start sectors of file systems (partitions), and reports what it finds back to you so you can decide if it makes sense to have TestDisk write the information it has found to MBR for you.
If you want, you can make another scan and search deeper, for more obscure remnants of old file systems.

Normally that works, and your file system is recovered.

There may be times when people have re partitioned their disk many times (like most of my hard disks), and they have old start sectors for defunct partitions all over the place. Sometimes it is even possible to resurrect an ancient partition you haven't seen for years and recover files from it if that part of that has happened by good luck not to have been overwritten by new data.
Other times, the start blocks for the partition you just used yesterday may have already been overwritten by data or a new start block for a new partition. In that case you won't be able to recover the partition with TestDisk.
I would then look to TestDisk's companion program, Photorec, to try to recover your files directly without bothering to try to fix the partition table descriptor.

And sometimes, it isn't possible to *easily* resurrect an old partition with TestDisk because if you do it will overlap a newer, existing partition, so you may have to delete an existing partition first if you really want to recover your old partition. It helps to know the partition table rules for situations like that, meaning we can have up to four primary partitions or three ordinary primaries and one extended which can be sub divided into many logical partitions as we like. (Quite a few anyway). But I don't think your particular situation will be too complicated. Yours should be perfectly straightforward and simple.

As long as your first partition really still begins with the start sectors for an NTFS file system TestDisk will be the correct program for you. but, If you accidentally slipped up (goofed) and created an ext3 partition over the top of your old NTFS partition then try Photorec. That should at least recover your files.
>          After I completed the steps on the testdisk page, what should I do next and what affect will it have on my OS's? You should make a backup of important files in Ubuntu first, just to be sure.
Hopefully, you will be able to fully recover your Windows operating system 100% as it was before, because I don't think it has even been touched, only the file system descriptor in the partition table in the MBR, which is not a part of the Windows file system at all. The MBR is a long way from your Windows partition.

I'll be back in a few days, I have to go away camping as part of my job, and I'll be out of contact, so I wish you good luck and I hope it all goes well for you.

Regards, Herman :)

---

### Post by hytonen on 2007-08-02
Hi thr33m!
If you have another windows box you could allways unplug your HD from the crasched box and install EasyRecovery Professional - Trial Edition.
I found it usefull to recover files under NTFS/Fat16-32.

The link: 
[http://www.ontrackdatarecovery.com/data-recovery-downloads/#data](http://www.ontrackdatarecovery.com/data-recovery-downloads/#data)

The Trial version is ofcourse limited, but this is one solution.

Wbr: Jan

---

### Post by thr33m on 2007-08-02
Okay guys, I'm back with more disaster!!
I started to mess around with A LOT of stuff including grub disk and a lot of different windows boot CD's like BART. Doing this just got me into a huge disaster.

I sort of gave up and tried to install XP but when I do there are no partitions to choose from which then gives me a "setupdd.sys" error. AGH!

Then I try to re-install ubuntu- That doesn't work.
Trying to boot up my old ubuntu doesn't work either.

The only thing that seems to work is booting live CD's. So I have basically given up on my files- those seem long gone, I have messed with too much stuff. Oh well... :mad:
But the weird thing is, is that my harddrive always reads 270gb when really it's supposed to be a 300gb meaning my files are on there- just lost as hell. 

So I was wondering if there was a way to COMPLETELY wipe out my harddrive using ubuntu live cd or any other live cd I can download?  
I tried using GParted to delete all the partitions but it still doesn't seem to wipe it out completely.

Anything you can suggest?

Thanks guys, 
Sorry for all the trouble.

Herman, I read your post and I will attempt to use testdisk in the meantime...Thanks so much!

---

### Post by thr33m on 2007-08-02
Okay I'm trying testdisk and it seems like I could get something off of this... But I don't see my sda1 "partition", only my hda (linux) and it says this:

Note: Some disks won't appear unless you're root user.
Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

What should I do? I tried to go into GNOME and make a new partition but it gives me an error that says 

"The following operation could not be applied to disk:

Create Primary Partition #1 (ntfs, 273.69 GiB) on /dev/sda

See the details for more information"


I then tried to delete everything in the partition (with testdisk) and it won't allow me to, it says:
Write Error: Can't delete partition table (or something along the lines of that)

It seems like I can't access it for some reason. I also can't delete my old ubuntu partition through GNOME!

---

### Post by HermanAB on 2007-08-02
Well, first of all I don't think Ubuntu can create a NTFS file system.  I think its NTFS driver is a Read-Only driver.

Secondly, you cannot format or delete a partition that you are using and has mounted.  In order to use something like GNU Parted or Gparted, you have to run from a bootable CDROM.

---

### Post by Orky on 2007-08-02
What you should do:

Boot from a Live CD
Run as root:

fdisk /dev/hda

t (change type)
1 (hda1)
7 (ntfs)
p (print table)

If (and only if) it looks good (i.e. hda1 is now type ntfs) type:
w (write table)
q (quit)

This operation is reversible (just change the type back to what it was), so it should be safe, as long as you know what you're doing.

If I'm right, and you haven't formatted or written to hda1, you should have an intact bootable Windows XP partition with all of your files.

Beware though, you might have done something bad, like format it (unlikely, since it's not readable as an EXT2/3 partition), or done something bad with so-called recovery programs.

(One last question: What were you doing not paying attention to the partitioning program during the installation?)

---

### Post by merlinus on 2007-08-02
> 
I think its NTFS driver is a Read-Only driver.


ntfs-3g will allow you to read and write to ntfs partitions from ubuntu.  I do this often with no problems.

-merlin

---

### Post by aquavitae on 2007-08-03
I don't think you should be trying to recreate the ntfs file system - that will only overwrite whats there already.  You should be trying to change the partition table to reflect what it on your disk, as in orky's instructions.

---

### Post by Jeremywilms on 2007-08-03
Well...You have the licence so... I guess its legal for you to torrent it. If you still have your old CD-KEY its 100% legal as far as I know.

---

### Post by thr33m on 2007-08-03
> **Orky said:**
> What you should do:

Boot from a Live CD
Run as root:

fdisk /dev/hda

t (change type)
1 (hda1)
7 (ntfs)
p (print table)

If (and only if) it looks good (i.e. hda1 is now type ntfs) type:
w (write table)
q (quit)

This operation is reversible (just change the type back to what it was), so it should be safe, as long as you know what you're doing.

If I'm right, and you haven't formatted or written to hda1, you should have an intact bootable Windows XP partition with all of your files.

Beware though, you might have done something bad, like format it (unlikely, since it's not readable as an EXT2/3 partition), or done something bad with so-called recovery programs.

(One last question: What were you doing not paying attention to the partitioning program during the installation?)

Hey thanks orky! Although I'm not really sure what you want me to do.. Do you want me to try all of those commands or what?


To your last question: What happened was I didn't set the partition space for Ubuntu  high enough because the first time I set it WAYY too high :lolflag:

---

### Post by aquavitae on 2007-08-06
Orky's commands are a list to followed.  The first (fdisk /dev/hda) starts fdisk.  The rest (e.g. t, 1, 7) are commands that you enter into fdisk.  Just type the following exactly and you should go right (with reference to Orky's comments!):
```
fdisk /dev/hda
t
1
7
p
w
q
```
But do pay attention to the output as you go, especially after pressing p.

---

