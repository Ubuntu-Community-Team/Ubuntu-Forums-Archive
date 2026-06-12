---
title: "Install Ubuntu/Kubuntu with encrypted root filesystem using LUKS"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by tdn on 2007-05-05
How do I install 7.04 with encrypted root file system using LUKS? 
I have not been able to find any HOWTOs on this for 7.04. Only for Edgy, but I've heard that it should be supported by the installer in Feisty. 
I have tried booting up on the alternate CD. But I cannot find anything about encrypted file systems in the partitioner. 

In Edgy this was done by creating an extra partition for the base system. After installing the base system to the extra small partition. Another large partition was set up with dm-crypt. Then all the files from the extra partition was copied to the new large encypted partition. GRUB entries was set to point to the new partition and then the new partition was used as rootfs. However, this process is tedious and you loose some of your disk capacity by having to create the extra partition for the initial installation. I actually wrote a HOWTO on this: [http://thomasdamgaard.dk/blog/article/krypteret-swap-og-root-filsystem-med-luks-og-ubuntu](http://thomasdamgaard.dk/blog/article/krypteret-swap-og-root-filsystem-med-luks-og-ubuntu) (note: it is written in Danish).

I heard somewhere on IRC that the new 7.04 installer should be able to do this "out of the box". 

Any help will be appreciated. :)

Note that I have been reading HOWTOs such as this one:
[http://ubuntuforums.org/showthread.php?p=2420739](http://ubuntuforums.org/showthread.php?p=2420739)

But this is not for encrypting at install time. Also it is not intended for the root filesystem -- only for storage partitions:
``This tutorial will destroy any data on the harddisk that you use. It is adviced to be very careful which harddisk you enter. Do not use it to encrypt your harddisk where you have Linux installed. The primary aim is to encrypt an additional harddisk that is used for date storage.''

---

