---
title: "Dual-Booting Question"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Tahakki on 2009-11-22
Recently, our computer, running Karmic and WinXP, died.

We're now looking at getting a computer, and have decided on one from Dell - with a 750GB HDD! :o

However, being a Dell PC, this will come with Windows 7 pre-installed. As it's a fairly decent machine, we'd be keen to keep this for gaming and those not used to Ubuntu, and put Karmic on too.

I had planned this:

125GB - Ubuntu 9.10
125GB - Windows 7
500GB - FAT32 partition for files.
I plan to use GRUB 2 as the bootloader.

Is this possible, getting both the Koala and Win7 to read and write their /home and Windows-equivalent to the same partition? Any advice would be appreciated.

Thanks!

---

### Post by mechro on 2009-11-22
Your scheme looks reasonable enough but it would probably be best to put Windows in the first partition. You'll also need a Linux swap partition but the Karmic install will take you through that.

I don't understand what you mean by *"read and write their /home and Windows-equivalent to the same partition"*. They are different filesystems, different permissions etc, etc. It's not feasible.

You can have shared data on the planned FAT32 partitition but that would be for documents, photos, music, and so on. You'll also find Ubuntu can read and copy files from the Windows partition.

---

### Post by Tahakki on 2009-11-22
Thanks for your reply.

Why would I put Windows first? Those who use this computer most often will use Ubuntu most of the time.

Apologies, perhaps I didn't make myself clear enough. Say I go to /home/Music in Ubuntu, and the Music folder in Windows. Is it possible to get them to both be the same place?

Program files, config, themes etc would all live on the partition for their respective OS. As for swap, sorry, forgot to mention that - it's twice the size of RAM, isn't it?

---

### Post by Bartender on 2009-11-22
You'll have to wait until you get the computer and then figure out Dell's partitioning scheme.
Some PC's come with too damn many partitions right from the factory.  Four primary partitions, three primaries and an extended partition, etc.  

So you'll need to examine the HDD and figure out what Dell did, because you might be boxed in.  You should be able to boot from an Ubuntu LiveCD, choose to run without making changes, go into System>Administration, and open the GParted partitioner.  You can plug in a thumb drive, and use the screenshot utility in Applications to take a screenshot, save it to the thumbdrive, then unmount the thumb drive and use any PC to post the screenie here at your thread.

The next thing you'll want to figure out is how Dell's recovery system works.  Either way, you want to burn the recovery discs right away, but the questions then are:
1) How many partition(s), and which one(s), can you delete after making the recovery partition?
2) Do the recovery discs set the HDD back up exactly like new or not?

On my Acer, which came with four primary partitions, running the recovery discs wiped away all previous partitions and created one big C:/ drive.  Installing Ubuntu was impossible before running the recovery discs, but easy afterward!

But the way Acer does it is probably not exactly how Dell does their recovery stuff.  

I think what's happening here is each manufacturer is trying to keep you from screwing around with your new computer, and they're all trying to dissuade you from copying a working version of Windows that could be installed to other PC's.

Until you know the answers to the above, it's hard to say what you should do.  There's a Dell Forum right here at Ubuntu Forums, Dell has a Linux forum at their forums, and there's always Google.

It's not necessary to set up a data partition in the old FAT32 file system anymore.  Ubuntu can read and write to NTFS just fine.

---

### Post by mechro on 2009-11-22
Well perhaps it's a myth, but I've always understood Windows goes first because Microsoft wants it to go first. Maybe it's different for Windows 7. You'll have to see how Dell installs it , no doubt with their hidden recovery partition.

You could have /data_partition/Music from Ubuntu and put a symlink(shortcut) in /home. From Windows I guess it'll be your D... E... F drive or similar.

---

### Post by Bartender on 2009-11-22
> **Tahakki said:**
> Thanks for your reply.

Why would I put Windows first? Those who use this computer most often will use Ubuntu most of the time.

Apologies, perhaps I didn't make myself clear enough. Say I go to /home/Music in Ubuntu, and the Music folder in Windows. Is it possible to get them to both be the same place?

Program files, config, themes etc would all live on the partition for their respective OS. As for swap, sorry, forgot to mention that - it's twice the size of RAM, isn't it?

When we talk about putting Windows "first", it's a two-part reference.  One, you want the Windows data "first" on the hard drive physically.  Two, you want Windows installed "first" chronologically.  In other words, install Windows today, then install Ubuntu tomorrow.  If you install Windows "first" chronologically to a blank HDD, you will kill two birds with one stone because Windows will also be "first" as far as the physical placement of the data on the HDD.

This has almost nothing to do with which OS would boot up.  That is decided by the GRUB bootloader, which is installed when you install Ubuntu.  If you're installing Ubuntu to a separate HDD then there are other ways to make it boot first, but we won't go into that.  As a matter of fact, GRUB by default will go to Ubuntu although you installed Ubuntu "second".  That can be easily changed if you decide you want to start up in Windows, I'm just trying to explain how it actually works.

Ubuntu's /home folder will be written in a Linux file system.  It doesn't matter if you create a separate /home partition or not, /home will be ext3 or ext4, both Linux file systems.

Anything Windows will be NTFS.  So as I understand your question, no this isn't possible.

However, the data partition, if formatted as NTFS, will be accessible from Ubuntu.  It might take an extra click or two but everyone should be able to deal with that.

---

### Post by darkod on 2009-11-22
+1 Bartender

I give my voice to him. You definitely want windows (any version) installed on the first primary partition and first (before Ubuntu). It avoids many possibilities for problems later.

And those damned recovery partitions create only problems. Search just this forum and you'll see what I'm talking about. From my (short) experience trying to help people here I am starting to think that very rarely will dual boot work correctly with recovery/utility partition on the drive. Because that partition seems to be on the end of the drive but still marked /dev/sda2 by ubuntu. Also, it might be that the "smart" engineers are somehow using that partition in the boot process too, which confuses the hell out of grub.

Few people reported success after deleting that partition but for someone who didn't receive windows OS disc with the computer that might be problematic.

Personally, even without dual booting I find those recovery partitions useless because it destroys your partition plan also, usually it creates 1 or 2 partitions, deletes everything, and makes the computer as from factory. What good is it to have D: partition for data if it gets destroyed during recovery just because windows was missing a file or two.
For dual booting it is even more useless because it destroys ubuntu straight away. I'm not too much into conspiracy theories but I'm starting to think microsoft is trying to make harder for dual booting this way, recovery partition will destroy your second OS. The price of a dvd disc is symbolic these days and I can't see a reason not to give one to the customer who has paid for a license.
Sorry for the long post, just MHO.

---

### Post by Tahakki on 2009-11-22
I think I'll set up some symlinks, if that's possible - I know how to do so in Ubuntu, is it as easy in Win7?

I had WinXP installed second on my old computer - however, as 7 comes with the new computer I'll probably leave it at that.

---

### Post by mechro on 2009-11-22
If it's possible I'd try and negotiate with Dell to supply you with the official Windows disc as they might only offer you their recovery disc.

---

### Post by oldfred on 2009-11-22
Do not consider FAT32 for a shared partition. I did that 3 years ago since then the NTFS tools were just getting to the point of working well. I did my backups to that partition and they were always 4GB. It turns out that is the max size of files in FAT32 and I never had a good backup.

Even though you can directly read the NTFS partition that windows is installed in, I still like a separate shared or data partition. If the windows operating system has problems you still have the data partition. Although the NTFS tools in Ubuntu work well windows is not always happy with other systems writing into it. You still need to use windows to defrag, chkdsk and do regular maintenance to your NTFS data partition.

Three years ago we were in windows a lot so I set up firefox and thunderbird profiles in the shared partition. That has worked well for me, even now that we are mostly in ubuntu.

Windows does not have to be the first partition but it has to be a primary partition. You can install windows to a logical but only can boot it thru another existing windows install in a primary, it will never work on its own. Ubuntu can be all in logical partitions without any issue.

You probably will not get a full install disk from Dell. If not the recovery disk you write will only totally reimage the drive to factory original erasing everything. I suggest you also download just to have:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Bartender on 2009-11-22
Hey, there, oldfred -
I'm on dial-up so there are many things I can't check out.
How can neosmart have Vista recovery discs available for download on their website?
I understand that it's the COA that makes each installation unique, not the CD or DVD, but if neosmart is offering a complete OS for download that still seems like something Microsoft would have a cow about!

To the OP -
I offer this with a caution.  I know this worked with Vista but I'm not sure how (or if) 7 is different.  And this will seem like jumping out of a perfectly good plane...
But I'll make the suggestion anyway.  Our new Acer 5920 came with Vista.  As I mentioned earlier, there were four primary partitions.  First thing I did was make recovery discs.  Second thing I did was screw up Vista by trying to shrink it with GParted.
So I ran the recovery discs and ended up with one big primary partition, which was easy to shrink using the tool in Vista and left me with lots of freedom to partition as I chose.
Another guy who had the same laptop and was going thru the same problems went at it in a different way - he had his recovery discs, but what he did was wipe all data using a GParted LiveCD, then he created one primary NTFS partition across roughly half of the drive at the "front" (left-hand side of the partition map in GParted).  When he popped in his recovery disc, it only recognized the NTFS partition and installed Vista to that partition.  He had the rest of the HDD open to install Ubuntu.
No I thought that was really slick because he didn't have to screw around with trying to defrag and shrink the Windows OS.

I have no way of knowing whether this would work on a Dell or not.  I'm sure you could find out by googling, checking out forums, etc.  

But regardless of what you try, burn those recovery discs first thing.  If nothing else, you'll be able to get the new PC going again if you screw things up.

One additional comment - recovery discs often won't work unless the drive (or part of the drive) is formatted as NTFS.  So if you somehow installed Ubuntu to the entire drive, then tried to run the recovery disc, it probly won't work.  Reformatting the drive as NTFS is relatively easy.  You could download the latest stable version of GParted (link below my sig) and create a bootable CD from the .iso same as you would an Ubuntu install CD.  There are other methods but that's my favorite tool for partitioning.

EDIT:  OK, I visited neosmart's site.  I think I understand what's going on.  It's a tool that MS has released that basically puts you into the Recovery Console.  Something like that.  I need to go to the library and download this!  I see there's a 7 version too...

---

### Post by darkod on 2009-11-22
I checked the links, it's only system repair disc, that's why they can "offer" them for download. But that's good enough if you only need to repair MBR as often is the case. For reinstall, you need a proper windows disc.
Thanks a lot for the links oldfred, very useful.

---

