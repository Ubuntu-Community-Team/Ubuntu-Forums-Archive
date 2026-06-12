---
title: "dual boot imac 350mhz macos9"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by mnnence on 2006-12-21
Hi all,
I am trying to dual boot a 350mhz imac and I install macos with 2 partitions, then after confirming macos is fine, i install ubuntu and it does something where my macos is not installed by yaboot, mac disk first aid does not see the partitions, and notrons disk doctor 6 sees them but gives a driver error and cannot mount the partitions .nortons still sees the names of the partitions i created, but cannot mount. I believe i correctly tried to mount the mac partition in ubuntu and it showed nothing. I would really like to be able to get this dual booting macos 9 and ubuntu. i am installing mac 9.2 and ubuntu 6.10. what could ubuntu be doing , i believe during the partitioning, that can corrupt ? the hdd from properly mounting / loading the disk driver.I have tried reloading multiple times, with different partition schemes. i am using hfs+ . Thanks in advance!

---

### Post by tagra123 on 2006-12-22
> **mnnence said:**
> Hi all,
I am trying to dual boot a 350mhz imac and I install macos with 2 partitions, then after confirming macos is fine, i install ubuntu and it does something where my macos is not installed by yaboot, mac disk first aid does not see the partitions, and notrons disk doctor 6 sees them but gives a driver error and cannot mount the partitions .nortons still sees the names of the partitions i created, but cannot mount. I believe i correctly tried to mount the mac partition in ubuntu and it showed nothing. I would really like to be able to get this dual booting macos 9 and ubuntu. i am installing mac 9.2 and ubuntu 6.10. what could ubuntu be doing , i believe during the partitioning, that can corrupt ? the hdd from properly mounting / loading the disk driver.I have tried reloading multiple times, with different partition schemes. i am using hfs+ . Thanks in advance!

I had a tough time getting it to install correctly. I have OSX.

I reinstalled OSX -- made a backup.

Then I installed dapper - selected manually partition and resized the OSK partition to 1/2 of what it was. Saved it. Then kepted using the go back option to get to the part where it ask you to partition your disk. This time I select use free space.  

On my installation I had to use expert mode on an ibook but the procedure is the same. Perhaps you can use the install - live disk in expert mode and select the Install yaboot option again.  You migh have to go through the find cdrom and cd sections, bu skip the install sections.

Yaboot should find both OS during the install.

---

### Post by mnnence on 2006-12-22
last night i tried expert install from 6.10 and i skipped yaboot, and a couple other minor things, and when i rebooted i hit option key and it only showed macos , which is fine since i played with the installer, but the mac os wouldnt boot. so it must be the partitioner messing things up,. im going to try dapper now, maybe something changed in edgy, but i do believe its the partitioner thats doing the damage, cause the 1st time i got my hands on this mac i got to the partitioner area, without even doing the installer, and it messed up the partition. so maybe i have to get those partitions setup using a different program, i believe this uses -parted-. are there any other partition apps for os9 or boable from cd that i can use to setup the linux partitions so then i can just have ubuntu choose those partitions instead of it playing with the partitions

---

### Post by tagra123 on 2006-12-22
> **mnnence said:**
> last night i tried expert install from 6.10 and i skipped yaboot, and a couple other minor things, and when i rebooted i hit option key and it only showed macos , which is fine since i played with the installer, but the mac os wouldnt boot. so it must be the partitioner messing things up,. im going to try dapper now, maybe something changed in edgy, but i do believe its the partitioner thats doing the damage, cause the 1st time i got my hands on this mac i got to the partitioner area, without even doing the installer, and it messed up the partition. so maybe i have to get those partitions setup using a different program, i believe this uses -parted-. are there any other partition apps for os9 or boable from cd that i can use to setup the linux partitions so then i can just have ubuntu choose those partitions instead of it playing with the partitions

If you are doing a fresh install of os9X  just partition the hadr drive before installing. Most of the MAC disks allow this. THen install osx, then dapper.  

I'm going to put together a how to later on to show how to install while making a backup along the way.

---

### Post by mnnence on 2006-12-23
Ok here are some updates. when i boot from mac 9.2 and format the hdd with 2 partitions , then install macos thats fine. then i boot off edgy 6.10 and install by deleting the partition i left for edgy and reformatting as boot/swap and /root it appears to wipe out the mac os 9 driver on the os9 partition or something on the drive. i tried everything and nothing could fix it. then i did the same thing with dapper 6.06 and it did not wipe out os9 disk driver, so i had dual boot,cccccccccccccc, but dapper i couldnt get to load gnome or x windows, like it never installed it during the load. buit i did have it dual booting. so i figured ok, ill install edgy over dapper, and not repartition, so all i did was reformat swap and root partitions, leaving the boot partition alone, but it still wiped out booting mac9. so i tried playing with parted and mac-fdisk, and they were useless, then i booted off an os10.2 disk, and it just locked up, so i booted off the 10.1 disk, nothing . then i booted off the 9.2 disk again, and reinstalled the disk driver, , in the menu where u mount the drive ( which i could never do ) , then i disk first aid the partition that was hfs messed up, and installed 9.2 and viola. dual boot, but not quite yet.i rebooted, and i got no operating system . so i held option key and was able to boot os9 , then i rebooted and held option and chose linux and it booted. so now i can dual boot with the option key, but that doesnt make me happy. im gonna work with yaboot i think thatll fix it, looks like a bug in edgy causes something on the hdd partition info to be wiped out. dapper does not have this issue, so it looks like an edgy bug. when i get more info ill post it as a bug. ps i get a mac hd error right now, but disk first aid thinks all is ok, its not a hardware error

---

