---
title: "Change mount point"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by maspai on 2012-02-08
I have one partition in harddisk as root. So, all system files are in that partition, including home.

What if I add another partition as home (mount point), through eg. gparted? Will files in home be accessed from this new partition? Or still in the first one?

Thanks for the answers. God bless you all.

---

### Post by Grenage on 2012-02-08
There would be a mount point (be it in /media, /mnt, other), and the files would be accessible through that.  You could mount the partition and have a symlink anywhere, or added as a favourite, or simply set the mount point to be in your home directory.

---

### Post by Lars Noodén on 2012-02-08
The files in the original /home folder would be hidden under the new mounted directory and not accessible.  To move them over first mount the new /home somewhere else like /mnt or something.  Then copy the files over from /home with [tar](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tar.1.html) or something.

---

