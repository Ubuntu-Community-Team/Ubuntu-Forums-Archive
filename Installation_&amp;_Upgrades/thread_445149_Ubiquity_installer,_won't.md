---
title: "Ubiquity installer, won't"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2007-05-15
Hi -

I've been using Dapper LTS for most installs but decided to wipe Mandriva on one of my laptops and install (Kubuntu) Feisty from the CD .iso (i386).  KDE comes up, I click on the "install" icon, I get a window for a couple of seconds, then nothing.  I tried to run it from a terminal:

```

ubuntu@ubuntu:~$ ubiquity
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
python: tzfile.c:344: __tzfile_read: Assertion `num_types == 1' failed.
Aborted (core dumped)

```

Then again, using sudo:

```

ubuntu@ubuntu:~$ sudo ubiquity
python: tzfile.c:344: __tzfile_read: Assertion `num_types == 1' failed.
Aborted (core dumped)

```

I did a search on this forum and found several similar threads, but these showed the same error messages coming up with different applications.  It appears to be a Python problem.

I did have another issue when trying to run the Mandriva 2007.1 upgrade (over 2007.0) in the same laptop...the install bombed, saying it couldn't read the CDROM drive (but it obviously had up until that point, because I had gotten a quasi-GUI requesting options for the install).  That is not a Python app, though. 

The machine is an old Dell Inspiron 8100 w/ 1GHz P-III and 512M of RAM and old NVidia video.

Anyone else seen this and have a workaround?

Thanks
Bob

---

