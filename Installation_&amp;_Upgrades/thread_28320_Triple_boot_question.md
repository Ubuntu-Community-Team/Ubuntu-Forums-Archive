---
title: "Triple boot question"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by veritas366 on 2005-04-19
Well, I posted before but now I have a slightly different question.  I decided to try to install Ubuntu.  I had some free space on my Master hard drive along with XP and FC3 is on the slave. 

The install went along fine but it got to Grub time.  It was able to detect only Windows, so I feared installing the new grub over the old would simply keep me from being able to boot FC3.  I didn't know what else to do, however.  How do I manually fix things so that all 3 can boot at my choice?  

Here is the drive that it's on:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       20321    10241406    7  HPFS/NTFS
/dev/hda2           20321       41633    10741563+   f  W95 Ext'd (LBA)
/dev/hda3   *       41634       77545    18099648   83  Linux
/dev/hda5           20321       40641    10241406    b  W95 FAT32
/dev/hda6           40642       41633      499936+  82  Linux swap

The reason I put it here rather than on the much larger second drive is simply because that is using the LVM2 system which has taken control of the whole disk.  No one so far has felt comfortable telling me how to shrink it down safely, even though there is very little data on it.  

So, I could install the new grub and add the info for FC3 (with fear and trembling) or in some other way manually edit grub and create a boot image manually for Ubuntu (it offered to put the boot image somewhere else, but I didn't know where to put it.  Evidently the automatic partion doesn't automatically make a boot partition??  The two Linux partitions above were a result of the automatic partitioning.

Any ideas?

---

### Post by veritas366 on 2005-04-19
Well, now I'm confused.  I chose not to install grub or any boot info at all and yet it has messed with my Windows MBR and now Windows won't boot.  My Grub is working as FC3 boots up fine but Windows will not.  Can someone tell me what in the process of installing has been changed in my MBR?  I thought I was safe, when it told me it couldn't find my FC3 to simply go back and skip the whole grub step.  If I do a repair of my MBR will that undo Grub?   ](*,)

---

### Post by bored2k on 2005-04-19
If you do the fixmbr trick with a Windows fix you wont be able to boot to anything but Windows.
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by veritas366 on 2005-04-19
Yeah.  I guess I'm hoping someone can tell me what the heck Ubuntu does on installation that messes with the master boot record even when I specifically declined to install grub on the master boot record?  What does it do?  Is there a way to fix it without fixmbr?

---

### Post by veritas366 on 2005-04-19
Okay, it was an easy fix.  Others have posted about going into your bios and changing the hard drive setting from auto to LBA.  I have no idea what that does or why it got changed...but hallelujah!  I'm back in business.  

Now, I have everything for Ubuntu on my system except (I assume) the boot image and the entry in Grub.  As I mentioned, when I try to install Ubuntu, it found Windows but not FC3 (which is more important!)  So, I could not allow it to install grub.  What is the safest way to get Ubuntu going with an entry in grub for all three os's?  Can I manually create the info I need for booting Ubuntu?  

From my partition info it looks like I'd have to manually mount a /boot partition and then put what I need there.  Or should I just go thru the Ubuntu install again and tell it to put the boot info in hda3 (info above for my drive) and then configure grub manually to add Ubuntu?  I want to just try things out....but I get nervous    :roll:

---

### Post by veritas366 on 2005-04-19
In case anyone actually reads this far.  I went ahead and just installed Ubuntu.  I figured I could just grab the grub info from fc3 after doing so.  Well, Ubuntu is up and running (sort of) but I can't access the other hard drive "hdb"  

It's not listed as one of the mounted devices when I run the "mount" command.

When I try to mount it (specifically hdb2, where fc3 lives) into a directory I created called /mnt/fc3 it says that "/dev/hdb2 is already mounted or /mnt/fc3 is busy.  If I try to unmount it...it says...you guessed it...device not mounted. 

I tried the same thing by adding it to the fstab with this:

> /dev/hdb2	/mnt/fc3	ext3	defaults	0	2 

Then I hit "mount -a" and it once again told me that /dev/hdb2 was already busy.  

I know I'm missing something here.  If I look in the devices, I see all the hdb drives there, but I can't open them from there.  

Please help...it's the last thing I need to do to get all this set up!

---

