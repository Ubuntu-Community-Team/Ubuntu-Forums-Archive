---
title: "Help with Partition setup"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by theone964 on 2011-12-02
Hello, I've been using 10.04 for a while now on a Dell and my sister just gave me a Sony (quad core :D). Well I wanted to keep Win7 but also do a dual boot of Ubuntu. I've done this before and it's very easy. I wanted to do a complete reinstall of Win7 to a much small partition first (wipe her old data and any viruses, etc). I set it up and installed 10.04 on a small partition also, the idea being two small OS partitions (Win7 and Ubuntu 10.04) and then a large EXT4 partition. This way my data would be separate from any OS and with EXT2Read installed on Win7 i could still access my data from Win7 and still keep it protected from viruses. 

However i later realized that there would be 4 partitions, the extra one being the Win7 system recovery partition, which i definitely want to keep. This presents no problems but when i fired up gparted i got:

/dev/sda1  ntfs                 Recovery                       10GB
/dev/sda2  ntfs                 System Reserved          100MB   boot
/dev/sda3  ntfs                                                      40GB           =====Win7
/dev/sda4  extended                                              20GB
/dev/sda5  ext4           /                                         19GB
/dev/sda6  linux-swap                                              1GB
unallocated                                                          220GB

As you can see i ended up with 4 primary partitions which now means that i cant have any more partitions and gparted points that out also.

My question is Do i really need sda2 or can i just delete the partition? I cant seem to recall having it on any other dual boot I've had but since i have no other PC's available to me i have no way of checking.

If anyone nows how to solve this situation I would be really thankful

---

### Post by darkod on 2011-12-02
1. If you use the Recovery partition to reinstall Win7 I am not sure you can select the destination size. Most of these partitions are designed to set up the computer as it was from factory, with the original partitioning scheme.

2. You can't simply delete /dev/sda2 because win7 has two of the boot files on it, and can't boot without them. That's another ridiculous thing MS did starting from Win7, two boot files go onto that System Reserved partition, not visible in Computer so most people are not even aware of it. And when they later delete it, win7 stops working.

If you install from win7 dvd you can avoid having this partition this way:
Boot with the ubuntu cd in live mode first (even if you still haven't installed ubuntu).
With Gparted create one ntfs partition with the size you want for win7.
During the win7 install when it asks just select this partition to install to. In that case the System Reserved is not created.

If you are using the windows partitioner during the install, you specify the partition size you want to create, but it creates the small one too.

3. You can still make it work with the System Reserved too. In that case your shared data partition will have to be logical, inside the extended. Both ubuntu and windows don't mind this.

---

