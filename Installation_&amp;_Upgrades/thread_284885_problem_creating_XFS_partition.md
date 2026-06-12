---
title: "problem creating XFS partition"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by syxbit on 2006-10-26
i wanted to try out XFS as I heard it was good.
upon installing Edgy i chose
20GB ext3   ---  /  
70GB XFS    ---  /home
2GB  ext3   ---  SWAP

it says i can't use XFS for "/" but i'm clearly not doing that.

any ideas ?

---

### Post by wkulecz on 2006-10-26
I don't think the qtparted program can format xfs yet.  I've only used 6.06 and Knoppix 5.0.1, so I could be wrong about edgy.  I had to install to ext3 leaving my xfs partition blank.  I then did mkfs.xfs /dev/whatever and added a mount line to /etc/fstab.  Mount it initially on say /mnt, copy your /home/ directories to it and reboot with it automounting on /home and away you go.

I'm using xfs on a mdadm created raid1 array mostly serving up shares to windows boxes.  Has worked great so far.

--wally.

---

### Post by kidders on 2006-10-26
Hi there,

Sounds like a glitch in the installer maybe? Perhaps you could just change the filesystem type *after* the install.

XFS is a good industrial filesystem, designed with a very specific purpose in mind. Just in case you don't already know, _do not_ use it unless you have a UPS. (Just checking!)

---

### Post by wkulecz on 2006-10-26
No file system cas protect against the power going down while disk writes are in progress and the resulting disk corruption.

I'd be intrested in what evidence you have that xfs is less robust than ext3.  XFS certainly seems faster for most everything on large (>200GB) drives.

--wally.

---

### Post by kidders on 2006-10-26
Hey again,

I mention UPS protection for XFS because (a) XFS is very RAM-intensive and (b) it uses metadata only journaling, so it is certainly a _far_ worse performer than Ext3 (in data loss terms), in the event of sudden power loss. It focuses on filesystem consistency, rather than data recoverability (which is almost impossible in XFS, anyway).

> No file system cas protect against the power going down while disk writes are in progress and the resulting disk corruption.XFS does a pretty good job at this ... it's one of the advantages it has over some other filesystems. In simple terms, you could almost say that it does this by *guaranteeing* data loss when the power dies suddenly.

Information on XFS is available at [http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/).

Have fun trying it :-)

---

### Post by emerika on 2006-11-08
I would like to say that I have had the same problem. I want to point out that it's worse than indicated. If you create ANY partion that is XFS it will fail. Not only does it fail, but if you use the back button to change things you will see that all the partions except the swap indicate they are xfs.

I carefully choose this configuration:

swap -> swap
/ -> ext3
/boot -> ext3
/home -> xfs

After it makes the bogus complaint that I am trying to format / as xfs, I back up and my partions are marked thus:

swap -> swap
/ -> xfs
/boot -> xfs
/home -> xfs

I suggest that if XFS or JFS (same problem -- really they say xfs and everything) aren't supported, they should NOT be options.

emerika

PS I read the documentation on XFS and speedy recovery from crashes is touted as a feature -- NOT a problem.

---

