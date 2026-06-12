---
title: "triple-boot."
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2008-03-03
Hi there guys.

I have a dual-boot Virista/Ubuntu, but I want to test out other Linux distros as well.  I know I *could* run a live CD, but I find that these give very little idea of how easy a particular distro will be to set up drivers etc.  So, I was going to re-partition my HD by removing space from the NTFS shared data partition to create a new ext3 partition onto which I can install Mint, Debian, gOS etc and test them out.

Now, my question is:  Can I tell them to install the /home in the same pace as the /home is currently for K/Ubuntu, or will this screw up my K/Ubuntu settings, meaning I'll need a fresh /home partition (or do without and leave it as a directory within root?)  I don't wanna over-complicate by having 7 partitions!

Additionally, will these adjust grub or will I need to do it manually?

---

### Post by fazavon on 2008-03-03
Why not just use Virtualbox or VMWare? They are both free.

---

### Post by koen plessers on 2008-03-03
Hello

When you have windows and ubuntu and you want to install a third distro, it wil recognize the distro's already present.

Also, the new distro will check the available disk space and make a proposition accordingly.

For more info, read this document: [http://portal.dfpug.de/dFPUG/Dokumente/Partner/Linuxtransfer/installation_multiplelinuxdistributionsononemachine.pdf](http://portal.dfpug.de/dFPUG/Dokumente/Partner/Linuxtransfer/installation_multiplelinuxdistributionsononemachine.pdf)
Although dating from 2004, it still contains useful information

Bye

Koen

---

### Post by jken146 on 2008-03-03
It isn't really advisable to share a /home partition between distros, because many programs store their settings within your user's home directory.  Different distros have different versions of the same programs, and so you could run into problems.

The best thing to do is probably to keep the home directories for each distro on the / partitions and have a separate partition just for storing your personal files.  If you already have a Ubuntu istallation with a separate /home partition, it's OK to keep that, but mount it as /media/storage or some such under all the other distros.  See [www.psychocats.net/ubuntu/mountlinux](www.psychocats.net/ubuntu/mountlinux) if you're unsure how to do this.

---

### Post by ajgreeny on 2008-03-03
As jken146 says DON'T use the same /home for all the distros as it will cause all sorts of problems.  Even your desktop will have a major headache trying to find the right background and application icons.  Just use as small a partitionas you can for / and don't bother with a separate /home for the test distros.  If you find something you really like, then will be the time to give it more space and make that with a separate /home.

---

