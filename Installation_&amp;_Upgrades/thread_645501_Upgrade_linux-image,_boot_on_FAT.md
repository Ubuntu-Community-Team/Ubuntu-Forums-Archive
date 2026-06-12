---
title: "Upgrade linux-image, /boot on FAT"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by RickardJ on 2007-12-20
Hi everyone,

Registered here to post this, so this is my first post. Decent Linux/Unix knowledge, I have used "unix"  for fifteen years and started installing Linux (as a tool/hobby, not obsession) around Debian potato somewhere. 

I have a fairly recent install of 7.10 on my Dell Latitude D400 laptop. The only thing I have changed at the system level, so to speak, is that I converted /boot to FAT to be able to put boot files from both Ubuntu and Windows XP on the same partition. Works fine, both systems can boot and I can keep drivers, manuals, BIOS updates and similar on this partition. 

Ok. On to the problem. Automatic updates wants to install a new linux-image,  2.6.22-14-generic. No go. Neither "Update Manager", nor apt-get gives any info to speak of, so I located the deb archive and tried installing it with dpkg. Seems it wants to do some symlinks, which of course doesn't work on a FAT partition:

```

...
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.46 (using linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
dpkg: error processing linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb (--install):
 unable to make backup link of `./boot/vmlinuz-2.6.22-14-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

Any suggestions on how I might solve this? My idea was to extract the script from the deb file, comment out the backup linking, re-pack it and installing it (with proper forcing options for dpkg, since the checksum of the archive will be changed). Problem is I've never looked inside deb archives before and I can't seem to find the script that wants to backup... 

Any help would be welcome. I might even be prepared to defend my choice of filesystem for the partition :)

---

