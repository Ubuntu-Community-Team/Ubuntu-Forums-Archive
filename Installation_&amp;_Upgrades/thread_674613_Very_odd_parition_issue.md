---
title: "Very odd parition issue"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Battie on 2008-01-21
Hello again!

A few days ago I posted for help installing a new Windows partition when I already had Ubuntu loaded.

Everything went fine until I decided I wanted to get back into Ubuntu.  Since Windows had blown away the MBR I used the Super Grub Disk to restore GRUB.  But it didn't work, failing with error 17.

A little worried, I booted my GParted disk and was stunned to find that my my hard drive was shown as unallocated.  Stranger still, the size listed was the total of the hard drive except what I had surrendered to Windows.  That bit wasn't even listed.

I booted the Live CD this time so I could find a little help online.  I'm still not sure what happend.  The output of fdisk -l revealed that my partitions were intact.  I also managed to boot back into the real system when GRUB's find utility revealed that I should boot to hd(0,6) instead of hd(0,5).  Not sure why SGD got it wrong.

So, I'm on home turf again, but all is not well.  I can access all of my data on all partitions (yay symlinks?), but GParted still shows an unallocated expanse and Nautilus doesn't seem to know what my other partitions are either.

What the heck did I do here?  Can I get myself out of this mess?

Is it my partition table that's screwed up, or something within Ubuntu?

Thanks!

---

### Post by _Phineas_ on 2008-02-05
What you should do is back up your data, then delete your your partitions.( you can use your xp disk to format it). hope it works I had to delete my partitions once.

---

