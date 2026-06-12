---
title: "[SOLVED] How do I safely delete old Ubuntu partition?"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by brundlelinux on 2008-07-03
Hey guys.... I'm in bit of a bind here.

I've been using Ubuntu for several years now.  In that time, I've done a fair amount of experimenting with different things, and I've learned a LOT.  I'm so very glad I gave up on Windows and made the switch.  The downside is, I have a metric ton of leftover "artifacts" from all my experimenting that I want to get away from and have a much "cleaner" OS running.

Bottom line... I started on Ubuntu Edgy.  Somewhere along the line, I installed the entire KDE desktop as well, to get a feel for it.  On one partition, I went back and forth between the two desktop environments, and did entire version upgrades along the way, up until Hardy.  I can't even begin to count the number of off-repository installs I did from source, mostly without using checkinstall.  I know, I know.... like I said, I was learning... and sometimes the hard way.  ;-)

Now I've pretty much gotten into a base routine of the things I use and the things I don't need / want.  Problem is, I have a an enormous amount of stuff to pick through to clean the system.  So, I took the easy route.  I installed a fresh version of Ubuntu Hardy to a second partition, created a mount point, and brought over all the media I needed.  It is up and fully functional, and I have no need for the original "frankenbuntu".  What is the correct procedure for deleting the original partition and getting that space back on my new, working partition?  I have a physical burnt disk of Gparted that I can work from, and I'm pretty sure it's just a matter of using that to delete the partition and then add the free space created, and then, of course, editing the grub to point to the right partion and editing the flags and whatnot.  I just want to make sure I actually attack the correct partition since they both come up as the same description on analysis while maintaining the integrity of that all-important swap partition.  In short, just asking for double-checking info before I botch this, which I have a habit of doing when working on my own  ;-)

Any help / info is appreciated.

---

### Post by Pumalite on 2008-07-03
Post:
sudo fdisk -lu

---

### Post by brundlelinux on 2008-07-03
Device Boot      Start         End      Blocks      Id  System
/dev/sda1   *          63   108888569    54444253+  83  Linux
/dev/sda3       108888570   234436544    62773987+   5  Extended
/dev/sda5       231464583   234436544     1485981   82  Linux swap / Solaris
/dev/sda6       108888696   228492494    59801899+  83  Linux
/dev/sda7       228492558   231464519     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Pumalite on 2008-07-03
It's either sda1 or sda6. You must know. Ignore /swap. Delete the old partition. Leave the extended one intact. You could eliminate one /swap
Reinstall Grub if you need to:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by brundlelinux on 2008-07-03
Yeah, that's what I had come down to, but honestly, with them being about the same size, I'm not sure which it is.  Logic would dictate that the beginning block would be the older one, but then I'm not sure if the second install freed space before or after the original partition.

I think the common sense way to approach this would be to resize the two and make one disproportionately larger than the other, and then booting into one and checking the OS disk analysis, so I knew which was which, and then following your above advice.

Under normal circumstances, I would have just done a complete hard drive wipe and started from scratch.... but re-ripping 700+ cds is NOT an option.  ;-)

Thanks for all your help.  Much obliged.

---

### Post by Pumalite on 2008-07-03
First mount them in your Live CD and examine them. Then you'll know.
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1

---

### Post by brundlelinux on 2008-07-03
Oh boy.  This isn't looking good for the home team.

So, before reading your last reply, I had already popped into the Gparted livecd and accomplished the same thing.  I totally forget that Gparted would also list used space, and that made it a no-brainer.  Sda1 was only using 5 gigs, and sda6 was showing the media I transferred over, so I knew which was which.  And then I started down a BAD path.

I deleted the sda1 partition and the sda7 swap partition.  I applied the changes.  Then I switched the flag to the remaining Ubuntu partition to boot.  

Enter the first snag.  I am completely unable to add my two unallocated spaces to the remaining Ubuntu partition.  Gparted simply will not give me the option to grow it any larger than it already is / was.  My only option for either of the unallocated partitions is "new", which doesn't seem to be getting me any closer to my goal.

So, I decided to not get frustrated and come back to it later.  I'd just go ahead and fix the grub.  

As anticipated, an attempt at a normal boot gave me the standard grub error.  Error 17, I think.  So, I popped in the Ubuntu livecd and set about fixing the grub loader.  I've actually followed that exact post in the past to fix the grub after I had a period with dual booting Windows XP, so I was in familiar territory.  Alas, snag #2.  It does repair my grub, however, the grub is still giving me the same options as before I nixed the partitions, however, not a single one of them returns anything besides telling me there is nothing at that location.

So.... here I sit, posting from firefox on the liveCD.  Have I gotten myself into an unrecoverable spiral, or can this be saved?  Time to bite the bullet and just wipe and start from scratch?

---

### Post by avtolle on 2008-07-03
As to the first snag; Linux resizes partitions "from the end", not "from the beginning". Thus, to me, you should be able to add the space from deleting /dev/sda7 to /dev/sda6, but you won't be able to add the space at /dev/sda1 to it without moving /sda6 to /sda1, which, as far as I can tell, won't get you anywhere. There are ways, I suspect ,to do this, but "biting the bullet" right now might actually be the most efficient use of time and effort.

EDIT: Just took another look, and the room formerly occupied by /sda7 WOULD NOT be available to /sda6. Sorry for this error. 

Wondering if you could create a separate /home partition on (former) /sda1? That might salvage some of what you have already done without a complete wipe and start over. If this sounds like something you might want to do, I'll post a link.

---

### Post by avtolle on 2008-07-03
Just realized you might not be able to evaluate whether you might want to try the separate /home partition without information. Take a look at [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) and see if this is something that might be helpful to you.

---

### Post by brundlelinux on 2008-07-03
I've actually gotten all my partition issues resolved now.  It was a matter of having to transfer the freed space from the logical partition to the extended for use there.  100% fixed.

My only issue now is..... how do I fix the grub so that it realizes there is a bootable partition with Ubuntu on it, AND actually points to it, but without being able to boot into the partition?

I can mount the partition using a liveCD and access the root/grub folder, but I have no idea what to do once I get there.  My command of find /boot/grub/stage1 is still returning the same results of (0,4) which, technically, doesn't exist anymore.  I would preseume that this is because it's reading the grub information which is written to the partition, but can't be modified.  In my mind, it would seem that there would be a way to manually edit that information after mounting the partition and accessing through the LiveCD, and then doing a grub fix as per usual.  Am I on the right path?

Either way..... if I get this fixed -or- if I do a fresh wipe and install, I WILL be using a dedicated /home partition from now on, in lieu of an actual secondary hard drive to back up to.

---

### Post by avtolle on 2008-07-03
You are on the right path. There is a plethora of threads on the forum about editing grub, which, since I've not had to do it, I read but don't book mark for easy retrieval. I'd suggest searching the forum, or perhaps someone else will have the information at their fingertips.

BTW, good news on the partitioning issue.

---

### Post by Pumalite on 2008-07-03
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by jnw222 on 2008-07-03
at that rate, just back all the music to external media and (gasp) reformat (/gasp)

---

### Post by brundlelinux on 2008-07-04
Good news.  I had two threads going simultaneously, one addresses more of the partitioning issues and one more oriented towards the grub issues.  I'm happy to report that I was able to get both resolved and that everything is fine.  Thanks to all who provided that provided information and got me through it.

My biggest issue was that I don't have a way to back up the media, or that would have been a no-brainer.  I'm not running any sort of external drive or a second hard drive, so in the interim until I get a backup device (which has quickly become a priority), I'm just going with a /home folder on a dedicated separate partition.  It won't help me at all in the event of a hard drive failure, but it's better than nothing in the meantime.

Again, thanks to all, and I'm marking as solved.  ;-)

---

