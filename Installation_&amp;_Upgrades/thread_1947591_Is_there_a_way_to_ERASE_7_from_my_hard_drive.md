---
title: "Is there a way to ERASE 7 from my hard drive"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by S2UIRR3L on 2012-03-26
I've had it up to here with Microsoft and all the problems I've been having with XP and 7. Crash after crash, issue after issue, fix after fix... I'M DONE!!!

I know enough about Linux and Ubuntu and what programs to use as an alternative to the ones that required ms. I'm FINALLY Linux only, no more ms!!!

Now... Is there a way to erase any existence of it on my hard drive? I have an 80-Gig sata split down the middle. Win-7 is so screwed up, it's pretty much useless and I want that 40-Gigs back.

I can always format the whole drive and start with a fresh install... but then I'll have to download and tweak everything all over again when I re-install Ubuntu. Not looking forward to it.

MY OBJECTIVE: reclaim the 40-Gigs used by 7 without formatting the whole disk. Thanks in advance for any and all help and suggestions.

-Leo

---

### Post by jerrrys on 2012-03-27
You can delete the partition

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-delete-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-delete-partition)

---

### Post by Bucky Ball on 2012-03-27
Simple.

Boot from the LiveCD, open Gparted, erase the Windows partition (which will be NTFS), resize Ubuntu partition into the free space left by deleting Win and set the boot flag on the Ubuntu / partition, hit 'Apply', done.

To resize the / partition you **must** be booting from the CD, NOT the hard drive, as the partition needs to be unmounted and it can't be if you are running the OS from it. ;)

---

### Post by darkod on 2012-03-27
It is simple, and also it is not. I didn't understand do you currently have a dual boot of XP and 7, or just 7?

If you have both XP and 7 it depends in which order they were installed because windows always combines boot files on the first system partition. So, if you installed 7 and then XP, the XP boot files went to the 7 partition. Deleting it will make XP unbootable.

Even in that case you can repair the boot with XP cd, just be advised.

If you only have 7, yes, simply delete the system partition and install ubuntu into that unpartitioned space.

---

### Post by Bucky Ball on 2012-03-27
> **darkod said:**
> Even in that case you can repair the boot with XP cd, just be advised.

If you only have 7, yes, simply delete the system partition and install ubuntu into that unpartitioned space.

From the OP's first post:

> I'm FINALLY Linux only, no more ms!!!

Whether they have xp and win 7 or one or the other doesn't matter. They want to get rid of Win altogether and use only Ubuntu ...

---

### Post by S2UIRR3L on 2012-03-27
I just installed this hard drive... I installed 7-ultimate first, then went in and installed Lucid Lynx. When installing Lucid, I split the hard drive right down the middle... I don't have XP.

I understand what everyone is telling me... Boot from the Lucid DVD and use THAT to delete the other partitions... New question: Does the Lucid kernel version matter or not?

Since I've been using Lucid, update manager has updated me several times to new kernels as they became available. (I have my update manager set to fully automatic download).

TO EVERYONE REPLYING - THANK YOU SO MUCH FOR ALL THE HELP - YOU'RE ALL ROCK STARS!!!

-Leo

---

### Post by Bucky Ball on 2012-03-27
> **S2UIRR3L said:**
> New question: Does the Lucid kernel version matter or not?

-Leo

Nope, you're just being updated to the latest stable (supposedly and generally) kernel. If you have troubles you can always drop back to the last working kernel or attempt to fix the problem in the new one (although if there is an issue it's generally fixed pretty quick in the next update or three). And you're right about the message being do it from a LiveCD.

And no problems, happy to add some suggestions. Hope it all works out. ;)

PS: Be an idea to backup anything you don't want to lose before deleting/expanding, just to be on the safe side.

---

### Post by S2UIRR3L on 2012-03-27
Sounds like a plan, Bucky... I don't have too much on the actual hard drive. Most of my photos, videos, music, etc. is on an external 500-Gig because the laptop's hard drive is so tiny at only 40-Gig.

But I guess it will be closer to 80 again once I delete the other partition? I mean, if Windows isn't there anymore, I should be able to use it as if it were extra space, right? If not, no worries.

Like I said above, if I have to format the whole drive and start out with it "all zeros" it's not a problem. It's just that I have my Lucid tweaked to where everything is where I need it quick... Not looking forward to spending hours re-downloading all the programs, visuals and tweaking compiz agian lol.

-Leo

---

### Post by darkod on 2012-03-28
You will be able to use that space, but there are basically two options.

After you delete the partition, you end up with unallocated space (unpartitioned). But ubuntu will not use this space automatically, you have to tell it what you want.

From there you can:
Option 1. Use Gparted and create a ext4 partition from that space. Then you can make an entry in /etc/fstab and mount that partition as /data for example. After that it will be available at /data in your system.

Option 2. To extend the root partition to include the unallocated space. But if your root and swap are logical partitions as part of the extended partition, you will actually need to extend the extended partition first to include the unallocated space, and once the extended partition is bigger you will need to extend root to take the available space.

Option 2 is risky in a way that any resize of partitions has the potential to go wrong. Have a full backup before you start it.

Option 1 is very easy and risk free, if you don't mind that the 40GB space will be avalable at /data (or another mount point you select but it will not be by default inside the root partition).

---

### Post by Bucky Ball on 2012-03-28
And option #3 is to just use it as /home ...

Get to partitioning section of the install, choose 'Something Else'

/ = root and Ubuntu OS; 20Gb fine;
/home = your data; big as you like;
/swap = swap and 2Gb should be fine.

Enjoy ...

---

### Post by S2UIRR3L on 2012-03-28
Thanks a million guys. I think I've gathered all the information that I need. I'm gonna go with the easy option one. Like I said, I really don't "need" the extra room, but it's nice to know I have it if I need it.

I'll let everyone know how it goes and mark this thread as solved when I'm done.

You guy are the best - THANKS!!!

-Leo

---

### Post by newhorizon on 2012-03-28
Thank you all for the information. I like the person whom started the thread am having a similar problem. I being curious set up a dual boot on my laptop of ubuntu 11.04 later to 11.10 with win 7 preinstalled when i purchased it. my back up disks were lost in a fire. now no matter safe mode system repair win 7 will start to boot then flash a blue screen for half second then goes back to boot menu. Linux hasnt given me any problems other than a steep learning curve. i have a 500 gb hard drive that linux is only using a 32 gb partition of. I really want that dead space back again thank you for helping someone else with a similar problem

---

### Post by S2UIRR3L on 2012-03-28
_[SIZE=2]**WARNING TO NEWHORIZON**[/SIZE]_

I just tried this:

> **darkod said:**
> 
Option 2. To extend the root partition to include the unallocated space.  But if your root and swap are logical partitions as part of the  extended partition, you will actually need to extend the extended  partition first to include the unallocated space, and once the extended  partition is bigger you will need to extend root to take the available  space.


But obviously, I did something wrong because I lost grub and my computer won't boot anymore. I'm not advanced enough to know how to fix it (if it CAN be fixed). Lucky for me tho, I didn't have very much to lose (because I had everything backed up on my 500-Gig external hard drive).

If you don't know what you're doing (like my self lol), you should read up on it... A LOT!!!

Thanks a million everyone... I'm more than sure that it was my error because I'm not very advanced at this. I must have deleted the wrong ext4 or dev or SOMETHING lol. But seriously, everyone here on these forums are fantastic. Thanks a million for trying your best to help me with many options. I'm marking this as SOLVED because in one way or another... Windows 7 is being formatted as we speak (via DBAN).

-Leo

---

### Post by darkod on 2012-03-29
What probably happened is that grub2 files have moved on the disk during the resize. Grub2 installs only small part on the MBR of the disk, and this part knows where to look for the files to continue the boot. But it looks for them on the exact physical location where they are. If they move, they are still on the disk but not where it expects them.

In this case you can simply reinstall grub2 to the MBR and it connects to the files correctly again.

---

### Post by S2UIRR3L on 2012-03-29
I just formatted and started from zeros... Like I said, didn't have much to lose... I was just being lazy about it and didn't feel like re-downloading every program and tweaking everything again.

---

### Post by darkod on 2012-03-29
> **S2UIRR3L said:**
> I just formatted and started from zeros... Like I said, didn't have much to lose... I was just being lazy about it and didn't feel like re-downloading every program and tweaking everything again.

That's fine. I just mentioned it for the future or for someone else finding this thread, when there is something to lose. You don't need a full reinstall, you just reinstall grub2 to the MBR, if the problem was what I suspect it was.

---

### Post by S2UIRR3L on 2012-03-29
darkrod - great advice buddy - thanks

---

