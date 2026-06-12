---
title: "which ntfs-3g driver for Jaunty?"
date: 2008-11-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-11-14
Hi all, 
 Any idea which ntfs-3g driver would be done for Jaunty?

The one which we have in our repository is 1.2506-1ubuntu2 while in debian all of the ones are newer 

I also saw the ntfs-3g site and these are the releases after what we have got 

[http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

**[COLOR=green]STABLE Version 1.5012 (October 12, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/638") **

 
[LIST]
[*]Version 1.2926-RC is released unchanged as stable. The NTFS-3G driver         is able for unlimited file and directory creation and          removal as the result of 13 years continuous development with the          help of hundreds of contributors over these years. Congratulations         And Thank You To Everybody Who Made It Happen!
[/LIST]
   **[COLOR=red]TEST Version 1.2926-RC (September 19, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/635") **

 
[LIST]
[*]New: Support unlimited file and directory creation. Successfully        tested the creation of 54 million (54,000,000) files in a single         directory, besides [the other test cases]("http://ntfs-3g.org/quality.html").
[/LIST]
  **[COLOR=green]STABLE Version 1.2918 (September 18, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/635") **

 
[LIST]
[*]Fix: A corrupted directory index entry could hang the driver instead of              returning ["I/O error"]("http://ntfs-3g.org/support.html#ioerror").
[/LIST]
  **[COLOR=green]STABLE Version 1.2812 (August 15, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/632") **

 
[LIST]
[*]Fix: The allocation size of an attribute may got corrupted if the attribute              size change failed.
[*]Fix: An MFT record could leak on big-endian CPUs if adding             a new attribute failed.
[*]Fix: The system log was flooded if a transparently compressed or encrypted              file was tried to be updated repeatedly.
[*]New: Solaris support.
[*]New: Libtool-2 support.
[*]Change: No external dependency on librt anymore when internal FUSE is used                 (default on Linux).
[*]Change: The default compiler is gcc.
[*]Change: Internal FUSE further shrank by 10%.
[/LIST]
  **[COLOR=green]STABLE Version 1.2712 (July 12, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/607") **

 
[LIST]
[*]Fix: A corrupted size directory or a directory over tens of million files may hang              the driver. If NTFS-3G is compiled with an external FUSE library (non-default              on Linux) then FUSE CVS is needed until FUSE 2.8.0 is released.
[*]Fix: Removing alternate data streams and extended attributes leaked memory.
[*]Fix: Mount could fail with some mount(8) utilities (e.g. busybox one)              if the /etc/mtab file didn't exist or was on a read-only file system. This             fix should solve most of the "/bin/mount: invalid option -i" mount problems.             If NTFS-3G is compiled with an external FUSE library (non-default              on Linux) then FUSE CVS is needed until FUSE 2.8.0 is released.
[*]Fix: The driver always returned "I/O errors" if the standard file descriptors were              closed during mount, e.g. via some usage of udev, hotplug, etc.
[*]Fix: Building the driver failed if the --prefix=/ configure option was used.
[*]Fix: Driver compilation may failed with 'PATH_MAX undeclared' error message in some              (cross)-compilation environments.
[/LIST]
  **[COLOR=green]STABLE Version 1.2531 (May 29, 2008)[/COLOR] -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/588") **

 
[LIST]
[*]Fix: Mount failed with *"Invalid argument"* error message if the mountpoint              was a symlink. If NTFS-3G is compiled with an external FUSE library (non-default             on Linux) then FUSE CVS is needed until FUSE 2.8.0 is released.
[*]Fix: A corrupted directory could hang the driver.
[*]Fix: Mount could hang if the block allocation map was corrupted.
[*]Fix: The driver could hang or misbehave when compressed, sparse or encrypted             file attribute flags were corrupted.
[*]Fix: The driver could crash when both an MFT attribute offset and the              allocated bytes were corrupted.
[*]Fix: Building the driver failed if the --exec-prefix *configure* option was              used without --sbindir=/sbin.
[*]Fix: Parallel 'make install' may failed.
[*]New: Support building the driver in a separate directory.
[*]New: Added --enable-mount-helper *configure* option which installs              */sbin/mount.ntfs-3g*, so mount via mount(8) and /etc/fstab can work             on Linux. The default is enabled on Linux and disabled on all other             operating systems.
[/LIST]
 It would be nice if we could get the version 1.5012 in Jaunty

Thoughts, suggestions, improvements to the same welcomed. 
[B][COLOR=green]
[/COLOR][/B]

---

### Post by plun on 2008-11-14
"Merge o matic" is running and it seems to be a patch

[http://merges.ubuntu.com/n/ntfs-3g/](http://merges.ubuntu.com/n/ntfs-3g/)

Entrance for "mum"
[http://merges.ubuntu.com/](http://merges.ubuntu.com/)

---

