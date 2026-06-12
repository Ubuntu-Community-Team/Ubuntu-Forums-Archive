---
title: "Thinkpad X6 Ultrabay CD-RW/DVD not working"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mikio on 2009-03-25
dear forum,

i have searched the forums and the internet for hours now and found some hints but no solutions.

the title says it all. it is a second hand Ultrabase X6 docking station with a CD-RW/DVD Ultrabay media drive. when i insert a audio cd, a data cd or a dvd the drive starts spinning but nothing ever shows up.

i looked at my logs and i can not find any related messages. i am beginning to think that that something is wrong with either the media drive or some part of the docking station that is running it (connector, something on the board,..)

also: i tried booting with a bootable cd, but the media drive is not listed as an option on startup :(

the questions that i have: 

i am not 100% sure that it is broken because i seem to remember (?) that i have disabled the media drive support when i got the laptop (since it does not have a media drive). i have since updated ubuntu twice (8.4 -> 8.10 -> 9.4) and i am now thinking that on the way the media drive configuration might have gotten lost/messed up.

if that was the case, i would possible need to manually enable/install the modules driving media drives ? 

would anyone know how to do this? after hours, i was not able to figure it out myself..

many thanks,
miki

lsscsi (gives only my harddisk):
[0:0:0:0]    disk    ATA      WDC WD3200BEKT-0 11.0  /dev/sda

lshw -C disk (again, gives only my harddisk):
  *-disk                  
       description: ATA Disk
       product: WDC WD3200BEKT-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WXE708PT9016
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00036131

ls  /dev/sd* :
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5

ls  /dev/h* :
/dev/hpet

ls  /dev/sr* : ( ThinkWiki says that it should be /dev/sr0)
ls: cannot access /dev/sr*: No such file or directory

---

