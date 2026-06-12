---
title: "dual boot install probs 7.04- diff HowTo guide"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by coolhandluke on 2007-05-10
Hi. I (obviously) cant find a similar thread anywhere - so here goes.
The HowTo guide refers to DDrake and noted 'later versions should be similar', but the install process for FFawn is a little diff - right at the crucial formatting stage. Obviously, I dont want to get that part wrong.  Steps are:
Welcome - language (english)
Where are you - (NZ)
Keyboard - (US)
Prep Disk Space - [starting partitioner]
    options - guided (entire disk) or manual
-- I select manual, >FORWARD
Prep Partitions - [scans disk]
   Device: \dev\sda1\  - Type: ntfs  - Mount Point: \media\sda1 - Format: [not checked]
-- Selecting  this device and >FWD returns error: "No root file sys" and the EDIT PARTITION option only allows me to change the format of the entire disk!

So, the main diff is there is no 'resize" etc.
I've tried using Gparted to pre-set up some partitions but this returns: "An error occured...[Resize] could not be applied to disk]".

Any help would be much appreciated. Its taken me about 10 hours and many work-arounds to get to this stage and I dont want to give up now...!
Cheers
I've also read (forums) that Gparted should no longer be required with 7.04...?

Apologies: this thread should be in 'Absolute Beginners'.
Possible link to this thread [http://ubuntuforums.org/showthread.php?t=439395](http://ubuntuforums.org/showthread.php?t=439395)

---

### Post by confused57 on 2007-05-10
It "may" just be a matter of needing to defrag your Window's partition, preferably a couple of times?

---

### Post by jerrylamos on 2007-05-10
If you want to resize your Windows partition, then you have to defrag, then you have to go into control panel system and set virtual memory so there is no paging otherwise there's a big swap file allocated up high.  Then defrag again and look at defrag details very closely to calculate how much if any free space is left at the top.  Shut Windows down doing nothing more, and bring up Gparted on CD Live.  You can resize Windows removing only the clear space at the top if you have it calculated correctly.  Windows uses the "scatter" principle in allocating files..  After resizing, bring Windows back up to see if it will work, and then use control panel system virtual ... to enable some paging.

Do note Windows wants to be the first partition on the first hard drive.

Cheers, Jerry

---

### Post by coolhandluke on 2007-05-11
Seems to be a problem with me being able to resize, either using the install's 'automated' facility or using Gparted. In Gparted, I can resize (from 40Gb to say 20 - even though XP only requires about 13) but when I APPLY, it errors with no details.
So, yep, I've defrag'd a few times and now a few more. And reduced the page file. And rebooted. (The XP defrag window shows a small amount of 'blue' files on the right - but I've  assumed that 'visual scattering' of data isn't a literal portrayal of how that data is stored on the HDD - so that shouldn't be affecting the resizing of free space...?)

If I use the 'Guided-Use Entire Disk' install (which would automatically assign partitions to free space?), I get in the following:
"WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap"

But this states formatting of 'partition #1 of SCSI1' - and my understanding is that partition 1 is (almost always) Win(XP) - so definitely the wrong option..1

So, something is preventing me from resizing. Buggered if I know what it is.
I'm using a laptop (and only one hard drive). Perhaps that's complicating things - a specific block of memory that isn't showing..? Just a thought.

The links provided don't seem to allow for this scenario as I get none of the options that the UserDocs/HowToGuides show.

Any other ideas?
Cheers again...

---

### Post by msandersen on 2007-05-14
Try using the built-in Disk Manager in XP (Control Panel -> Administrative Tools -> Computer Management) to resize the Windows partition, then run the Installer and install into the empty space. Should also minimise any trouble you might get from resizing Windows partitions from Linux.

---

### Post by coolhandluke on 2007-05-28
Bit of a break but back into it...

It sounds like adjusting the partition outside of Linux might be worth a try.
Cheers

---

### Post by coolhandluke on 2007-05-29
Ok. Comp Management isnt letting me make any changes either ('format' options etc are grey'd out).
I have a 40GB hard drive - which Disk Mngmt shows as being 66% free - but when I use DiskPart (command line), that shows me: Free=0.
It would seem that XP will not let me repartition, unless I try (buy) Partition Magic, and that's not certain either.  Also the Microsoft forums (MVPs) state that its not possible to change the size of an existing Windows partition without deleting the data within.

---

