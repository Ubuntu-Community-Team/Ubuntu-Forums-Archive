---
title: "2nd hard drive not mounting"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by ciscoookid on 2007-06-04
I installed Ubuntu Studio onto my second hard drive (an 80 gig) after trying a dual boot with Fedora 7 on my 1st hard drive. The dual boot didn't work, and now I'm having a lot of difficulty mounting the first hard drive into file system. I tried everything I could find in different posts. 

Is there a way to mount it into filesystem so that all of it shows up as one giant mass of memory? I know it's possible in Fedora, but I can't use that as my wireless won't be supported. I'd greatly appreciate any help I could get. My first hard drive is 120 gigs, if that matters.

---

### Post by x64Jimbo on 2007-06-04
You want to use two hard disks as one filesystem? That's quite risky, as failure of one of them would cause the whole filesystem to crash. You should have each hard disk as its own partition. You can mount the hard disk as a separate partition by adding it to your /etc/fstab and then rebooting, or you could mount it as a one-time operation using the mount command.

---

### Post by ciscoookid on 2007-06-04
I already figured all that out about adding it into the /etc/fstab, but it will still mount as a seperate hard drive. I want it all to be one big pile of memory, like I had it in Fedora. My one complaint about Ubuntu is that it makes it difficult to do things like this. 

I know it's risky, but I don't want it to mount as a seperate hard drive, as I already have an external hard drive (250 gigs). How would I go about mounting the hard drive into filesystem?

---

### Post by confused57 on 2007-06-04
See this guide for mounting different filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by x64Jimbo on 2007-06-06
You'll want to look into software RAID. Apparently it's a feature only found in the Alternate Install CD. Here's a tutorial for it:
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
You'll want to look up the different kinds of RAID (0,1,5) before you do it.
If you stripe it, may the force be with you. I have had too many hard disks physically break to try anything that risky.

---

