---
title: "Extended partition not on physical sector boundaries"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by trovatore on 2012-07-21
Sorry for the dupe post -- got no traction in Hardware & Laptops, so I thought maybe that was the wrong place.

I have a new laptop, windows pre-installed (of course they used the  whole partition table, so I had to figure out which ones I could delete,  grr).  Anyway I repartitioned it before finding out about the 4096  blocksize issue.  Fortunately I haven't gone crazy yet -- I have sda1  and sda2 for Windows (sda2 is the main Windows partition), sda3 for  Linux root, sda4 extended, sda5 is /home, and sda6 is swap.

Sda1 and sda2 have sizes that are multiples of 4096, but sda3 does not,  so the extended partition does not start on a physical block.

Is there any way to non-destructively move the start point of the  extended partition?  I'm guessing not, but just in case.  If I have to  delete the extended, that's not too bad, because I don't have much on  /home yet, which is the only non-swap partition in there.

Assuming I do have to delete the extended partition, (1) how do I make  it start on a multiple of 4096, and (2) how do I recreate my user home directory, with a  home directory in /home and all the defaults?  (Using ecryptfs, if that  makes a difference.)

---

### Post by oldfred on 2012-07-22
It is my understanding that the extended partition itself does not have to be on the 8 sector boundary. You do not directly write into the extended partition but in the logicals inside the extended. And all the logicals then should be on the correct boundary.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by trovatore on 2012-07-22
Thanks much!  But I would still need to move the start point of /dev/sda5 (mounted on /home), which I'm guessing probably means deleting it and recreating it.  As I understand it, the content of /home is contained in a file called .Private (using ecryptfs).  If I just move .Private into / , then delete /dev/sda5 and recreate it on the correct boundaries, remake my /home/$USER directory, and move .Private back, will everything work smoothly?  I know that ecryptfs gives you some huge long passphrase, but I don't exactly understand how that can really be needed, given that I just log in with my ordinary password and it is able to mount the encrypted directory.

---

### Post by oldfred on 2012-07-22
I do not know about encrypted partitions, other than users occasionally post that they want to recover data from a failed drive or other drive issue. And of course the purpose of encryption is to prevent any access.

Possibly related info:
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

