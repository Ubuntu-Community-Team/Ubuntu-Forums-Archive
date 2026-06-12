---
title: "new 8.04 hardy install using remastered dvd"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by projserve on 2008-08-04
Proline computer with 2 ide drives, 80Gb and 120 Gb, windows and linux, attempt to change distros from Suse 10.2 to Ubuntu 8.04. So the machine has had linux installed and functional before. I remastered a dvd that includes edubuntu, quasar accounting, etc on my hp pavilion laptop. I attempted to install using the live dvd as well as a direct install from the dvd, but both sustained problems with drive geometry the moment it wanted to set up the partitions for install. After 24 hours and various changes, including burning the dvd at 6X, I still struggled to get to the partioning. After a bit of persistence, retrying the option, it eventually gave me the partitions, with a lot of strange reporting. However, the drives where defined correctly under sdX. I chose the manual option and asked under advance to install grub on the sda, not hd0 it had by default (prior install failed using that option). The install followed to about 80%, and after installing language options (with skip option) it reverted to live cd (with no user intervention).

Under the live dvd it sees the drives not as ide by SCSI drives, as sda and sdb.

I have researched about bios on the mboard which is a MSI N1996. Someone said it is actually a hp board. I changed bios settings a number of times. Then I tried ubuntu install cd - it went through the install, getting to partitioning, and read all the drives fine. 

In trying to do a grub install manually the error message was "sda1 does not have any corresponding BIOS drive.

The install problem then, in my mind, has to do with the difference between the remastered dvd which has upgrades as new as 2008/8/3 and the original ubuntu 8.04 cd release.

Kernel - 2.6.24-16-generic and 19-generic
Any assistance will be appreciated. I can install using ubuntu and edubuntu cds, and get all the apps again, but that is the whole point of remastering - to cut that out.

---

### Post by projserve on 2008-08-05
Will go ahead and do a ubuntu standard install - but still will be interested to know if there is someone out there with answers!

---

