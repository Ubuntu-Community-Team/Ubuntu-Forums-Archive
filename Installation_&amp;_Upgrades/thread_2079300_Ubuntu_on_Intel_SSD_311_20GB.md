---
title: "Ubuntu on Intel SSD 311 20GB"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by bloodychaos on 2012-11-01
I've been using Ubuntu for a couple of years and I've decided to do a fresh install. Before I start, I'm using the following motherboard, that is a Gigabyte GA-z68xp-UD3-ISSD that comes with Intel SSD 311 20GB.

My previous Ubuntu installation was on a HDD ( '/' and '/home' in different partitions) and dual boot with Windows 7 that uses the Intel SSD 311 20GB as the cache volume. I've decided to erase Windows altogether and install Ubuntu and would like "/" to be on the Intel SSD 311 20GB drive while the '/home' drive on another HDD. I'd like to inquire the following.

1. Is 20GB more than enough for "/"? From my measly understanding and Googling, 20GB seems to be more than enough for /, updates and softwares.
2. Are there special requirements needed for installation to the SSD? If there are, may I know what are they.
3. Do I need to set anything in fstab for the SSD? I'm pretty much a noob when it comes to SSD since I've been using HDD for years
4. Is this SSD more than sufficient to run Ubuntu?

I tried searching the forums and Google for them but I wasn't able to find info on this particular SSD. Most links point towards questions that ask how to use the mentioned SSD as a cache volume in linux instead. I haven't tried experimenting yet since I'd like to get more information before making the final move.

Thanks in advance.

---

### Post by dannyboy79 on 2012-11-01
> **bloodychaos said:**
> I've been using Ubuntu for a couple of years and I've decided to do a fresh install. Before I start, I'm using the following motherboard, that is a Gigabyte GA-z68xp-UD3-ISSD that comes with Intel SSD 311 20GB.

My previous Ubuntu installation was on a HDD ( '/' and '/home' in different partitions) and dual boot with Windows 7 that uses the Intel SSD 311 20GB as the cache volume. I've decided to erase Windows altogether and install Ubuntu and would like "/" to be on the Intel SSD 311 20GB drive while the '/home' drive on another HDD. I'd like to inquire the following.

1. Is 20GB more than enough for "/"? From my measly understanding and Googling, 20GB seems to be more than enough for /, updates and softwares..
YEs, 20GB is enough for / IF you have another drive for /home and you store most large files in your /home folder
> **bloodychaos said:**
> 
2. Are there special requirements needed for installation to the SSD? If there are, may I know what are they.
No special requirements

> **bloodychaos said:**
> 
3. Do I need to set anything in fstab for the SSD? I'm pretty much a noob when it comes to SSD since I've been using HDD for years..
again, no special requirements
> **bloodychaos said:**
> 
4. Is this SSD more than sufficient to run Ubuntu?.
yes

---

### Post by bloodychaos on 2012-11-01
> **dannyboy79 said:**
> YEs, 20GB is enough for / IF you have another drive for /home and you store most large files in your /home folder

No special requirements


again, no special requirements

yes

Thanks for the swift reply! Now I can get on with the installation during the weekends once I finished with the backups.

---

### Post by oldfred on 2012-11-01
I normally install in 25GB and actually use about 9GB including /home. But all data except .wine is in partitions on my rotating drive. And my .wine is 1.5GB of Windows version of Picasa. And my /home is a total of 2GB including the .wine or my / is really 7GB with lots of applications.

Some examples of users with portable/laptops with the Intel SRT which is like what you have.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

If it is or was configured as RAID you may have to remove the RAID settings.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

And now most think SSD life is not much different than HDD life. But you can reduce some writes.
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)


These were the settings I did:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center, ot just have swap on rotating drive to have some.
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

SSD Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,discard,errors=remount-ro 0       1

---

### Post by bloodychaos on 2012-11-02
> **oldfred said:**
> I normally install in 25GB and actually use about 9GB including /home. But all data except .wine is in partitions on my rotating drive. And my .wine is 1.5GB of Windows version of Picasa. And my /home is a total of 2GB including the .wine or my / is really 7GB with lots of applications.

Some examples of users with portable/laptops with the Intel SRT which is like what you have.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

If it is or was configured as RAID you may have to remove the RAID settings.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

And now most think SSD life is not much different than HDD life. But you can reduce some writes.
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)


These were the settings I did:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center, ot just have swap on rotating drive to have some.
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

SSD Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,discard,errors=remount-ro 0       1

Hmm, this is quite useful! Thanks for the added info.

---

