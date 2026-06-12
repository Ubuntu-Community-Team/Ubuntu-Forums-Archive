---
title: "Grub Error 17, pretty sure its ReiserFS. Options?"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by electrosoccertux on 2005-06-14
I've been having error 17 for some time now....problems with Fedora, Ubuntu, and just about any other distros I've tried that that use Grub. I've been reading around and this seems to be a pretty common problem with Grub.

I believe my problems are stemming from the fact that I want to use reiserfs. Ext3 is not an option (its just too slow); I really like rfs.

Error 17 is selected partition is seen but not understood...as in the grub doesn't support that filesystem. In searching around in these forums and on lq, the majority of the people who were using reiserfs were getting error 17...so I'm assuming thats what the problem is.

I've got hda2 as my linux partition (last 25Gigs on a 60Gig drive, this is the reiserfs partition) and my swap (this doesn't have anything to do with booting does it?) at the very end at hdb3 on my 160GB hdd.

So can I use grub with my reiserfs so that its pretty on boot? I haven't had these problems with lilo. I'm in ubuntulive right now, so if grub won't work out, how would I install lilo? I've mounted /dev/hda2 (the reiserfs drive) as /mnt/ubuntu.

Thanks!

btw since this is a problem I've been having with all my grub installations, a way to fix this for sure would be cool so I can do it in the future with other distributions should I ever need to [*gasp*] switch away from ubuntu. Would lilo installation via a live cd work for the others as well?

---

### Post by electrosoccertux on 2005-06-14
OK I'm really sorry about all that.
Setting your motherboard hard drive settings to LBA or Large should take care of this.
I checked my BIOS just to make sure that I had it on Large/LBA...and I did. But it was on "Manual" -> "LBA". I had to change it to "Auto" -> "LBA". Go figure.

I've got a Shuttle AN35N-Ultra/400. Just in case anyone has one and can't get theirs working, put it on Auto -> LBA.

Thanks for those that read my post.

---

