---
title: "Struggling with instalationl of Ubuntu"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by 0writer on 2008-04-07
Afternoon,

I'm a newbie with Ubuntu and am having a problem at the moment, where I'm starting to panic a little.

I'm a techie but just can't seem to figure this out.

I can't boot Ubuntu and I can't boot my Windows partition.

I started off after a new install, rebooted and got Error 16. After doing much reading I followed the details in [this ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")article.

I now get GRUB Geom Error when I try to boot. 

I have tried using my Windows CD and did a FIXMBR, rebooted and then I got the typical No OS found. 

I've hit a bit of a dead wall and not sure what to try next.

Any advice would be really appriciated!

Thanks

---

### Post by Herman on 2008-04-07
Quoted from the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")> 16 : Inconsistent filesystem structureThis error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.                                        Try running a file system check in your Ubuntu partition.

[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") 
Boot your Ubuntu Live CD, open a terminal in it and run 'sudo fdisk -lu' first, to check your partition numbers,
```
sudo fdisk -lu
```
Then run your file system check on the file system in your Ubuntu partition,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Were" 'hda2' is the partition number for Ubuntu, check with 'sudo fdisk -lu command and alter accordingly.

You may need to re-install GRUB again as you have done once already.

Regards, Herman :)


---

### Post by 0writer on 2008-04-08
Hi Herman,

Thanks for the reply.

I did as you said and also re-installed GRUB afterwards but now I'm back to getting Error 16 when trying to boot.

Is there anything specifically I should be looking for once the scan of the filesystem completes? I didn't receive and warnings or error messages.

I've also tried the instructions on [this ]("http://ubuntuforums.org/showthread.php?t=224351")page but still no luck. I'm now back to always receiving Error 16 when trying to boot.

I don't know if it is just something I'm doing wrong but my menu.lst seems to be completely blank.

Many Thanks

---

### Post by Herman on 2008-04-08
Hello 0writer,
If the file system check completes and doesn't give any error messages or warnings then your file system is in good shape.

:-k Hmmm...
We need to try some tests to see if we can pinpoint the problem.
If there's no problem with your file system then possibly there's either a problem with your GRUB itself or with the hard disk (partition table), or the way it's plugged in and jumpered. 

Is it a PATA (IDE) or SATA hard drive?

Can you post the output from 'sudo fdisk -lu' here please?

Can you download a copy of [Super Grub Disk]("http://sgd.benjamin-butschko.de/")   and burn it to CD or make a floppy or USB (depending on what kind of Super Grub Disk will work in your computer), and see if that will boot Ubuntu and Windows?

If it does then we'll re-install your GRUB files in /boot in case those are somehow corrupt. I'll tell you the list of commands later if they're needed.

Also, as you were feeling a little panicky, If Super Grub Disk doesn't boot Windows either, please down load an NTLDR CD from the following website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")[U].
[/U]That CD contains NTLDR, NTdetect.com. and a special boot.ini file that will boot Windows in any primary partition in a first or second hard disk. It bypasses the MBR and the boot sector, so that will boot your Windows for you or I don't know what will.Probably you'll be calmer and happier if you can boot Windows somehow for now until we get this problem fixed properly.

If even that doesn't work then I'd say the problem is almost definitely in your BIOS or the way your hard disks are plugged in or jumpered, if they're (or it) is PATA. (IDE).

Regards, Herman

---

### Post by 0writer on 2008-04-08
Hi Herman,

It's an IDE drive, specifically an IBM T41 laptop. It's the only drive and no external drives are plugged in.

The result of the fdisk is:

Device          Boot        System
/dev/sda1                   HPFS/NTFS
/dev/sda2    *              Linux
/dev/sda3                    Extended
/dev/sda5                    Linux Swap

After the first line of the fdisk I get "Partition 1 does not end on cylinder boundary".

If tried using SGD from a USB but when I try to boot it I get the error "Grub: Error 18: Selected Cylinder exceeds maximum supported by BIOS".

I'll try NTLDR in the meantime but would really love to get Ubuntu running as I'm planning on migrating from XP to Ubuntu hopefully.

Update* No luck with NTLDR but it's ok, I'm not too concerned about getting into Windows at the moment. I have spent the last 4-5 hours reading trying to understand and fix things but without any luck, I'm suprised at how hard it is. I've confirmed the filesystem is clean as well as reinstalling grub, checking that the menu.lst is intact, I really feel helpless as a techie. 

Thanks for all your help.

---

### Post by Herman on 2008-04-08
> After the first line of the fdisk I get "Partition 1 does not end on cylinder boundary". AHA! There's your problem!
Your partition table needs fixing. :)

Next time can you please copy the whole fdisk output and paste it here so I can see the exact details please? 

Anyway, your first partition should begin at sector number 63, because there are 63 sectors in a track, and the first track of the hard disk is reserved by convention for boot loader code, and should be otherwise empty.

The last sector of your NTFS partition should finish well before the next partition starts, to be sure you can resize your Windows partition a little smaller to lave a little gap between the two partitions for the time being.

For most people all this happens to fall into place automatically, I don't know why yours is different. Perhaps, being a techy, you have experimented at some time in the past with some program or code that has changed things a little and you may have long forgotten the changes. 
Anyway, whatever the cause is, we need to adjust your hard disk and partition table a little somehow.

What partitioning program did you use for creating these partitions? It might be easiest to keep using the same partition editor. 

If GParted in the Ubuntu Live CD will open it, (look in 'System'-->'Administration'-->'Partition Editor', make sure you tick the square for 'partitions must start and end on cylinder boundaries', if you see that anywhere. (it's the default, but some versions of GParted have that setting, in other version you might not see it).

Probably though, GParted won't look at your partition table, and you'll have to use another partition editor like fdisk, cfdisk or sfdisk to fix it first.

If you need specific help with that let me know which hard disk partitioning program will open it and I'll have to practice with that program a little here first to refresh my memory before I'll be able to give you good advice. 
Sometime Gnu Parted will open a partition table but cfdisk will refuse, other times Gnu Parted will refuse but cfdisk will be able to open it and fix the problem. 

Regards, Herman :)

---

### Post by 0writer on 2008-04-08
Hi Herman,

Thanks for the reply.

I realised that my problem was the Ubuntu partition manager. Even after wiping the laptop completely, installing a fresh image of Windows and then using Ubuntu to install and partition, it then made the fresh install unbootable.

Since then, I imaged the laptop again, created all the partitions in Windows and then installed Ubuntu to the dedicated partition already created rather than let Ubuntu do it.

This works fine and I am now writing this reply from within Ubuntu, great!

A long headache but I found out the best way to do it.

I can't believe than no one else has experienced this? I am using a fresh download of Ubuntu v7.10.

Thanks again for your persistence!

---

### Post by Herman on 2008-04-09
> I can't believe than no one else has experienced this? I am using a fresh download of Ubuntu v7.10. I haven't heard of anything like this happening. It is rare but I have seen fdisk outputs where one or two partitions overlap and maybe one operating system won't boot, and that could be simply fixed with cfdisk or the like, (simply by resizing a partition smaller). Your problem seems to have been extreme. I wish I could have seen a copy of the fdisk output.

It seems as if the partition editor is reading your disk geometry wrong or something like that. If this is true then you may have discovered a bug in the partitioning program and it would be good if you could  [file a bug report]("https://bugs.launchpad.net/ubuntu/+filebug"). and let developers know as many details about the problem as you can so they can try to track down the problem and fix it. 
That will help other users in the future.
It is especially good that your problem can be replicated, (it happened the next time you tried again too). If it's something that happens every time then it should be easy to find out what it is exactly that's going wrong there.

Here's a link about how to file a good bug report, ["Howto: File a bug report on Launchpad"]("http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/") by K.Mandla.

You don't have to, but it would be nice of you if you do. :)

Regards, Herman :)

---

### Post by Herman on 2008-04-09
> This works fine and I am now writing this reply from within Ubuntu, great! - oh, and I'm glad you got the problem fixed, and have a working Ubuntu now. :)
Congratulations! :guitar:

Regards, Herman :)

---

