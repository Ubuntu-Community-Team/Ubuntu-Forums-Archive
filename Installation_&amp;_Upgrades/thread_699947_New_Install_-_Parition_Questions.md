---
title: "New Install - Parition Questions"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by aetherh4cker on 2008-02-17
I'll be reinstalling Ubuntu from scratch (speaking of which, any word on when the next Ubuntu will be released?) and I had a few questions about parititioning.

I'll be splitting some things into their own partitions, and I want some opinions on what some good sizes for them are.  This will either be on a 160 GB hard drive, or a 500 GB hard drive.

/ - I was thinking of giving this about 30 GB.

/var - Not sure if I'll put this in it's own parition or not, heard it's sometimes good to do.

/usr - Same as above, not sure if I'll give it it's own partition.

/tmp - Pretty sure I want this in it's own partition, but have *no* idea how much space to give it.

/boot - I was thinking of giving this one about 200 MB.

/home - The rest of my hard drive.

swap - Equal to my RAM.  (1 GB)


I read up that Ubuntu offers near fully encrypted installations (everything but /boot) and I think that's what I want to do.  From what I could tell, it had /boot as a primary partition, unencrypted, then everything else as logical partitions in an encrypted LVM?  Does that sound right?  Cause that is what I'm going to attempt to do.

So I guess what I'm asking is:
- If my encryption scheme will work, and...
- Recommendations on sizes for each partition.

Thanks in advance for any input!

---

### Post by TuxImpersonator on 2008-02-19
A much simpler set-up is to put all but /boot and /home in one partition. You could the rest in different partitions but I don't know of any real advantage to this. So depending how many large programs you want on your systems I'd say 50-60Gb is plenty for all the /etc, /tmp,... stuff and have your /home folder on a separate partition to the rest. Or do you want the different partitions?

As for the encryption I'm not sure; someone else will have to help on that one.

And the stable release of the next version of ubuntu is expected in [April 2008]("https://wiki.ubuntu.com/HardyHeron/Alpha1"):

---

### Post by dstew on 2008-02-19
I think for encryption the OP is correct, that you want an unencrypted /boot partition, and the rest can be encrypted. 200 Mb for /boot is fine. A bit smaller is fine too, but maybe the kernel images used with encryption are bigger, or there are some extra files, so go with 200 Mb.

---

