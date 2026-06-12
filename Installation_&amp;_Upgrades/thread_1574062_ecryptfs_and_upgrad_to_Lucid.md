---
title: "ecryptfs and upgrad to Lucid"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by revtds on 2010-09-13
My system is listed in the signature, and I had a working 9.10 system [sda5,6,7]with a new 10.04 [sda8,9,10] installed beside it.

I copied my root and home partitions [sda6,7] to a second hdd sdb, using gparted booting from the 10.04 partition and then rebooted the 9.10 partitions, and ran an upgrade from 9.10 to 10.04 using the update manager.

I was impressed by a seamless, clean install that preserved all of my files, programs, settings, desktop, backgrounds, desktop links, etc., yada, yada...

After a week of experimenting, and everything appearing to be in good shape, I decided to delete the old copies of root and home on sdb in order to make a new partition I could use for Grsync to start doing timed backups.

In the process, I have discovered that I am booting 10.04 from root on sda6, which is what I would have expected, but my home directory is now sdb2, the partition I copied sda7 to prior to upgrading to 10.04.

ecrypt is running, making the whole thing very scary for me, after reading all kinds of posts about ecrypt doing strange things if you move partitions/files around.

My question - not caring how it happened, how do I undo it, get my data secure, and running from sda7 again, instead of sdb2 as it is now?

Additionally, I would like to get rid of ecrypt, until I better understand it and can make intelligent decisions about it.

Help??!?!?

---

### Post by revtds on 2010-09-29
As weird as this sounds, my Ubuntu machine just changed the /home directory for no apparent reason that I know of.  The post above tells the install story, which no one replied to, and now, this morning I noticed a whole lot of my email addresses recently added have disappeared.

Looking in Gparted, my /home partition decided it wanted to be next to my / partition and is now in sda7, as opposed to the sdb2, which is still labeled home, but is no longer mounted.

Could someone weigh in on this and help me figure out how to get this straightened out, so I feel like my data is secure?

HELP!

---

### Post by revtds on 2010-09-29
Still looking for some help on this issue.

I got curious and was looking at the drives using GParted, and discovered that sda7 and sdb2 have identical UUID's.

I didn't think that was possible, and yet I have two partitions on two distinct hdd's with identical UUID's.  No wonder it flops back and forth as to which partition it mounts as my home directory.

Now what?

---

### Post by revtds on 2010-11-24
see this thread for solution

[http://ubuntuforums.org/showthread.php?t=1585003](http://ubuntuforums.org/showthread.php?t=1585003)

---

