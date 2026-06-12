---
title: "Can I dualboot in a SSD with intel RST"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by evoka0 on 2012-12-04
Hi,

I'm building a pc, and want to know if this can be done:

Using a 1tb hd, half for windows half for linux, and using intel RST in a 120gb SSD, in which I use the max 64gb for the RST, and the rest for linux, either using the remaining space as a partition for installing, or even better using it for caching the linux hd partition. 

I found [http://tobestool.net/using-intels-rst-with-linux/](http://tobestool.net/using-intels-rst-with-linux/) but that only address the second option, and the author doesn't recommends it.

---

### Post by oldfred on 2012-12-04
With SSD's falling in price, I am not sure that Intel's SRT will be a good choice in the near future. Better just to have one or even two SSDs with the full install on the SSD. Then use rotating drive as data storage which does not gain from caching. 

It seems a lot of laptops are using Intel SRT. That may be to save $ on RAM and still improve performance and with limited space you do not have room for multiple drives.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    

---

### Post by evoka0 on 2012-12-04
olfred,

Thank you for your response, I'm looking into the links. One of the reasons I'm trying to use the caching/RST is that I can't afford a bigger SSD that could fit windows and the games that use a lot of space.

---

