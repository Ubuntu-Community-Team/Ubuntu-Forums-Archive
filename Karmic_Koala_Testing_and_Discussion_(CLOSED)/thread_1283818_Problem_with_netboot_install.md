---
title: "Problem with netboot install"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nimdae on 2009-10-05
I use netboot installs inside my network because it makes things easier and faster (no CDs to maintain). I loaded up the karmic alternative ISO and created the appropriate configs, tftp repo, and http repo for karmic and discovered there appears to be a problem with the ISO build, possibly. In this directory:

/dists/karmic/restricted/binary-i386

There are two files:

-r--r--r-- 1 root root  20 2009-09-29 06:46 Packages.gz
-r--r--r-- 1 root root 100 2009-09-29 06:45 Release

I ran into this warning when attempting install:

Warning:
http://<address>/<path to>/dists/karmic/restricted/binary-i386/Packages was corrupt

When I compared the Packages.gz to the one from jaunty in the same location, it is considerably larger:

-r--r--r-- 1 root root 1786 2009-04-20 09:02 Packages.gz

The Packages.gz in karmic is a valid gzip file, and extracts to an empty Packages file.

The preseed file I'm using is the one I used from jaunty, which was copied and updated from the one I used with intrepid. I had not had any problems with it up until now, having only needing to update it to include new features. I'm not sure where to look to see if this is the problem, just yet.

The warning dialog gave me the option to continue, so I did. The installation appears to have completed, but I'm concerned that something may not be quite right with it.

---

### Post by Nimdae on 2009-10-06
I took a rough peek through my preseed files and could not find anything, off hand, that would be causing this. I did comment out a suspect line, but it didn't change the problem.

I checked the server distribution ISOs (I'm attempting a server install via netboot install, I have a separate preseed file for desktop installs as well) and found the same Packages.gz file was the same as on the alternative ISOs. This leads me to believe that the problem is with my preseeds.

I guess I'll just keep hacking at it for now and if I can't find the problem, I'll post the preseed files for more eyes to look at.

---

