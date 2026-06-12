---
title: "Karmic installer doesn't see Windows 7"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Acc3ss on 2010-04-06
Hey all,

I recently did a fresh install of Windows 7 on my laptop, then shrunk my partition and set aside some free space for Ubuntu. When I went to install Ubuntu, however, it told me that no operating systems had been detected on the system. I ignored this message and just installed Ubuntu on the free space, but when the installation was finished, GRUB failed to recognize Windows 7 as well and would only boot into Ubuntu.

After several attempts at getting GRUB to see W7, I eventually gave up and used my W7 CD to reinstall the Windows bootloader which, naturally, didn't detect Ubuntu and would only allow me to boot Windows.

I've tried messing around with my Windows partition a bit, but no matter what configuration I use, I can't seem to get the Karmic installer to see it. I've resorted to using WUBI for now, but I'd really like to have Ubuntu on its own partition in case something goes wrong with Windows; plus, I'd love to be able to use ext4 and GRUB. Anybody know how I can get around this issue?

PS: I've used the same install CD on several other machines with Windows 7 and it recognized them just fine. It's only this one computer that's having the issue.

---

### Post by oldfred on 2010-04-07
I have seen several others with similar issues. If you have already made the win7 partition smaller (best to do with the windows tools)  and understand a little about parititions, you might try downloading gparted liveCD or partition magic CD and set up the partitions for root (/), swap and optionally /home. Then you can use the manual install and select the already created partitions to install to.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://partedmagic.com/](http://partedmagic.com/)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Beanmonster on 2010-04-07
Has anybody had any luck solving this issue?

My 9.04 CD detects  Win7 but my 9.10 CD refuses... Neither does Grub2 :(

**Edit**

Just  missed Oldfred's reply. I managed to install via the setup partitioner,  manually. 
Trying to configure grub2 to boot Win7...

Thanks  for the links :)

---

