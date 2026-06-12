---
title: "[SOLVED] Multiple Linux distributions with a shared data partition"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by minus24 on 2008-07-03
Hi everyone,

Last night I installed Ubuntu 8.04 on my desktop, and it worked perfectly first time!  Even better, GRUB installed fine, and Windows XP still runs as well as it ever did, once it verified its resized partition. 

My goal is to install multiple Linux distributions on the machine, so I can check out the different flavours.  Each distribution will use a shared swap partition and a shared data partition.  Everything else (including the /home directory) will be within that distribution's root partition.  The idea is for all my websites, music, photos, and so on to be accessible from any of the Linuxes.  I'm not too bothered about them being accessible from Windows.  (Though I'll be checking out Ext2 IFS For Windows.)  In all this, I'm trying to follow (more or less) Bart Whiteley's guide at [http://www.novell.com/coolsolutions/feature/11802.html](http://www.novell.com/coolsolutions/feature/11802.html)

With this in mind, I specified manual partition on the Ubuntu install, which seems to have worked fine.  I now have the following hard drive mount points and file system types in /etc/fstab:

/ ext3
/data ext3
none swap

Following section 5 of the above guide. I then created a directory, /data/nick -- I will be the only user on the machine.  I've not moved any dot-files to /data/nick, as suggested in the guide, because I don't yet know which ones can safely be shared across distributions.

My question -- at last! -- is regarding the symlinking suggested in section 5.2 of the guide.  I tried creating a symlink from $HOME to /data/nick...

ln -s /data/nick $HOME/data

... but, being a Linux newbie, I'm not sure how to test whether this worked.  In fact, shouldn't the symlink be...

ln -s /data/nick $HOME

... as there is no data directory within $HOME?

My goal is for $HOME to map to /data/nick, and also (as per section 8.1 of the guide) for $HOME/Documents to map to /data/nick/Documents, and similarly for other standard folders of $HOME.  As far as possible, whenever anything defaults to $HOME, I want the system to transparently use /data/nick.  What is the best way to do this with symlinks?

Any other comments on this scheme would be welcome.  I'm new to Linux, and I have nothing in $HOME as yet, so I'm free to experiment!

Thanks,
Nick

---

### Post by minus24 on 2008-07-11
I solved my own problem -- it was simply a newbie misunderstanding of what a symbolic link is.  I had thought it was a link between two already existing files (or directories.)  Once I got past that misconception the solution to my problem was obvious.

---

### Post by gunashekar on 2008-07-11
> **minus24 said:**
> I solved my own problem -- .
Consider marking the thread SOLVED

---

