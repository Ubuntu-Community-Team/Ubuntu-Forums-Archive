---
title: "Strange fstab problem after 8.10 upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by whyamihere on 2008-11-01
Hi,
Upgraded to 8.10 last week, and I'm having some trouble with my hard drives.

I run the OS off a SATA disk, sda, this boots fine. I also have a second SATA disk containing all my media files. The problem is that this second disk seems to alternate between being called sdb and sdc for some reason. As a result, when I put it into fstab, the next time it switches it will not be mounted because it's not there. I can mount it fine using the mount command having found out what name it's using in gParted.
There is also a third disk in there, which appears to be displaying wrong. It's a PATA drive, so should be labelled as hda in theory, but it's instead being labelled as sd*, and switching between sdb and sdc depending on what my storage drive isn't taking up. (This third drive contains my test setup which I can boot into separately when I don't want to risk breaking my main installation). 
I basically just need a way to make sure that the second and third drives keep the same drive name so that I can create a proper entry for them in fstab.
Thanks in advance, Chris.

---

### Post by PA_Dummy on 2008-11-04
I had the same problem.

I changed GRUB to boot kernel 2.6.24-21-generic.

The install default was kernel 2.6.27-7-generic.

This solved the problem

__

---

### Post by whyamihere on 2008-11-04
Ah, that might be a problem, I allowed the installer to removed the .24 kernel as part of the cleanup process.

Thanks for that. If it's a kernel issue then there's not a lot I can do until the next release as the .24 kernel's been removed from the repos.

---

### Post by jimv on 2008-11-04
The 24 kernel is Hardy's kernel.  DOn't use it.

The solution is rather simple.  Instead of using /dev/sdb or /dev/sdc in your fstab file, use the UUID for that drive (doesn't change).  The line will look like this:

UUID=bf3ecdec-ca1c-4f1d-86d0-b7540f3e6420  /media/storage     ext3   users 0 0

You can get the UUID by typing 'sudo blkid' in the command line.

---

