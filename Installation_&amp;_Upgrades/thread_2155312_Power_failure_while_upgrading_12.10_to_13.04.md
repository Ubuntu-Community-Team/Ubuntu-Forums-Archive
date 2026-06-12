---
title: "Power failure while upgrading 12.10 to 13.04"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by jbuczek on 2013-06-17
Boy, I hope there is some quick fix for this!

OK... I'm stupid.  I didn't backup root before I started an upgrade because I was about to change it all anyway AND I've been upgrading since 9.04 and never had a problem and there is no easy way to keep 500 GB backed up all the time.  

SO... I had dual boot Ubuntu 12.10 AMD64 + XP upgrading to 13.04 AMD64. Here in the Philippines my "broadband" ain't all that broad so after a couple hours the download was still in progress showing 10 min to go. I fell asleep and woke up five hours later when power went off. Happens a lot here.  When it came back on I could boot to grub which shows 

Ubuntu
Advanced Options for Ubuntu
Memtest
Memtest,Console"
Windows XP
Ubuntu 13.04 -this -that -whatever {that ran off the screen}
Ubuntu 13.04 Recovery -this -that -whatever etc.

With the last two entries being new.  Selecting any Ubuntu lead to a black screen hang.

I had an extra partition so I downloaded the 13.04 live CD and did a clean install of 13.04 AMD64 into that partition which updated grub which changed the bottom two entries to:

Ubuntu 13.04 
Advanced Options for Ubuntu 13.04

The new (clean) Ubuntu (top entry) works fine but of course has none of my settings.  The "Ubuntu 13.04" goes to

General Error Mounting File systems
A maintenance shell will now be started.
Ctrl-D will terminate shell and reboot system.
Give root password for maintenance (or type Ctrl-D to continue).

It accepts my old password and I can access root (CLI only).

Since it's complaining about file systems I rebooted the new (clean) system and mounted the old root. All appears superficially normal.  "Superfically" means I don't know enough to examine much.  Just in case, I modified "old root" /etc/fstab to comment out all filesystems except swap and root.  Both seem OK since the swap partition is being used in the "new" system and I can mount and access "old root".  Rebooted and tried the "Ubuntu 13.04" grub entry again with no change then restored the original fstab settings.

Booting to the clean install again I tried a little testing. NOTE: "Old root" is sda6.

parted is normal:

johnb@UbuMax:~$ sudo parted /dev/sda 'print'
Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.0GB  21.0GB  primary   ntfs            boot
 2      21.0GB  47.2GB  26.2GB  extended
 5      21.0GB  25.0GB  4000MB  logical   linux-swap(v1)
 6      25.0GB  47.2GB  22.2GB  logical   ext4
 4      47.2GB  68.2GB  21.0GB  primary   ext4
 3      68.2GB  320GB   252GB   primary   ext3


Fsck says everything is OK.

sudo fsck /dev/sda6
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda6: clean, 249355/1357216 files, 2662315/5422848 blocks

Same results for "fsck.ext3" and "fsck.ext3 -f"

So I rebooted and tried the "Ubuntu 13.04 Advanced Options" and "recovery mode".

I activated networking and ran "dpkg Repair Broken Packages".  It downloaded the package lists but failed with an error message something like "dpkg unable to lock. You must run dpkg --configure -a manually to fix this" repeated several times.  I opened the maintenance shell and tried doing that but it returned an error and repeating again gave the same error.

I'd really like to recover this install cuz I've got MANY apps installed and configured and I invested hundreds of hours in researching and testing settings to make unity bearable.

Anyone got any suggestions?

Isn't ext4 supposed to be easier to recover because of "journaling"?  OTOH, this is probably just a glitch from interrupting the final shift from 12.10 to 13.04.  I'm sure the upgrade process was over and just waiting for a final <enter> to reboot.

Any assistance greatfully received.

Final note: I don't know if this affects the situation but I should note an unconventional use of this partition within the "old" system.  On the "old" root in /home, there is one entry for each of the two 'users' (johnb and family) as one would expect except that instead of being directly the HOME for each user, each entry is a link to a bottom level dir on /dev/sda3. I did this because I was running out of room for all my files. OK, I admit that just moving the entire /home tree to a separate partition seems to be more standard but this is what I have to deal with.  I don't know if a ubuntu boot will hand if it can't access HOME for the users.  I also don't know for sure that it can't.

I can mount /dev/sda3 from the new {clean} boot. Nautilus shows all the bottom level folder names but classifies them as "unknown type".  With the CLI and sudo I can walk the data tree to any level but can't open any files. This is 159,000 files that are backed up but to a bunch of different media which would take days to sort out.  So I used ddrescue to clone the partition to an external HDD and experimented on that.  Everything looked the same as looking at the original partition and everything I tried complained about "permission".  Owner of everything was root so I did 

sudo chown -R johnb:johnb 

on it and now everything is accessable. So maybe this is an artifact caused by the bottom level of this partition belonging to "old root"  and not "new root" or some such and has nothing to do with the boot error message.  I just don't know.

Full Disclosure: I was a pretty good "guru" type up until I retired 16 years ago.  Now I mess with admin stuff only as much as I must to in order to tame my computer.  Everything I did here was step by step over a week and after HOURS of research online.  I only vaguely understood what I was doing most of the time so .... have a little mercy.

---

### Post by darkod on 2013-06-18
Can you start the recovery mode of your old install that you were upgrading? If you can, select Drop to root shell from the recovery menu that shows up, and once in the shell remount the root partition as RW (it's mounted as read only in recovery):
```
mount -o remount,rw /
```

Then try to finish configuring any outstanding packages and fixing any broken dependencies:
```
dpkg --configure -a
apt-get install -f
```

See if that helps to get the system going.

I wouldn't have started changing ownership of your home folders just yet. If you manage to repair the old system not sure if changing the ownership can affect it.

---

### Post by jbuczek on 2013-06-19
OK.... that got me most of the way.  

I can now boot both the "old" and "new" installations.

The "old" one says it's 13.04 but the Software Updater tool says I have 1259 updates to do.  When I say OK, it says it cannot do all of them .... attempt partial update or cancel.  When I choose the partial it says

"update from raring to quantal is not supported by this tool".

which of course would be a downgrade.  Any way to remove the confusion from the poor little penguin? 

I suppose that after all this I really should move everything carefully over to the clean install but I don't know how long that will take and I'm nervous about having a potentially unstable system.  I've got to learn how to move Vbox VM's among other things.

Thanks, BTW, for the instructions.

About changing ownership of my files.... I guess I wasn't clear.  I was NOT changing ownership of the original files.  I was changing ownership of a clone of the data partition I made onto an external drive.

---

### Post by darkod on 2013-06-19
Look in /etc/apt/sources.list whether they point to 13.04 or 12.10. I'm not really sure where it can get stuck, you never know with a stopped upgrade. If the sources are correct, for 13.04, try doing the apt-get update to update them, and see how it goes after that.

---

