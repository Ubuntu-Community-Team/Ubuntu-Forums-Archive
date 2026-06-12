---
title: "Getting Vista to boot again after a failed Ubuntu install"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2007-06-16
Hello all,

Following a failed Ubuntu install described [elsewhere]("http://ubuntuforums.org/showthread.php?t=475539"), it looks like Vista may also be unbootable.

The machine is a new Lenovo ThinkPad R61.  During the install I was able to repartition the 120GB hard drive, apparently successfully, leaving 45GB for the preinstalled Windows Vista Business and assigning the remainder to ext3 partitions.

The install failed while installing the base system and now Vista will not boot.  Booting from the hard disk dumps me straight into the ThinkPad recovery system instead.

I'm wondering if anyone can advise on getting Vista to boot effectively again.  I don't know whether it's been screwed up for good or whether the system is no longer aware that this is a partition it can boot from.  Could I do this by e.g. using the alternate CD in rescue mode and installing GRUB?

Since this laptop appears to be seriously allergic to Linux right now, it's urgent that I get a working OS back onto it.  If I can recover Vista without a full system restore, it would be a big help.

Thanks in advance for any advice.

---

### Post by Pumalite on 2007-06-16
> **WebDrake said:**
> Hello all,

Following a failed Ubuntu install described [elsewhere]("http://ubuntuforums.org/showthread.php?t=475539"), it looks like Vista may also be unbootable.

The machine is a new Lenovo ThinkPad R61.  During the install I was able to repartition the 120GB hard drive, apparently successfully, leaving 45GB for the preinstalled Windows Vista Business and assigning the remainder to ext3 partitions.

The install failed while installing the base system and now Vista will not boot.  Booting from the hard disk dumps me straight into the ThinkPad recovery system instead.

I'm wondering if anyone can advise on getting Vista to boot effectively again.  I don't know whether it's been screwed up for good or whether the system is no longer aware that this is a partition it can boot from.  Could I do this by e.g. using the alternate CD in rescue mode and installing GRUB?

Since this laptop appears to be seriously allergic to Linux right now, it's urgent that I get a working OS back onto it.  If I can recover Vista without a full system restore, it would be a big help.

Thanks in advance for any advice.

Did you create your new partition from Vista?

---

### Post by WebDrake on 2007-06-16
> **Pumalite said:**
> Did you create your new partition from Vista?

No, I repartitioned using the alternate install CD.

---

### Post by Pumalite on 2007-06-16
> **WebDrake said:**
> No, I repartitioned using the alternate install CD.

If Ubuntu is sharing drive with Vista, I'll tell you this: Vista is known for not liking to share with any other OS. But, if you want to keep Vista, you have to partitioned FROM Vista.

---

### Post by WebDrake on 2007-06-16
> **Pumalite said:**
> If Ubuntu is sharing drive with Vista, I'll tell you this: Vista is known for not liking to share with any other OS. But, if you want to keep Vista, you have to partitioned FROM Vista.

OK, so I guess I can assume that Vista is pooched.  No way of recovery?

---

### Post by merlinus on 2007-06-16
You should be able to restore the vista mbr from the recovery console.

-merlin

---

### Post by WebDrake on 2007-06-16
> **merlinus said:**
> You should be able to restore the vista mbr from the recovery console.

-merlin

Could you give a more detailed explanation? :)

---

### Post by merlinus on 2007-06-16
What are the options when you boot into the recovery console?

-merlin

---

### Post by WebDrake on 2007-06-17
> **merlinus said:**
> What are the options when you boot into the recovery console?

-merlin

Mmmm, I'd misunderstood those options.  In the event I went overkill and used the "Restore System" option to restore Vista to its "factory fresh" form, which took a while (no data loss, as it was a new machine) but left me with a working system again.  I could probably have got away with less but did not see an option to repair just the boot record.

It looks like the partitions did work effectively as Vista is now in the smaller partition as intended.  The swap partition also exists, as does the ext3 primary partition I created for the root filesystem.  The logical partition created for /home is listed as simply "empty space", but from context I think Windows does recognise it as a partition (it offers the option to "delete partition").

So long as I don't alter the partition table, is it safe to format and attempt to install things to these partitions without affecting Vista again?

Thanks for all advice.

---

### Post by merlinus on 2007-06-17
Are you talking about re-installing ubuntu, or simply formatting /home to EXT3?

If the latter, that you can do whilst running ubuntu and using gparted from System/Administration.  You can install it via Applications/Add Remove if you have not already done so.

Another option is gparted live cd from:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by WebDrake on 2007-06-17
> **merlinus said:**
> Are you talking about re-installing ubuntu, or simply formatting /home to EXT3?

A reinstall, since there is no working Ubuntu on my system.

What I'm concerned about is this---that if I attempt to install Ubuntu or any other distro again and it fails in the manner it did before (installing the base system, long before installing GRUB or similar), will this affect the boot record and require another rescue for Vista?  Or am I "safe" now that I won't be repartitioning the disk, just formatting and writing to existing partitions?

---

### Post by merlinus on 2007-06-17
I would never bet on anything from Redmond, but....

as long as you are not doing anything with your vista partition, it should be okay.

And remember that grub will replace your windows bootloader, and should it fail, you will have to restore the mbr for vista.  That should be an option from the recovery console.

Good luck!

-merlin

---

### Post by WebDrake on 2007-06-17
> **merlinus said:**
> I would never bet on anything from Redmond, but....

as long as you are not doing anything with your vista partition, it should be okay.

And remember that grub will replace your windows bootloader, and should it fail, you will have to restore the mbr for vista.  That should be an option from the recovery console.

Good luck!

-merlin

Thank you ever so much for all your advice.  Here's hoping! :D

---

### Post by oboedad55 on 2007-06-19
If you run into this problem again, check into recovery options for Vista. For example, with XP you can boot from the CD, hit "R" and get to a command prompt. From there, you just type in "fixmbr" and it will restore the Window$ boot sector. You will get some dire warnings as usual, but I have never had this fail to make Wimpdows bootable again. After you get going again you can give Linux another try.

---

### Post by cwgpress on 2007-06-21
In my similar setup, I used Vista's disk management to reduce the size of the Vista main partition, creating free space on the disk. Then I used the Ubuntu alternate install, so I wouldn't have to do everything from a gui; less complexity => more reliability. I hope.

I let Ubuntu create a 12 Gb partition and a 1 Gb swap partition, leaving myself more free space for future experiments. I'm in a  mode where Vista has to be my primary operating system for now, but I'm trying to learn more and more about Linux and Ubuntu seems by far the most convenient way to do that.

At first, the Ubuntu installation looked fine until I tried to log on; then I discovered that the keys were not recognized. I figured I'd messed up on identifying the keyboard during the install. Upon rebooting, I chose the Vista option and it still worked fine. The next time I was able to play with it, the keyboard still didn't work, and I wasn't sure what to do. Recovery mode acted the same as the original. I got myself into the grub command line but after fooling around a bit I decided I didn't know what to do. So I rebooted. I got distracted and it went into Ubuntu. I typed in my username and it worked! Ubuntu is fine ever since.

Hopefully I'll remember to change the default option in Grub to the Windows installation, and keep the timeout reasonable, perhaps 5 seconds. Then I don't have to remember to stay at the screen unless I am going into Ubuntu, and that's for play rather than work.

Cheers!

Chuck

---

