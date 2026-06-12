---
title: "I screwed up my disk!"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by mateoc15 on 2007-10-04
I installed Windows XP to set up a dual-boot configuration and then starting installing Feisty.  Everything was going fine EXCEPT ONE MAJOR PROBLEM.  In the partitioning section I accidentally chose to install on  an existing NTFS drive (which is badddd because that's where I have/had about 5000 MP3's).  When I realized my mistake I canceled the format less that 5 seconds into it.  I used the "undo changes to partitions" button (I think that's what it was called) and the checkbox for "format" was never checked on that NTFS drive.  I chose the correct unpartitioned space, created EXT3 and SWAP partitions, and installed.  Everything works beautifully... I love Ubuntu... Ubuntu recognizes the NTFS disk I screwed up but cannot read any files.  It says "lost+found" in the file browser window for the drive.  Windows also recognizes the drive but when I accessing using the Run command "d:" it tells me that the drive is not formatted and offers to format it.  Obviously I clicked no.  chkdsk d: from a command window tells me that it is of type RAW and cannot be used with chkdsk.

So... the problem is that I know that the files are still there.  In the 5 seconds where there was a problem it could not have POSSIBLY overwritten/dumped all of those files.  The question is, how do I get it back to a readable format?

I knew something like this was going to happen to me.  Always does.

Thank you in advance!

---

### Post by yabbadabbadont on 2007-10-04
You might see if one of these will get them back for you:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

---

### Post by mateoc15 on 2007-10-04
I did make a slight mistake in describing the problem.  When I use the file browser to try to view the directory I get a message that I don't have permission, *not* that the files can't actually be loaded.  So I tried this... I'm a bit of a Linux newb (I bet you couldn't tell) so tell me how I can try to view the list of files please.

matt@mattlnx:/media/hdd1$ ls
lost+found
matt@mattlnx:/media/hdd1$ cd lost+found
bash: cd: lost+found: Permission denied
matt@mattlnx:/media/hdd1$ sudo cd lost+found
sudo: cd: command not found
matt@mattlnx:/media/hdd1$ 

Can I not do "sudo cd <directory>"?  Ubuntu doesn't actually have an accessible root account, right?  If so, how can I get that?  Should the password be the same as my matt user (the only defined user)?

I'll review the links you posted.

Thank you!

---

### Post by mateoc15 on 2007-10-04
Ok, so I'm a little afraid to try anything.  I did the analyze function on TestDisk (nice util at first look) and it only recognizes the Linux partition.

"Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[Mac    ]  Apple partition map
[None   ]  Non partioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection"

I chose Intel (since it's a PC, actually has an AMD64 processor though) since it seems most logical.  Certainly not Mac, Sun, XBox.

"Disk /dev/hdd - 120 GB / 111 GiB - CHS 232581 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 P Linux                    0   1  1 232575  15 63  234436545
No partition is bootable

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted"

Should I select *, P, L, E, D?

"Disk /dev/hdd - 120 GB / 111 GiB - CHS 232581 16 63

Warning: the current number of heads per cylinder is 16
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps."

It shows it as a Linux partition but as I said I know there's some NTFS and files under there.  This gets worse as I go along.  I have realized that a good chunk of my school work from back in the day as well as all of my digital camera pics are on there!  I don't want to pay to get this data back!

Thanks everyone.  I think I'm at least headed in the right direction.  But I don't want to totally hose the disk and be screwed.

---

### Post by trippinnik on 2007-10-04
do you have ntfs-3g installed?

---

### Post by mateoc15 on 2007-10-07
Yes, I've been using NTFS-3G for a while now.  It works great (as far as I can tell).  I have another (in tact) NTFS drive that Linux is reading with no problem.

Using testdisk I tried to change the drive Type from Linux (ext3) to NTFS but it couldn't write the changes.  Can anyone explain the message:

"Warning: the current number of heads per cylinder is 16
but the correct value may be 255."

I'm not sure where to change that or if it's safe to do so.

Thanks!

---

### Post by coleman on 2007-10-09
Also, what about those poor souls (me) who did not press cancel after five seconds?? Is any of our precious data recoverable or did the reformat to ext3 'white out' everything that was on what used to be the NTFS partition...

---

