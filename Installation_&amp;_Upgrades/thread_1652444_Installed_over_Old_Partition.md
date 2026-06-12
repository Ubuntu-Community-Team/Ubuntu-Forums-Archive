---
title: "Installed over Old Partition"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Fizzixnerd on 2010-12-24
Hey Fellow Ubuntu Users,

So heres the deal - I've been using Ubuntu for about 5 months now and had lots of fun.  I've reinstalled it a bunch of times (because I like to experiment with sudo) and always my home folder has been okay after reinstallation.  To be precise, I select "Specify Partitions Manuall" while installing, and then  I (think) every time I've "deleted" the old partition and installed a new one (ext4 in both cases) in the same 'space'.  Everytime, my home folder has magically survived, and so I've started to take this as granted.

So I tried it again tonight, doing everything as stated above, but this time after reinstall, my familiar desktop did not greet me.  It seems my home folder was erased after reinstall, and I am unsure as to how to recover it (if that is even an option!!)  I looked at recovering partitions, but those HOW-TOs seemed mainly concerned with accidentally deleted ones and the like - somewhat unlike my problem.

I want to stress that I did not reformat the partition, only installed Ubuntu again over top of it.  I shall try the more generic recovery options I've found around the net, but from the looks of them, I am not hopeful.  If anyone has any specific advice they can give me, that will be grand.

I have learned my lesson - backup before reinstalling!

Cheers,
Matt

---

### Post by tommcd on 2010-12-24
For future reference, if you have a separate home partition, you do not need to delete it or the root partition before reinstalling Ubuntu. Just choose manual partitioning as you have been doing. Then choose to format the root partition. Set the root partition to be mount point / (for root). Then select whatever file system (ext4 is fine) that you want for it.
 For the home partition, just choose:
Do not format.
Use as ext4 file system (if that is the file system that your home partition is formatted as).
And choose mount point /home. 
Then select "done adding partitions" and continue with the install. This way your home partition and all it's data will be preserved.

And welcome to the Ubuntu forums!

---

