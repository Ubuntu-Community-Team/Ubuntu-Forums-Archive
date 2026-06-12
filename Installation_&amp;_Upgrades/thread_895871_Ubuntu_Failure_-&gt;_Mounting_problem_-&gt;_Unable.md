---
title: "Ubuntu Failure -&gt; Mounting problem -&gt; Unable to boot or mount"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by MASEngr on 2008-08-20
I'm having trouble with my Ubuntu installation. The installation has been working and in use. This is a single-boot system, with no Windows stuff installed. 

I recently replaced the motherboard / CPU / RAM to get a speed upgrade. I have disabled the onboard SATA, and the hard drive is in its own IDE cable, as the primary master. The DVD is the secondary master on its own IDE cable. The BIOS diagnostics confirm the drives are configured correctly.

If I attempt to boot from the hard drive, GRUB hangs with the message "Grub is loading, please wait..." It will stay there for at least 10 minutes. Only a power cycle will fix the problem. 

If I run from a live CD, the HDD is not accessible. I get the message "Unable to mount the selected volume. device /dev/hda1 is not removable; could not execute pmount". 

Thus, I can't possibly write to the correct fstab, so please don't suggest that. It will be a waste of time, as the changes can't be written to the HDD. I'm not mounting a second storage drive - the boot drive is unable to mount correctly.

The contents of /etc/fstab are:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0

But like I said, that's from the live CD - I can neither read nor write from the boot disk. This is a regular HDD which had been working up until the time I replaced the parts listed above.

The output of fdisk -l is:
/dev/hda1  *      1    9681  77762601   83  Linux
/dev/hda2      9682   10011   2650725    5  Extended
/dev/hda5      9682   10011   2650693+  82  Linux swap / Solaris

So, it reads the drive correctly, but it just won't let me access it, mount it, nor boot from it. Any suggestions?

Thank you.

---

