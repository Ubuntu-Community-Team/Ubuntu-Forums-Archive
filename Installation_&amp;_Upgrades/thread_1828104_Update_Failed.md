---
title: "Update Failed"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by wagb278 on 2011-08-18
Running Ubuntu 10.04 LTS, 32-bit.

Update fails. Synaptic Package manager indicates one broken package identified as "linux-headers-generic" version: 2.6.32.33.39.

The error details are:
```
E: /var/cache/apt/archives/linux-headers-2.6.32-33_2.6.32-33.72_all.deb: unable to create `/usr/src/linux-headers-2.6.32-33/arch/score/include/asm/unaligned.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-33/arch/score/include/asm/unaligned.h')
E: /var/cache/apt/archives/linux-headers-2.6.32-33-generic_2.6.32-33.72_i386.deb: error creating symbolic link `./usr/src/linux-headers-2.6.32-33-generic/include/linux/atm_nicstar.h'
```

The download completes OK. The error(s) appear during the install phase.

Only possibility I can think of is Linux is installed on a small physical HD (6.01 Gig). Gparted says there is 1.06 G avail. Could I be running out of space to complete the update?  I have another HD in this machine.

PROBLEM SOLVED - cleaned off files to make space for Update to complete.

Thanks,
Jim

---

### Post by wagb278 on 2011-08-19
UPDATE 

I found that a significant number of files were stored in directory: /root/.local/share/Trash  After removing those files the Update completed successfully. So it was a disk space issue. The files were all linux-header version files.  I cleared out 600 meg of space removing those files.

Does anyone know why those files were there? Shouldn't they be removed after updates complete?

Should I be doing something different or change some configuration setting associated with updates?

---

### Post by Hakunka-Matata on 2011-08-19
these are all good commands for cleaning up, making room.  do a "man apt-get autoremove" to see all the options.

the two directories "/var/cache/apt/archives/ and /var/cache/apt/archives/partial/" are also interesting to look at, and understand.  

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```> 
       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

