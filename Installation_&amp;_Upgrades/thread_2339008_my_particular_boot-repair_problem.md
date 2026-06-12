---
title: "my particular boot-repair problem"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by d.coli on 2016-10-03
Hi,

I'm dual booting Windows 10 and Ubuntu 16.04 LTS. It worked the first time I used it, and I ran Ubuntu successfully while Windows was in hibernate. However, after visiting Windows once, Ubuntu stopped booting. I was getting a kernel-panic VFS unable to mount message, so I used boot-repair from a live Ubuntu USB key. This is the result: [http://paste2.org/gtesfG2C](http://paste2.org/gtesfG2C).

---

### Post by oldfred on 2016-10-03
You have an UEFI system.
But it looks like you left Windows fast start up on which is always on hibernation.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Is system UEFI have drives in RAID or Intel SRT mode? 
You show /dev/mapper which is RAID or LVM in Linux.

And is then sdb a small SSD used by Windows/Intel SRT just for the hibernation?

       
 [http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by d.coli on 2016-10-04
Thanks. Yes, it is set up with RAID 0 across a 32GB miniSSD drive and a 1TB drive. The SSD acts as cache for Rapid Storage Technology. Unfortunately I wasn't able to get Rapid Start working on this machine because it was set up with too small of an SSD. 

I turned "acceleration" for the 1TB drive off in the Rapid Storage controls. Must I also unRAID the two drives? As I said, Rapid Start has been disabled for a while now.

Just saw your link about turning of the faster restart in windows which uses hibernation. Trying that now.

---

### Post by oldfred on 2016-10-04
With older systems, some users that did not use Windows much turned off the Intel RAID, removed RAID meta-data from drives, and installed / (root) to SSD to make Ubuntu fast.
Windows only uses SSD for booting, so does not help Windows a lot. (unless newer versions use it for more than start up hibernation).

Some that only had 8GB or less of RAM and 32GB SSD found Windows was only using the size of RAM in SSD, so kept start up cache of 8GB and used 20GB for / having both faster start in Windows and fast all the time Ubuntu.

These now are all older threads.
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

