---
title: "Problem Installing with Compaq Smart Array"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by YouBunn2 on 2008-04-24
I have been unable to install on a Compaq DL380 with Smart Array. When trying to partition the disk I receive this "Unable to determine geometry of file/device. You should not use Parted unless you REALLY know what your doing."
 I ignore then select /dev/ids/c0d0 -0B0 Compaq Smart Array
then I get Failed to partition selected disks "...free space is too small to be automatically partitioned."



I have read the forums and have used GParted and partioned the array several times to ext2, ext3 and left unformatted and receive the same results.

Any suggestions?

---

### Post by rustybronco on 2008-04-24
yep, stick around and i'll dig it up in about 1/2 hour...

dug up...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110585](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110585)
[http://ubuntuforums.org/showthread.php?t=384319](http://ubuntuforums.org/showthread.php?t=384319)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47526](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47526)
[http://ubuntuforums.org/showpost.php?p=4543258&postcount=9](http://ubuntuforums.org/showpost.php?p=4543258&postcount=9)
I all depends on what version you plan on installing. 6.06.2 lts, 7.04, 7.10, 8.04.

do you have the smart start 5.5 cd for setting up a raid array?
this post may help [http://ubuntuforums.org/showpost.php?p=4764915&postcount=2](http://ubuntuforums.org/showpost.php?p=4764915&postcount=2)

does the server have a remote insight lights out edition? that is the problem for me (almost sure of it) on getting it installed.
 
debian 4.0 is a possibility, as is centos5 (what I have on mine)
what more can I do to help?

---

### Post by YouBunn2 on 2008-04-24
Thanks for the help, but seeing that 8.04 was released today I installed that without any troubles. :guitar:

---

### Post by rustybronco on 2008-04-24
Good to know! what generation dl380 if I may ask.

I guess I will have to try it tommorow on the g1 to see how the final version installs. (tried the alpha, beta and rc versions) might even try the virtual disk install through the r.l.o.e card.

---

