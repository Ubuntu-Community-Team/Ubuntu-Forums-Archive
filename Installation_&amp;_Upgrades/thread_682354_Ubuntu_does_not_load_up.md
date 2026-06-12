---
title: "Ubuntu does not load up"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by popiculo on 2008-01-29
I am a new user to Ubuntu or linux in general so please keep that in mind.  As a suggestion from a friend of mine I decided to give Ubuntu 7.10 a shot.  Installation went smoothly for the most part.  My issue seems to be that the operating system does not load up.  Once the computer starts up it directs me to what looks like a Grub command prompt. As per his recommendation I used the XFS file system.  After doing some research I see that Grub and XFS are not compatible.  My question is, how can I fix this without having to reinstall Ubuntu? And if I have to reinstall, how would I go about installing without Grub as a boot loader?

Any help is greatly appreciated. Thanks.

---

### Post by logos34 on 2008-01-30
That's the one drawback with XFS--you need a separate (ext3) /boot:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

or

[http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/](http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/)

---

