---
title: "NOT SOLVED YET.  Partition misalignment"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by oldfred on 2013-01-17
How much RAM do you have? swap is for too many applications all at once wanting to use RAM or for hibernating. If you do not hibernate, edit videos or start every app you have at once and have 4GB of RAM or more you may not even need swap, but some is recommended.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Did you end up with UEFI or BIOS install?
Some alignment issues reported are not relevant. All partition need to start on a sector that is divisible by 8. Extended partition does not matter, but logical do, if in MBR mode. All gpt partition tools should automatically give aligned partitions.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Post this:

sudo parted /dev/sda unit s print

---

### Post by Conscript on 2013-01-17
Okay.   Bought this new machine - HP Pavilion G6.  It came installed with the  dreaded Windows 8 Virus.  I say virus because it took 2.5 hours at the  help desk to kill it.  For whatever reason the new BIOS they made makes  it impossible to boot any distro prior to 12.04.  Something about  encryption and whatnot.  Can anybody illuminate me on this?

Somehow we managed to get Ubuntu 11.10 on it because that is the version  I liked the most, but have since switched to 12.04 64 bit on this  machine with a gnome fallback interface.  It had to be done in DOS from  the windows 7(8?) system, we had to manually tell it to recognize the  setup file in Ubuntu 11.10 in order to install.  Apparently it takes  windows 7 to kill windows 8.  And then from windows 7 you can kill it  with Ubuntu with extreme effort given the new BIOS's they are making  now.

Anyways....

I have noticed the machine to be slower than expected - Windows ran  faster so something had to be wrong.  It just gets a little slow and  hangs for a while not sure why.
Then by sheer accident I was fiddling with a flash drive and found this when I clicked on my hard disk summary in Disk Utility:

"WARNING: The partition is misaligned by 3072 bytes.  This may result in very poor performance.  Repartitioning is suggested."

How exactly do I fix this without reinstalling/butchering the system?

Also, do I really need a 4 gig swap file?  Or is that just a tasty treat  for the FBI forensics division?  What is a swap anyways?

Sorry for the duplicate thread, I hit solve on accident instead of Ubuntu.


                                                                  [[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12460329")

---

### Post by Conscript on 2013-01-17
I suspect that if I don't have to reinstall(hopefully- lots of data already) I'll have to fiddle with the partitions, is Gparted the way to go?  Or is the default Disk Utility?  Don't have much knowledge on fiddling with partitions.

Either way I am lost thus far.

---

### Post by oldfred on 2013-01-17
I had already posted in you other thread. Moved it here but now it is first.

---

### Post by sidzen on 2013-01-17
> **Conscript said:**
>  . . . "WARNING: The partition is misaligned by 3072 bytes.  This may result in very poor performance.  Repartitioning is suggested."

How exactly do I fix this without reinstalling/butchering the system?

Also, do I really need a 4 gig swap file? . . .

I suspect that if I don't have to reinstall(hopefully- lots of data already) I'll have to fiddle with the partitions, is Gparted the way to go?  Or is the default Disk Utility?  Don't have much knowledge on fiddling with partitions.

Either way I am lost thus far.

Suggest starting over first using [*SystemRescueCD*]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") to cleanup your hard drive either with DukeNuke'em or the dd command, then getting to know [*cfdisk*]("http://www.tldp.org/HOWTO/IBM7248-HOWTO/cfdisk.html") or fdisk.  These latter partitioners make the error referred to nearly impossible.

But begin by getting rid of all traces of nasty old ntfs.

Nowadays a swap partition does not need to be over 2GB, if this large, with all the RAM available to the motherboards put out. 

Best wishes!

---

