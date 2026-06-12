---
title: "Reiserfs - how to prevent complete fsck on boot?"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Stormbringer on 2006-07-27
Hi!

I switched my box from ext3 to reiserfs to get rid of that annoying filesystem check that appears every X mounts or Y days.

As I store lots of files on my box the check on ext3 needed about 45 minutes to complete ... sorry for the rant, but that's not acceptable in any way.

Now that I restored all data onto the reiserfs volumes I rebooted my box and found out that it does a _COMPLETE_ fsck on all reiserfs volumes on boot ("Checking all filesystems" on bootsplash) - although it's faster (~15 minutes) it still isn't acceptable.

Man ... that's plainly annoying ... even CentOS or Fedora installations do a better job here (I know that reiserfs takes longer to mount - but why the hell do we have to do a complete fsck on boot? JOURNALED filesystem, anyone?).

So, the question is ...

HOW do I make the "Checking all filesystems" thingy to shut up on boot for as long as the filesystem is clean and only let it do it's job in case the filesystem(s) is/are dirty (i.e. make it behave the same way as it does on CentOS, Fedora, SuSE, ...)?

EDIT: Forgot to mention that the volumes *are* clean (read: having no errors), so there would be no need to run a complete fsck at all.

Any valueable thought to get this issue resolved would be welcome.

Regards,
Storm

P.S.: If this post may sound slightly bitter please excuse me ... I just spent ~11 hours switching filesystems and restoring data, and this outcome now irritates me bigtime.

---

### Post by RAOF on 2006-07-27
> **Stormbringer said:**
> ...
HOW do I make the "Checking all filesystems" thingy to shut up on boot for as long as the filesystem is clean and only let it do it's job in case the filesystem(s) is/are dirty (i.e. make it behave the same way as it does on CentOS, Fedora, SuSE, ...)?...

The "Checking all filesystems" step **does** only run fsck when the filesystem is dirty, or as you found in the case of EXT3, every 30 mounts or so (unless you tell it otherwise).  Reiserfs, as far as I can tell, performs a minimal sanity check on its internal tree every mount - this makes Reiserfs  slow to mount.  There's no way around it, as far as I know.

You can change the number of mounts before your ext3 filesystem has a fsck forced, though, using tune2fs (the **-c** (# of mounts) or **-i** (time) options).  Also from that man page:
[quote="man tune2fs"]You should strongly consider the consequences of disabling mount-count-dependent checking entirely.  Bad disk drives, cables, memory, and kernel bugs could all corrupt a filesystem without marking the filesystem dirty or in error.  If you are using  journaling  on  your  filesystem,  your  filesystem will never be marked dirty, so it will not normally be checked.   A  filesystem  error detected  by  the  kernel  will  still  force an fsck on the next reboot, but it may already be too late to prevent  data  loss  at that point.
[/quote]

---

### Post by Stormbringer on 2006-07-27
Thanks for your reply RAOF ... although very useful it's not really the solution to the problem.

> **RAOF said:**
> Reiserfs, as far as I can tell, performs a minimal sanity check on its internal tree every mount - this makes Reiserfs  slow to mount.  There's no way around it, as far as I know.

O_o

You are right - upon boot, in the "Checking all filesystems" stage, it performs an check of the internal tree. This, however, can only be witnessed on Ubuntu --- CentOS (with CentOS plus kernel for reiserfs support) and Fedora Core (just to mention the two of them I deployed for server usage in the past) don't behave that way.

If there's no way around that tree check it's next to useless - guess I either switch my desktop back to ext3, and go through the hell of the scheduled fsck's every now and then, or kill the startup script out of the init-process.



However - let me rephrase my question; maybe there's an answer hidden deep within:

Is there ANY filesystem for _Ubuntu_ Linux that behaves the way reiser does in CentOS and/or Fedora ("fast" mount, sanity check only if dirty)?

If all filesystems behave the same way in Ubuntu like reiser does I don't even need to think about delpoying Ubuntu as the server os of choice as the delay on boot is simply insane (I currently have ~200GB of data on my desktop and this causes a startup delay of ~15 minutes --- now imagine a server having 1TB+ of storage space and lots of data on the volumes; just tell me how you explain the "boot-delay" to a client without getting thrown out of the door right away.


> **RAOF said:**
> You can change the number of mounts before your ext3 filesystem has a fsck forced, though, using tune2fs (the **-c** (# of mounts) or **-i** (time) options).  Also from that man page:

I had tweaked that setting already --- to 180 days or 140 mounts; but sooner or later it snaps in without mercy, and the more data you store on your machine the longer it takes to complete. :-(

That's why I wanted to switch to reiserfs as this "problem" doesn't show up there ... at least in, sorry if I stress it, CentOS or Fedora, but this seems to be a dead end in Ubuntu.

-Storm

---

### Post by go2dell on 2006-07-27
ReiserFS won't run a complete check unless it's dirty, and even then it won't run a full check.  For various reasons I quite often have to reboot via the power button.  It's not pretty, but Reiser takes only a few seconds extra to bring itself back into a working state.  This includes my 160GB softRAID 0 partition, which is around 90% full at the moment.  The full mount of ReiserFS shouldn't be any slower than ext3, and much faster if ext3 is configured to allow periodic checks.

A FULL tree check in ReiserFS (reiserfsck --check) pretty much has to be started by hand.  I can't think of a single time I've ever seen it do an ext3-style check on boot.  If yours is doing something like this, there's something else going on.  You might try booting from the LiveCD and running *reiserfsck --check* on the filesystem while it's unmounted.

---

### Post by Stormbringer on 2006-07-27
> **go2dell said:**
> You might try booting from the LiveCD and running *reiserfsck --check* on the filesystem while it's unmounted.

Did as you suggested --- booted off the Live CD (Dapper AMD64) and ran an fsck on the volumes - perfectly clean.

Upon boot of the installed system at the "Checking all filesystems..." line the splash disappears and I see the "internal tree" checks running through (keep in mind that they are clean and have been correctly unmounted).

Reformatted one of the storage volumes as ext3, copied some data back and rebooted.

On the first reboot the ext3 volume gets completely checked as it's newly created ... on the second reboot the ext3 volume gets mounted without futher hassle and the remaining reiserfs volumes still get tortured with the complete tree check.

EDIT2: That's what's going to happen:
. The "Checking root filesystem" is quickly done
. At the "Checking all volumes" stage the splash disappears and I can read the following output...
- Checking internal tree (some output is going on)
- Comparing bitmaps (prints out a "finished")
- Checking semantic tree (some output is going on)
... and in the end...
- No corruptions found (followed by some statistics)

If there's something fishy going on - how do I track down the problem?

I switched from ext3 to reiserfs this way:

- Booted off the live cd (Dapper AMD64).
- Mounted the partitions of the installed system and copied the whole content to another hard drive (by keeping the permissions).
- Unmounted the partitions of the installed system.
- Formatted them reiserfs (mkreiserfs --format 3.6 /dev/sda1 (/boot) sda3 (/) sda4 (/home))
- Mounted the partitions and copied back the backup (by keeping the permissions)
- Corrected the fstab lines to read reiserfs instead of ext3, replaced "defaults,errors=remount-ro" with "defaults" for /, replaced "defaults" with "notail" for /boot
- Restored grub
- Booted the installed system, formatted the data volumes reiserfs, mounted them into place and copied back all data from an external NAS I borrowed from a friend.

I guess that's the correct procedure as I already restored borked systems that way numerous times.

EDIT1: Some background on the hardware of my Desktop --- maybe the problem is related to the hardware in use (although I doubt it):

- AMD Athlon 64 3000+ on an MSI K8T Neo (VIA K8T800)
- Seagate 80GB SATA on SATA Channel 0 (Ubuntu)
- LG 4120B DVD+/-R(W)/RAM on Primary OnBoard IDE Channel
- 160GB Maxtor (VMware Machines), 300GB Maxtor (Data), 400GB Seagate (Cinelerra Video Cache) on an HighPoint HPT370A (non-RAID version of the controller)

EDIT3:
- Fired up Dapper 32-Bit (fresh installtion, only a few days old) inside VMware Server and attached a virtual disk to the VM.
- Formatted the drive reiserfs.
- Copied some gigabyte of junk onto the drive.
- Rebooted
- Same behaviour as on the real installation; a full filesystem check is invoked, no matter how often I reboot, although the filesystem is clean.
- Booted VMware off the alternate install cd of Dapper 32-Bit and invoked an fsck manually just to check that everything's right; and it is.

---

### Post by go2dell on 2006-07-27
Looks as though you're running /boot on ReiserFS?  I'm not sure I was aware GRUB could do that, but then again I don't remember the last time I tried it.

Here's a suggestion:  run everything ReiserFS EXCEPT /boot.  You can run /boot as ~100MB ext2 (you don't really need the journal for storing just kernels and pretty much everything can mount ext2).  If it's a server, you might even tell your fstab to drop /boot so it takes you one extra step to destroy it. :rolleyes: 

About the notail option:  *notail* disables tail packing.  This increases speed, so it's nice if you have plenty of disk space or you're running a heavily-used server.  Otherwise leave it on for a nice space boost (most desktop usage on modern systems).

***edit:*** when using mkreiserfs, don't bother giving it any options except the one partition you're creating.  You can tune later if you solve your fsck problems.

---

### Post by RAOF on 2006-07-27
> **Stormbringer said:**
> ...
I had tweaked that setting already --- to 180 days or 140 mounts; but sooner or later it snaps in without mercy, and the more data you store on your machine the longer it takes to complete. :-(
...

Set it to 0 or -1, and it **disables** the checking.  No more automated fscks (at least, unless the fs is dirty).

---

