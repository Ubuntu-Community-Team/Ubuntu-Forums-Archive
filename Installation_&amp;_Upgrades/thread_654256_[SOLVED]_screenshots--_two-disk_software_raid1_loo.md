---
title: "[SOLVED] screenshots-- two-disk software raid1 looks like two single-disk software ra"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by ogomoe on 2007-12-30
I'm trying to install Gutsy 7.10 using the alternate install cd.  When I get to the "partition disks" screen, it shows my two-disk raid1 array as two single-disk raid1 arrays, md0 & md1.

I will boot from an 80GB disk with the swap, root, and /home partitions.  I'm using two 300GB disks for the raid1 array as /data.

I created the array when I was using Opensuse 10.1.  I successfully upgraded that to Fedora 7 with no problems.

The most relative information I could find on the forums was in these threads:

[http://ubuntuforums.org/showthread.php?t=55211&highlight=mdo+md1+raid](http://ubuntuforums.org/showthread.php?t=55211&highlight=mdo+md1+raid)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282)

...which led me to here:
[http://www.excalibur-partners.com/archives/18](http://www.excalibur-partners.com/archives/18)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Is there some busybox magic to be done before I get to the "partition disks" screen that will non-destructively reassemble that original raid1?

I'm not sure how to proceed.  My gut feeling is to install Gutsy with the two Raid1 arrays, backup, and restore.

I've tried Fedora 8 and the Ubuntu 7.10 Live cd's, but those wanted to create a fresh raid1.

Here are some screenshots...

---

### Post by foolsh on 2007-12-31
you'll have to download the alternate install cd to use RAID sorry

---

### Post by bsmith1051 on 2008-01-01
What about this post (by me!...)
[http://ubuntuforums.org/showthread.php?t=481499](http://ubuntuforums.org/showthread.php?t=481499)

I would assume you need to install from the Alternate Install CD (yes, I know you're already trying that) and then you might need to delete one of the mirrors and let Ubuntu recreate it.

---

### Post by ogomoe on 2008-01-02
I'm glad to say everything is back to normal.  I'm sorry I didn't see the responses to my original post, but thank you for taking the time to respond!

I was terrified that I would destroy my files by accident, so I continued to dig around.

What really got the ball rolling was this thread...
[http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136)

I never committed writing to disk what was in my alternate cd installaion screenshot.   I aborted the install and started over.

At the point where you're supposed to give a network name to the computer, I hit alt-f2 for a busybox terminal.

There I typed (not knowing if everything I typed was required)...

> modprobe  raid1
modprobe dm_modI threw in an "fdisk -l" to make sure I had the correct drives one last time.

> mdadm --manage /dev/md0 --stop
mdadm --manage /dev/md1 --stop
mdadm -E /dev/sdb1
mdadm -E /dev/sdc1The "stop" for md1 wasn't necessary and the "-E" commands were for peace of mind.

Now, this is where I started sweating.  I heard zeroing the superblock was a ticket to disaster,  but I had nowhere else to go.

I did read about wiping/ re-partitioning one of my two disks, but some sources warned about incorrectly re-syncing the disks.  They said the disk with data could be wiped out with the "data" from the empty disk!

I went and zeroed the superblocks.

> mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/md0The command to zero md0's superblock said there was no md0, so I didn't bother trying to zero md1's.

The last thing to do was re-create the array.  Again, I was really freaking out about losing my files during the re-sync.

> mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1Here, I had to enter a "Y" to continue.

I could hear the disks going to work and typed "cat /proc/mdstat" a few times at the beginning to get an idea of how long this would take.  (The cat command shows a progress bar.)  After two hours or so, I typed "cat /proc/mdstat".  I forget the output, but there was no progress bar and it looked like all was done.

I hit alt-f1 to get back to the alternate cd's disk partitioning screen.  I'll include a screenshot at the end of this post to show what it is I wanted back.

The installation completes with no errors.  I removed the install cd and rebooted.

At this moment of truth, I'm still grinding my teeth, hoping I didn't trash the 300GB of real data.

To my horror, the reboot doesn't finish.  I'm dropped to an "initramfs" prompt!  See screenshot.  (I'm confident this is where I began the entire situation 3 days ago, panicking and ignorantly following commands and prompts that destroyed my superblocks.  Please read on.)

I searched the forums again and found thread #611251, linked below.  In the grub boot menu, I had to replace the UUID of the root disk with "/dev/sdb2".  I forgot to remove "quiet splash", so I couldn't tell what was happening during the reboot.   It took forever (probably actually one minute) for the gdm prompt to come up.

I logged on and found my /data partition (the /dev/md0 raid1 partition).  I looked at some files and I'm feeling everything's cool.  I calm down, edit /boot/grub/menu.lst  (followed with an update-grub command) to reflect the root partition and not the UUID, install the :twisted:140+  software updates and reboot.  Whew!

During the reboot, I'm dropped back to the "initramfs" prompt because somehow my root device got changed from "/dev/sdb2" back to the UUID in grub's menu.lst file.

I'm thinking that any time there is a kernel update this will happen again!

But I don't care!  I HAVE ALL MY FILES BACK!  All I have to do is figure out how to set an UUID manually or just continue re-editing menu.lst whenever there's a kernel update.

Here's a list of more links that were helpful in this epic solution...

[http://ubuntuforums.org/showthread.php?t=643527](http://ubuntuforums.org/showthread.php?t=643527)
[http://ubuntuforums.org/showthread.php?t=611251](http://ubuntuforums.org/showthread.php?t=611251)
[http://www.mail-archive.com/linux-raid@vger.kernel.org/msg03668.html](http://www.mail-archive.com/linux-raid@vger.kernel.org/msg03668.html)
[http://ubuntufourms.org/showthread.php?t=410136](http://ubuntufourms.org/showthread.php?t=410136)
[http://directory.fsf.org/project/mdadm/](http://directory.fsf.org/project/mdadm/)

Finally, there was a thread somewhere out there that pointed me to the "/usr/share/doc/mdadm" folder.  There's extremely useful info hidden in there.  (duh!)  Why is this such a secret?  Anyway, I'm satisfied that the main issue is over and the UUID problem must be as easy to solve, too.

Thank you everyone past and present!:cool:

---

