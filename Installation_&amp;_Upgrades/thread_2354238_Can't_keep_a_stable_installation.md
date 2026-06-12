---
title: "Can't keep a stable installation"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by rare.tofu on 2017-02-28
I am brand new to Ubuntu and so far love it..

Only problem is that I can't get my server to go more than a few days without losing everything. The system has locked up in exactly the same way, twice now:

1. Everything I am doing slows to a halt, except my mouse. Nothing responds to anything, but I can move my mouse around!
2. Stays like this indefinitely, until I hit the reset button on my tower.
3. System boots into "Emergency Mode" or something like that. Asks me to hit D or Enter to continue. I hit enter, and I am my root@computername. I can navigate my whole computer.
4. I turn the comp off and boot into ubuntu live usb. Run Boot-Repair. Here is the summary it gave me after telling me it was successful: [http://paste.ubuntu.com/24088028/](http://paste.ubuntu.com/24088028/)

5. Lose all traces of an installation. Currently reinstalling OS for the third time.


Some quick specs of my system, although I am sure you can get all of this from that paste link:

4 HDD's
Each drive has first GB unallocated (for BIOS, I guess, but doesn't seem to have used this space on any of the drives)
Next 4 GB ubuntu raid5 from all drives. Results in about a 12 GB sized array that I marked for linux-swap
Next 10 GB ubuntu raid5 from all drives. Results in about a 3 GB sized array that I chose for root install of ubuntu
Remainder of drives raid5'ed for storage.

The OS array, decided on its own to peel off 12 GB for another swap. I fix this by deleting that partition and reactivating the one I made for it. With this in mind, I think I will just forgo making the swap raid in my next install. I start off by installing Ubuntu Server, but then install the ubuntu-desktop files. I am not advanced enough to run it headless quite yet.


I should have a operational OS by the time I get a reply on this thread, so look forward to seeing what the community comes up with to diagnose this! Keep in mind that I know next to nothing about ubuntu, but I am quick study!


EDIT:

Got to the installation part where it goes into partitions and this message came up. I hit yes and continued with seemingly no problems. But isn't it odd that this one drive of the 4 in that array is mounted? And to what OS?

[http://imgur.com/cCjtfww](http://imgur.com/cCjtfww)

---

### Post by TheFu on 2017-03-01
Welcome to the forums.

Servers don't have mice.

Instability is usually some kind of hardware failure.  Check the log files form a live-boot flash BEFORE doing anything else.  The logs with HW issues are overwritten at boot.

Always check the log files.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

If you are new, best NOT to use RAID at all.  There are many decisions that are Unix-specific which running other OSes don't prepare you to understand. Become a power user first, then learn LVM.  Get daily, versioned, automatic, backups working ASAP.  You shouldn't need to reinstall the OS all the time.  If there is a HW failure, like a HDD, get a new disk, restore from the backups.  Backups solve 1,000 issues and RAID solves 3. Backups are much more important than RAID.

Lastly, for someone like you, wanting to learn Linux as an admin, here is my best advice: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  Spend a few hours with the first 6 items on the list there. It will save you hours, days, weeks, months of frustration.

And that warning from the install was probably the flash/optical drive being used to perform the install.  It said which partition on which drive was mounted.  Which disk is that?  You can swap to a different console and check.

---

