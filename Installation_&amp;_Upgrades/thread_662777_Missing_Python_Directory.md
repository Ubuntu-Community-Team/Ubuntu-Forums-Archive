---
title: "Missing Python Directory"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by SiameseLoki on 2008-01-09
**Warning Linux n00b looking for help**

Hi all!!

I am trying to setup a Zenoss Core management system on a spare desktop for trial testing.  (I have succesfully installed Zenoss on an Ubuntu 7.04 Desktop, but now am trying to install on Ubuntu 7.10 Server).

I am faithfully following the install guide from this post [http://ubuntuforums.org/showthread.php?t=591727](http://ubuntuforums.org/showthread.php?t=591727).
but have seem to run into a strange problem on step #10.

[B]10. Gutsy Gibbon ships with Python 2.5, but certain dependencies of Zenoss are
unable to build properly with this version. Once Zenoss has been installed,
it will run just fine under 2.5, but we'll need to change the symlink for
the installation. Run:

unlink /usr/bin/python && ln -s /usr/bin/python2.4 /usr/bin/python[/B]

When I try to run this command I get an error...
*unlink: cannot unlink '/usr/bin/python': No such file or directory*

If I list the directrory /usr/bin  then sure enough there is no 'python'.

But if I try to 'apt-get install python' it tells me that python is already the newest version.
I also tried to 'reinstall' python and it seems to go through the process cleanly but "No-Joy".

I have tried searching the forums and google and broke out a few of my Linux books, but am about ready to admit defeat in the arena of "IT self-sufficency".

Can anybody help me with this one??

Thanks,

--Will

---

