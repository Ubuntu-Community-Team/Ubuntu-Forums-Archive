---
title: "feisty upgrade failed - /home problem?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by HeyItsMatt on 2007-05-06
Hey everybody.

I just attempted to upgrade from Edgy Eft to Feisty Fawn.  The upgrade process seemed to go normally, and all the files were downloaded (other than a few vague looking possible errors in the process list as it was upgrading things, and a few config files that I elected to keep rather than replace).  However, when I restarted, it gets me to the GRUB menu, lets me choose Ubuntu, shows the Kubuntu loading screen, and then dumps me into a command prompt as root, along with a screenful of messages before the input prompt (which I can use to navigate the filesystem).

It tells me I can press cntrl+D in order to resume boot, which then gives some messages, in particular a message "warning: no newline at the end of /etc/fstab".  It then takes me to the Ubuntu login screen - if I try to log in, it tells me that my home directory is listed as "/home/matt" but does not appear to exist.  It gives me the choice to login as root, but that fails.

I recently moved my /home folder to a separate partition of the computer - I am assuming that, since I am missing the newline in fstab, it is failing to mount my /home directory on startup and that dumps me into a command prompt.  My question:  should I go ahead and use nano to add a newline to the end of stab, and if so, how do I add that newline?  Just press enter, or is there some special character representing newline I have to insert?

Perhaps the error is already obvious, I'm just nervous about doing anything without confirmation now that I'm being dumped into a command prompt and unable to login.  I'm also a bit confused, because I restarted the computer several times after moving /home to a new partition and modifying fstab, but before attempting to do this update.  Why would fstab work fine during those restarts, but suddenly not work after the upgrade?

I can try to provide more information if needed.  The messages that occur along with the command prompt mention an error log, so I could look at that if I needed to (although I don't know how I would transfer anything from that log to this separate computer, other than looking at it and typing it out here by hand).

---

### Post by randomhuman on 2007-05-06
Hi

I don't think the missing newline is the problem, but you can add it if you want: just press enter. The screenful of messages should give you some idea, what do they generally seem to be about? Is your fstab ok other than the missing newline? If it is you might be able to just mount /home from the command line, press ctrl-d and login as normal for now, then at least you might be able to copy &  paste the error messages into a post.

This has just happened to me as well, see, but on a fresh install to a new hard-drive. After the install I took out the old hard-drives, but they still had entries in fstab that couldn't be found for the fsck during boot. Maybe it's the same thing?

Good luck

---

### Post by HeyItsMatt on 2007-05-06
Hey, I added the newline to fstab (I'm assuming that pressing 'enter' after the end of the last added line adds a newline) but it did not help.

you mentioned fsck - amongst the messages I get along with the command prompt is "fsck died with exit status 8" and then "file system check failed" below that.  When I press cntrl+D to try to continue with boot and log in, it talks about mounting filesystems and says that special device /dev/hda1 and /dev/hda5 do not exist. (/dev/hda1 = Windows XP, which I had mounted in Linux with a line in my fstab, and /dev/hda5 = separate Linux /home partition, also with a line in fstab)

I am dual booting Windows XP and Ubuntu - I can boot into Windows just fine, and using partition magic I can see all of my partitions, which look fine.  Partition Magic doesn't complain of any errors either. 

It says a log was saved to /var/log/fsck/checkfs... when I look at that log it says this:

Log of fsck -C -R -A -a
Sun May 6 21:54:53 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/hda5
/dev/hda5:
The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

fsck died with exit status 8

Sun May 6 21:54:53 2007
------------

 I am a Linux newbie (and not a computer expert) so unfortunately I don't understand what "superblock" or "fsck" are in the above logs.  However, both my Linux partitions are ext3, not ext2 as the log is mentioning.

Also, I just used the "fdisk -l" command, and although my partitions look right, they are listed as "/dev/sda1", "/dev/sda2" etc.  I don't think they were sda previously... could this have changed for some reason, so that I have to update my fstab file?  Both the lines in fstab are to mount /dev/hda1 and /dev/hda5.

---

### Post by HeyItsMatt on 2007-05-07
I seem to have fixed my problem - all I did was changed the entries in fstab from "hda1" and "hda5" to "sda1" and "sda5" respectively.  Feisty Fawn now seems to be booting up and functioning normally as far as I can tell.  I don't mean to bump my own thread so soon but I thought it might be a good idea to post my solution in case anyone else stumbled upon this thread with the same problem.

Also, here is another useful looking thread that has a lot of information about changes in hard drive idenficiation from Edgy to Feisty Fawn, how to modify fstab, how to look for UUIDS, etc:

[http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab](http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab)

---

### Post by randomhuman on 2007-05-07
> **HeyItsMatt said:**
> I am a Linux newbie (and not a computer expert) so unfortunately I don't understand what "superblock" or "fsck" are in the above logs.  However, both my Linux partitions are ext3, not ext2 as the log is mentioning.

Also, I just used the "fdisk -l" command, and although my partitions look right, they are listed as "/dev/sda1", "/dev/sda2" etc.  I don't think they were sda previously... could this have changed for some reason, so that I have to update my fstab file?  Both the lines in fstab are to mount /dev/hda1 and /dev/hda5.

Indeed it did change for some reason. In Fiesty, all drives are regarded as scsi devices, or sd* rather than hd* for ide, although I don't know why. You shouldn't have had to update fstab yourself though, it should have been done during the upgrade.

fsck is File System ChecK, I believe. It's a utility for checking the integrity of your filesytems.

---

