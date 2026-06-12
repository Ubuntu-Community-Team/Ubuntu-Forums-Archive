---
title: "mkinitrd &amp; pivot_root: no such file or directory"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by Pustulo on 2005-03-09
I know there are other posts with this message, but they seem to be related to different issues.  Here's my problem:

Previously I had a setup something like this:

/dev/sda2   -   /
/dev/hdb1   -  /oldroot
/dev/hdb3   -  /home
...
etc.

The sda2 installation (disk on SATA interface) was my test installation, the oldroot was my redhat 9 root partition.

My aim was to remove the old RH9 root (after backing up, of course) and move the test installation onto that partition.  I used 'tar' to copy the contents over, and that seems fine.

I also changed the grub menu.lst that was now on the oldroot disk to reflect the new root  partition.   I am pretty certain that the entries in this file are right.  I will happily post the file if necessary.

Now on booting from oldroot (the new root if you will), I get this:

Starting Ubuntu
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!

To me, the error looks like it is happening in the initrd file.  On mounting the initrd in question, I can find everything mentioned in the error including pivot_root (in /sbin), /dev/console as well as the line in /sbin/init that causes the error.

The generation of the initrd appears to use some auto-detection magic from your running system - which of course is no use when moving to a new disk.  The /loadmodules file lists modules necessary to load the SATA drivers and a file called /script has the line:

ROOT=/dev/sda2

I am unable to generate a new initrd if I chroot into the oldroot directory,  I get an error like:

/dev/fd: No such file or directory

It is a symlink into the /proc tree, which of course isn't available in the chrooted environment.

I've learned a bunch about how the boot process works in all this, but the magic of initrd generation alludes me.   What can I do to get a nice working initrd  for this new root tree?

If I was using Solaris I could have had this running days ago!

---

### Post by Nebvin on 2005-03-11
to get /proc working in a chrooted environment, you need to run the command "mount -o bind /proc /mnt/newroot/proc"

---

### Post by Pustulo on 2005-03-13
Excellent!   That did it.  Thank you very much!  The initrd file definitely sets the root partition in its /script file.

I've since read between the lines of the mkinitrd(8 ) man page and discovered that I could have shortened the whole experience by doing:

# mkinitrd -r /dev/hdb1 /boot/initrd.foo

The manpage made no real mention of what the ROOT variable in the config file (or the -r command line arg) could be used for other than with the keyword 'probe'.  I only now thought to experiment with it.

That's at least 3 places that the root partition is recorded in: boot args (grub menu.lst), fstab and the initrd (and potentially the mkinitrd.conf).  It's a shame that the initrd couldn't have been told the root filesystem by the kernel arguments.

Thanks again.
Colin.

---

