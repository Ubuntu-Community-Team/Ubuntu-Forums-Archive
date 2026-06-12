---
title: "chain of errors with /cdrom"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by fsdemir on 2010-12-10
I used to run ubuntu-amd64 fine. I have no problem installing it again either on my machine. Unfortunately I have to replace it with ubuntu-i386. When I tried to install from live cd, it gave an error during boot like:

```
(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs
```

I checked the forums and the general response was to use UNetbootin for installation. I used it (tried both linux and windows versions btw) That seemed to work, as I passed the boot process, but this time during the installation it gave another error:

```
Failed to unmount partitions
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points
Would you like the installer to try to unmount these partitions again?
```

I checked the forums again and it seems like people got it right by manually unmounting /cdrom. When I tried that however, Installer crashes. In the log files I see, 

```
Dec 11 05:45:12 ubuntu ubiquity: cat: /cdrom/casper/filesystem.size
Dec 11 05:45:12 ubuntu ubiquity: : No such file or directory
```

and a few lines later:

```
Dec 11 05:45:26 ubuntu python: Traceback (most recent call last):
Dec 11 05:45:26 ubuntu python:   File "/usr/share/ubiquity/install.py", line 608, in <module>
Dec 11 05:45:26 ubuntu python:     install.run()
Dec 11 05:45:26 ubuntu python:   File "/usr/share/ubiquity/install.py", line 122, in run
Dec 11 05:45:26 ubuntu python:     self.copy_all()
Dec 11 05:45:26 ubuntu python:   File "/usr/share/ubiquity/install.py", line 299, in copy_all
Dec 11 05:45:26 ubuntu python:     assert os.path.exists(fs_size), "Missing filesystem.size."
Dec 11 05:45:26 ubuntu python: AssertionError: Missing filesystem.size.
Dec 11 05:45:26 ubuntu python: 
```

It seems like unmounting the /cdrom caused other problems. What can I do?

---

