---
title: "ALERT! /dev/disk/by-uuid/xxxx does not exist"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by AlphaLexman on 2010-01-23
Fresh install of 9.10. Update all. The update froze at the very end: configuring grub-pc. I let it run like that all night before settling for a reboot while the update manager was still running. (The update also raised the kernel version.)

After reboot, I tried the newer kernel [2.6.31-17-generic] at the grub menu and got this error:

> udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
After 2 minutes maybe, I got this:

> Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/e3c4b139-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist. Dropping to a shell!
I rebooted to the older kernel [2.6.31-14-generic] (recovery mode) and get this error:

> /dev/sda6: Superblock last mount time (Sun Feb 21 12:27:48 2010, now = Sat Jan 23 10:58:45 2010) is in the future.

/dev/sda6: UNEXPECTED INCONSISTENCY; run fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck /home [418] terminated with status 4
mountall: Filesystem has errors: /home
init: mountall main process (400) terminated with status 2
Filesystem check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Here is the output of:

> cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=uuid=e3c4b139-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro single
And, cat /proc/modules gives me a long list of modules (too much to retype for now).

So my hard drive is there. maybe some errors on the / home partition [sda6] and I can get to the root directory.

FYI: MS-win XP still boots fine from grub.

Where do I start in fixing this mess?

edit: changed title.

---

### Post by tonyb_uk on 2010-01-29
Hi I had this error after I installed 9.10 onto my laptop, after installing all the updates.

I went back to the original version loaded in GRUB and went to Systems>Administration>Synaptic Package Manager and received an error, that contained the following

E:dpkg was interrupted, you must manually run "sudo dpkg --configure -a" to correct the problem.

Ran this and was presented with an option to select a GRUB menue. Selected first in list (Package GRUB).

Once completed, Rebooted PC, and selected latest version on Linux from GRUB, and this loaded OK. 

Good Look

---

