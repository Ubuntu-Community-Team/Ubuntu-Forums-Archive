---
title: "1st boot GRUB error 18"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2007-08-16
I am installing this on a new 750GB hard drive. Ubuntu server from a CD. After a wile it ejects the CD and reboots. But will not boot up. It comes back like this:

> GRUB Loading stage1.5.


GRUB loading, please wait...
Error 18
_

I even did a full reinstall but it comes back the same.

This is on a Pentium III system with 1GB ram.

The 750GB hard drive is a SATA drive. But using a Serial ATA to Parallel ATA adapter

[It's this adapter]("http://www.cooldrives.com/saidecomisat.html")

It all installed good and Ubuntu seen it as a 750.2 GB hard drive.

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/Ubuntu-sees-750GB.jpg[/IMG]

Any one know what I can do to get it to boot?

-Raymond Day

---

### Post by merlinus on 2007-08-16
[FONT=Helvetica,Arial,sans-serif] 18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area.

Perhaps you can upgrade the BIOS?

-merlin
[/FONT]

---

### Post by Raymond Day on 2007-08-16
Wow that's good to know it's the BIOS.

It's a motherboard about from 2000 they don't make any new BIOS for it.

Can't GRUB just bypass the BIOS? The BIOS sees the hard drive as a 136 GB hard drive.

Is there any way to just have it by pass the BIOS.

Or in the BIOS I can Manual set the:

Cylinder
Head
Precomp
Landing Zone
Sector

But I don't know what numbers to set them 5 words too. Any one know for a 750.2 GB hard drive?

-Raymond Day

---

### Post by MQMike on 2007-08-16
It's usually not the BIOS.  That's a cryptic error, sometimes annoying.
Did you install GRUB to the MBR of that drive during the install?
That's Step 6 (of 6) using the regular Live CD Desktop version.  The advanced button in lower right.  You can specify where to have GRUB installed, which should be the MBR for your case.
Hard telling what it's called. Ubuntu is in sda1, right? First partition of sda?
Is that the drive hd0?
If so, specify (hd0) for GRUB (using the parentheses).

---

### Post by MQMike on 2007-08-16
Or, you can to simply re-install GRUB to that MBR from the Live Ubuntu CD, at a GRUB prompt.
See:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Qqmike aka MQMike)

---

### Post by Raymond Day on 2007-08-16
I am installing ubuntu server. Not the desktop.

I don't know I guess it installed it on the MBR. I mostly just auto installed every thing from the boot CD.

Put my name and password in and just like next, next, next. Told it to use the hole hard drive. It made a Swop and use the rest of the hard drive when it formated.

-Raymond Day

---

### Post by MQMike on 2007-08-16
OK.  That probably did put GRUB in the MBR of the drive you were installing to.
I must say I have no experience with servers at all.
I don't know about this BIOS error you got -- I get it frequently, but somehow get it to clear up by checking fairly standard GRUB stuff.  I'm wondering if this has something to do with the SATA-to-PATA connection, although I don't really see why it should be a problem.  Maybe it is BIOS as was suggested above.  I'll think on it.  Maybe someone else will chine in with some hardware insights.

---

### Post by Raymond Day on 2007-08-16
I booted the CD to a command line and typed:

sudo grub

But it comes back with:

> Probing devices to guess BIOS drivers. This my take a long time.
Error opening terminal: bterm.
#

I can boot the cd in rescue mode. Re install GRUB but it don't change any thing.

It says "You are ready to use this adapter since it is transparent to the BIOS and operating system."

Just don't know what to do to fix this.

-Raymond Day

---

### Post by MQMike on 2007-08-16
Well, that's what I was about to suggest -- somehow try re-installing GRUB to that MBR (just in case the installer got foxed or something and didn't get the job done).  I've seen that work.
Not here though, apparently.

I don't know what Error opening terminal: bterm means, but that's moot if you found another way with the Rescue mode.

---

### Post by MQMike on 2007-08-16
You can google on:

GRUB error 18

and you'll probably get all sorts of wild stuff, but maybe something useful (I've done this before).

---

### Post by MQMike on 2007-08-16
BTW, GRUB cannot just bypass the BIOS.  In fact, GRUB sees the drives EXACTLY as BIOS sees them (which may differ from how Linux sees them).

---

### Post by confused57 on 2007-08-16
Here are some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

You might want to consider setting up a small /boot partition(100-200 Mb) at the beginning of the hard drive when you install Ubuntu.

---

### Post by Raymond Day on 2007-08-16
For a test. I found a old "Trustix-3.0-mini" that I put on the CD.

Installed it. It took it about a hour to format the 750GB hard drive. But it did.

I told it to reboot and GRUB goes the same way as ubuntu but it dones not error!

Trustix boots up and works. Sees the hole 720GB hard drive!

Is there some way I can use the Trustix GRUB boot and install Ubuntu server but not mess up the Trustix GRUB to use that one to boot Ubuntu?

They should fix this in Ubuntu. A old Trustix works.

-Raymond Day

---

### Post by Raymond Day on 2007-08-17
After I did a swup --upgrade in trustix and installed webmin. I could look at it's GRUB boot and because swup --upgrade installed a new Kernel it has two that can pick to boot.

When it boots were the error comes up in Ubuntu this comes up with 2 Kernels now to pick.

I am thinking to edit the 1st Kernel so it will boot Ubuntu. I can backup the Boot with True Image backup. Then install Ubuntu then restore the Trustix boot with True Image backup.

But I don't know how to edit GRUB?

In webmin the 1st Kernel shows this:

Option title   "Trustix Secure Linux (2.6.13.4-1rt)"
Boot image partition 	Default Selected  "IDE device A partition 1 (Linux)" Other
    Don't mount and verify partition
Operating system to boot 	
Kernel 	Path to kernel "/vmlinuz-2.6.13.4-1tr"
Kernel options "ro root=/dev/hda2 ramdisk_size=8192"
Initial ramdisk file None "/initrd-2.6.13.4-1tr.img
Other OS 	From first sector of partition "checked"
From chainloader file
Make root partition active?
None (non-booting menu entry)
Password locked? 	Yes No "no checked"

In quotes is what I can change that it says right now.

I have Ubuntu server installed on another system and I went to webmin on it and made a 3rd GRUB on Trustix just like the 1st GRUB on the other Ubuntu system. I could not pick the same boot image partition because it has to be there. So I picked Default. I hope that works.

I booted True Image backup and started a backup of Trustix along with it's MBR that I edit. I will post back if it all works.

I will install Ubuntu server agian then use True Image backup to restore the MBR that Trustix made and I edit some.

After TIB backed it up. It did 3 Partitions. One GRUB 125.5 GB, Ext3 696.5 GB, and swap 1,969 GB. That how Trusix auto formated it. I am not sure how Ubuntu does. Maybe that is why it don't boot.

Can some one show me a link or here how to format the drive like this in a Ubuntu server install? Or is there some way to tell Ubuntu to install it's self with out formating the hard drive?

-Raymond Day

---

### Post by Raymond Day on 2007-08-17
I think this my be what's wrong with Ubuntu. When I go to install it and it comes to Partition disks. It auto shows this:

SCSI1 (0,0,0) (sda) - 750.2 GB ATA ST3750640AS
          #1 primary  131.6 MB   K ext3      /media/sda1
          #2 primary  747.9 GB   K ext3      /media/sda2
          #3 primary      2.1 GB   F swap     swap

It don't show a GRUB. It that what it wants to put GRUB on the 131.6 MB one? If so it don't boot.

When I went to Manuel do the partition it says No root file system.

So I have to tell it to do "Guided - use entire disk"

Then is shows:

The following partitions are going to be formatted:
  partition #1 of SCSI1 (0,0,0) (sda) as ext3
  partition #5 of SCSI1 (0,0,0) (sda) as swap

I don't know how to made like a 125.5 GB partition for grub to be on that looks like Trustix did to boot.

-Raymond Day

---

### Post by confused57 on 2007-08-17
I can't guarantee it will work, but you might want to try selecting "manual" partitioning, using the alternate(or server) install cd...there are some excellent screenshots in this guide for installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Make the /boot partition approximately 200 Mb, in the dropdown menu, select the mountpoint as /boot, format as ext3, select primary partition...then set up your root partition next, make it approx 20 Gb, select the mountpoint as /, format as ext3, select primary partition...the next partition you might want to set up a separate /home partition in the remaining space(all but 2 Gb, which you will set up as swap), select the mountpoint as /home, format ext3, select primary partition...then in the final 2 Gb of free space, select the mountpoint as swap, format as swap, select logical partition.

As I mentioned, it "may" not work for you, but I've seen it work for others on older bios computers.

Added:  It's "possible" that you wouldn't need a separate /boot partition, if you set up your / (root) partition at the very beginning of the hard drive, but make it 20 Gb...then set up your separate /home partition and swap partition as I described above.

---

### Post by Raymond Day on 2007-08-17
Well I reinstalled Ubuntu server yet again. Takes about a hour to format.

It did not boot. Same thing with GRUB Error 15.

I booted True Image backup and just restored the MBR from Trustix that booted on this same system. It said track 1 or 0 I forget. But it resorted it in a sec. I rebooted but it did not change any thing. Ubuntu still says error 15.

I guess I just can not install Ubuntu server on this.

I will restore the Trustix one and set that all up. It works.

But if some one knows a fix I love to have Ubuntu server running.

-Raymond Day

---

### Post by Raymond Day on 2007-08-18
I put a SATA 160 GB hard drive on it. The BIOS did not see it full size and GRUB got a error too booting after a new install. So I used a IDE 80 GB. That worked and it booted. I backed it up with True Image backup. Then restored it to the 750 GB hard drive. Now it boots from that drive!

I need to resize the partition or make a new one to use the rest of the hard drive. It is only using 80 GB of it. But it can see the full size at 698.64 GB.

Is there a command to resize or make the rest of the hard drive a big partition? I am sure there is. I did some commands but can't get it to work. Is they any step-by-step way that shows how?

They need to fix this on Ubuntu. When a old CD I burned a long time ago with Trustix on it worked and booted then Ubuntu don't something is very wrong.

-Raymond Day

---

### Post by Raymond Day on 2007-08-19
Made the rest of the hard drive a new Partition.

With help form a person he told me to do:

mkreiserfs /dev/sda3
reboot

He set it up a little before that.

It worked. Now I have a big 624.09 GB Partition. Still a 80 GB one too. I wish could of just had one. I have to make a lot of symbolic links now to the big Partition.

I hope they fix this on the next update of Ubuntu.

-Raymond Day

---

### Post by Raymond Day on 2007-08-25
I seen this looking on line that said something like disable the IDE Drives in the BIOS.  Ubuntu should see the full size. I all ready have it set up and working but with a small 80GB partition and the rest one partition. I make symbolic links to the bigger parition from the smaller one. Because I want 2 other server to be on just this one system and for them to be set up the same only one one Ubuntu server. I spent a lot of time so I don't want to test this out but it my help some one else. Just tell the BIOS you don't have a hard drive then maybe it will boot right. I don't know.

-Raymond Day

---

