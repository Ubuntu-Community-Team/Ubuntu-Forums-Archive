---
title: "Installing via USB - No CD-ROM Detected"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Jericon on 2010-05-17
When I am installing 10.04 Server LTS off of my USB Drive (I do not have a CD-ROM in my file server), I receive an error "No Common CD-ROM Drive was detected."  No matter what I try, I can't get it to install from the USB Drive, even though it boots from it.

I have tried Help -> F6 -> install cdrom-detect/try-usb=true  as recommended in the wiki, but it doesn't work.

Any ideas or suggestions?

Thanks in advance,
-J

---

### Post by Merath on 2010-06-09
Same here, anyone got any ideas?  I tried the detect-cdrom/try-usb=true option as well.  I can mount the usb media on /dev/sdb but it still doesn't move forward with that.

---

### Post by Fusion855 on 2011-01-10
I am having the same issue.  Trying to install AMD64 10.10 server on a box with no optical drive.  

I've tried the above method to no avail.  Am currently downloading Hardy Heron and hoping to run an update to get things working.

This sucks.

---

### Post by macdewar on 2011-03-10
Same problem.
Did installing older Ubuntu and upgrading afterward work?


EDIT:  Solved via: [http://ubuntuforums.org/showthread.php?t=1550317](http://ubuntuforums.org/showthread.php?t=1550317)

summary:
After you make your USB installation media based on some ubuntu-dist.iso file, copy the ISO file itself on the installation media also, and mount it as a CD-ROM device during install.

---

### Post by DrDim on 2011-03-10
I had some problem with USB installation of Ubuntu 9.04 server. Finally solved everything and got preseed to work also. One thing that helped against the "cdrom detect" problem was to copy the initrd.gz and vmlinuz from images hd-media.
[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/hd-media/) for example

---

