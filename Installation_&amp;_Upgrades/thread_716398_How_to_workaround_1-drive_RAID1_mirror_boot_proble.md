---
title: "How to workaround 1-drive RAID1 mirror boot problem?"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-03-05
There's a known bug in the Ubuntu installer (Ubiquity?)
.  [http://launchpad.net/ubuntu/+bug/58894](http://launchpad.net/ubuntu/+bug/58894)
and another bug in the version of GRUB used in Ubuntu 7.10 and earlier,
.  [http://bugs.launchpad.net/ubuntu/+bug/120375](http://bugs.launchpad.net/ubuntu/+bug/120375)
and I would really appreciate some help implementing the workaround described in the 2nd bug's discussion

**1st bug - Ubiquity doesn't make both drives bootable**

The 1st bug is that when you setup a mirrored drive-pair, only the 1st drive is made bootable.  So good luck if that's the drive that were to fail on you!  Fortunately, the workaround is simple -- update the MBR on the 2nd drive so that it, too, loads GRUB.  I believe the following is a valid example of how to do this, where the two drives are 'sda' and 'sdb'
```
> sudo grub-install /dev/sda
> sudo grub
grub> device (hd1) /dev/sdb
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Note - if drive #1 has already failed unexpectedly (before updating drive #2 with GRUB) then you'll have to boot from the LiveCD to perform these commands.  You might be able to skip the first 'grub-install' command, too.  And the device names might be 'wrong', i.e., drive #2 might be called 'sda' if the real 'sda' is dead.

**2nd bug - GRUB won't boot with only 1 mirrored drive**

The 2nd problem is more difficult.  Apparently, **GRUB will refuse to mount _either_ drive** if it hasn't already been 'notified' that it needs to load the array in "degraded" mode, i.e., missing a drive.  The discussion in the Launchpad bug is long and extremely technical and, frankly, I couldn't follow it.

Can someone please post a simplified instruction for adding another boot option to GRUB which you can safely choose if/when you lose a mirrored drive?  Also, it sounds like the required fix is different for 7.04 vs 7.10. I'm running 7.04 now but obviously I'd like to upgrade soon, too...

---

### Post by bsmith1051 on 2008-03-05
P.S.  The discussers are hopeful this bug will be fixed in Ubuntu 8.04 ...

---

### Post by bsmith1051 on 2008-03-06
Also, can someone explain what the difference is between marking sdb as (hd1) as opposed to (hd0) in GRUB?  I've found multiple references to this issue and some tell you to use (hd0) on the 2nd drive, and I'm wondering if that was just a typo.

---

### Post by bsmith1051 on 2008-03-14
> **bsmith1051 said:**
> the difference between marking sdb as (hd1) as opposed to (hd0) in GRUB?
Apparently, the 'root (hdX,Y)' command defines what drive/partition should be referenced in the MBR.  So, for making a mirrored drive bootable, you want to be sure to reference it's own local root (/) partition.  For the first drive this is easy.  For the second drive, though, it will depend on whether you plan to swap cables on the drive if/when the first drive fails.  If your computer won't boot from the secondary controller/cable you would have to swap the drive.

---

### Post by VulcanTourist on 2008-03-14
*chuckles*  You're having a full **dialog** with yourself.  I'd make it a real conversation, but I've got nothing to add.

---

### Post by M0nk3Ee on 2008-03-15
Just a quick post to register that "I am having the same problem" I really hope this is fixed in the next release.  

I have spent the last week fiddling around moving my system from a single hard disk over to  a raid1 system.  After following several online articles and not getting very far i thought i had finally finished tonight with all the work complete, only then to find that when a disk did fail it wouldn't boot, i couldn't belive it.  My system doesn't feel much safer.  

I am so happy that i found this bug report and the problem is not something that i have done wrong.  That doens't happen very often!:)

how long until the next release anyway?

---

### Post by bsmith1051 on 2008-03-16
> **M0nk3Ee said:**
> how long until the next release anyway?
The 'final' Hardy 8.04 is due April 24, I believe.  But the next alpha (or beta) release should be next week... I think!  I'm eagerly awaiting the latter so that I can test this again.

---

### Post by bsmith1051 on 2008-03-25
This simple test-case still fails in the new Hardy beta.

---

### Post by bsmith1051 on 2008-03-30
One of the people in the Launchpad bug discussion clarified the 'best' solution!  I've just modified my system and I'm about to try rebooting...

[List]
[*]Update the 'initramfs' boot script,
```
 > gksudo gedit /usr/share/initramfs-tools/scripts/local

```
[*]Find the comment,
```
 # We've given up, but we'll let the user fix matters if they can".

```
[*]Just *before* this comment, add the following:
```
 # The following code was added to allow degraded RAID arrays to start
 if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
  # Try mdadm and allow degraded arrays to start in case a drive has failed
  log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
   /sbin/mdadm --assemble --scan
  log_end_msg
 fi

```
[*]Finally, update the boot image to use the updated script,
```
 > sudo update-initramfs -u

```
[/LIST]

---

### Post by M0nk3Ee on 2008-03-30
Just had an email to notify me you had added something to the thread.

Any Joy??

---

### Post by bsmith1051 on 2008-03-31
Well my reboot went ok!  But I haven't had time to do a real test, i.e., unexpectedly kill one of the drives.  Actually, all I've been doing to test was to shutdown and unplug one of the drives, then power-on again.  No chance of damaging a drive that way.

I've got a test system at work that I'll try this on later today...

---

### Post by bsmith1051 on 2008-03-31
so far, so good!  My 8.04-Beta test box booted successfully on just the 2nd drive.  I shutdown again and reconnected the 1st drive, and now I see that I have to manually add it back to the array, e.g.
```
> sudo mdadm --add /dev/md0 /dev/sda1
```
I'm now tracking the resync progress via
```
> cat /proc/mdstat
```

---

### Post by bsmith1051 on 2008-04-09
Updated the original post with a note about fixing GRUB after the fact, if needed.

Also, I just tried a simple performance test and it seems to indicate that a pair of mirrored drives is **25% faster** than a single drive!

All I did was set my computer to skip the login prompt, then also set about a dozen apps to auto-load.  With both drives, it took 1:30 for the system to finish booting.  I then disconnect one of the drives and let the array fall-back to 'degraded' mode.  I then re-ran the test and it took 2:00 to finish booting.

Whattya think is this a valid test, or is the array slower in degraded mode for reasons other than lost drive-sharing?

---

### Post by M0nk3Ee on 2008-04-22
I only just got your replys, great news that it all seems to be fixed now.  I will have to upgrade in two days time.  INteresting results as far as the boot up times.  I don´t really understand why it would be quicker.

Thanks for your time on this.

---

### Post by Boblin on 2008-04-22
> **bsmith1051 said:**
> One of the people in the Launchpad bug discussion clarified the 'best' solution!  I've just modified my system and I'm about to try rebooting...

- update the 'initramfs' boot script,
 > gksudo gedit /usr/share/initramfs-tools/scripts/local

- find the comment,
 # We've given up, but we'll let the user fix matters if they can".

- Just *before* this comment, add the following:
 # The following code was added to allow degraded RAID arrays to start
 if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
  # Try mdadm and allow degraded arrays to start in case a drive has failed
  log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
   /sbin/mdadm --assemble --scan
  log_end_msg
 fi

- finally, update the boot image to use the updated script,
 > sudo update-initramfs -u

Yesterday, I installed new Hardy Heron. However this patch doesn't works for me :(

---

### Post by bsmith1051 on 2008-04-22
> **Boblin said:**
> Yesterday, I installed new Hardy Heron. However this patch doesn't works for me :(
Really?  it did for me, back on one of the earlier betas.  How are you testing it?  If you're getting an error just in the process of following the instructions, then you're doing something wrong.  The test then is to unplug one of the drives and try to boot on the other.  If you try to boot the 2nd drive, you also have to manually install GRUB

---

### Post by Boblin on 2008-04-23
I found the difference between yours and my setup: I use lvm

/dev/md0 - /boot
/dev/md1 - lvm - vg-root,vg-var

I attached screenshot from booting with only one hard disk.

Thanks.

---

### Post by Boblin on 2008-04-23
Here is solution for Hardy:

You have computer with raid1(+lvm): if you turn off your computer and unplug one of two disks, after next boot you have to wait (3 minutes). After this you get some error messages about raid. Than  press <CTR>+<D> and you will boot normaly. After next reboot you will also boot normaly.

You have computer with raid1(+lvm): you have running system. Set up one of two disk as faulty. Halt system. Unplug faulty disk. Start system. You will boot with one disk normaly.

---

### Post by bsmith1051 on 2008-04-23
> **Boblin said:**
> I found the difference between yours and my setup: I use lvm
Sorry, I don't know anything about LVM...  From looking at your screenshot it looks like the array is starting 'correctly' in degraded mode so I don't know why it then falls-back to the Busybox prompt.

You should create a new bug report on Launchpad.

---

### Post by Boblin on 2008-04-24
As I wrote in previous post, I one drive is missing, you have to press <CTR>+<D> and next boot is OK.

---

### Post by rgotten on 2008-04-26
I had the same problem and today decided to install the ubuntu server 8.04. corrected the first bug so each drive can boot, and when i reboot the system with one har drive out...there was a question if i would like to start the raid in degrade (or somethng similar), with the command mdadm -R /dev/mdx    It worked well, i am new intu linux and ubuntu, so i tryed to rebuild the array and the message i got was that the disk was busy all the time. I am doing more testing and also will try to do a reinstall of the whole thing and even not do the fix for 1st bug and see what happen...Will kepp poesting

rgotten

---

### Post by WendyWeber on 2008-05-18
I have Ubuntu 8.04 and the patch works ok for me. I can unplug either drive and the system will boot from the remaining drive with no prompts and no actions required from the user. It takes a while for the system to realize one drive is missing, but then it boots normally and sends me an email that there's a problem with one drive.

Thanks bsmith, this was helpful.

---

### Post by bsmith1051 on 2008-05-18
cool, glad I helped!  Now, maybe you can give me a quick how-to on setting-up the email notification??  :)

---

### Post by ShetlandBreeder on 2008-06-03
> **WendyWeber said:**
> I have Ubuntu 8.04 and the patch works ok for me. I can unplug either drive and the system will boot from the remaining drive with no prompts and no actions required from the user. It takes a while for the system to realize one drive is missing, but then it boots normally and sends me an email that there's a problem with one drive.

Thanks bsmith, this was helpful.

I've just upgraded my Dell PE840 from 7.1 to 8.04. I had the patch to initramfs-tools from bug #120375 (same as the one suggested by bsmith) installed on 7.1 and it worked fine. But on 8.04 with one drive unplugged it drops through to BusyBox, so I suppose that the test is not working for some reason. But the good news is that if I assemble the arrays with 'mdadm --assemble --scan' then I can hit Ctrl+D and the machine will continue to boot, unlike 7.10 where I couldn't get out of busyBox without rebooting, which lost the arrays....

Does anyone understand what the second part of the test line is doing?

Seems there's still some quirks to be ironed out.  

Pete Hardman

---

### Post by Bogaurd on 2008-07-03
I've just installed 8.04 LTS - this fix was just what I was looking for, works perfectly! Thanks! :)

---

### Post by bsmith1051 on 2008-07-03
> **Bogaurd said:**
> I've just installed 8.04 LTS - this fix was just what I was looking for, works perfectly!
Did you actually test it?  I thought the Launchpad bug had discussion about it not working on 8.04?

---

### Post by Bogaurd on 2008-07-03
> **bsmith1051 said:**
> Did you actually test it?  I thought the Launchpad bug had discussion about it not working on 8.04?

I sure did, booted off a single drive with no probs (unplugged one of the drives) :)

---

