---
title: "formating [appears to be] stuck at 33%"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by mastablasta on 2015-06-08
formating [appears to be] stuck at 33%
so i need to reinstall the OS after the previous USB drive died. and i am having major problem doing it for some reason or another. here is the setup:
1. install media USB flash drive (tried a few of them, and used a few of USB installers/burners)
2. system drive - USB flash - brand new (i have 2 to choose from 8 GB or 16 GB - both seem to have the same issue)
3. data drives - 2TB software RAID 1 HDD array - it holds 2 GB /swap, 2 GB /var/log, the rest of the space was mounted as /data

Problem 1 - burning server image to USB via unebootin or linuxliveusb gives a success, however when i boot from the created image the "check the disk for defects" fails usually at the same file. the md5sum 
of downloaded image (via bitttorrent) is good. i then moved to linux desktop and created an image using startup disk creator. this time all most is good but some pxe file is reported as "may be corrupted". 
ok so i continue with install anyway. the mini.iso (net installer) did not report any issue, but same issue appears when doing install as with supposedly corrupted image.

Problem 2 - during install installer picks up the previous raid parittions, so i tell it to just format the 8 GB flash drive with ext4 and set it up as / . it proceeds and says it will format /swap on raid 
and / on USB. format then goes underway, but it stuck at 33 %. i left it for 30 minutes at which point since there was no progress i tried to turn off the PC. the off button didn't work, so i unplugged the 
electricity. 

i tried again. same thing it got stuck at 33%, so this time i dropped to terminal and checked df -h and sure enough the system disk is not yet formatted. this time i rebooted via command line (reboot 
command).

i asked on IRC and it appears this is a known bug - when installer sees another system it prompts if you are sure to reformat, but the prompt is not visible but in backgroung so it is stuck at 33%. the 
advice was to dd some zeroes to system disk and see if that will help it progress (since there will be no file system on it, no question should be triggered). if this is a known bug i couldn't help but 
wander how it got into an LTS and how come it is not yet resolved since most disk come preformated (usually NTFS). anyway on we go, but this time it said it can not mount the cd-rom media (i.e. install 
USB). i've checked the media on another PC and it looked ok. all files can be read just fine. and yes the zeroes were written on correct USB disk (where the system would go).

i boot and tried again. only this time i checked the install disk for errors again it keep saying it can not mount it. well how are you boting from it and all if you can not mount it? duh? another bug it 
seems. also it goes into a loop. it goes something like - i can not mount the cd rom, should i retry? NO. attempting to mount, unable to mount cd rom, should i retry? NO. attempting to mount, unable to 
mount cd rom, should i retry? NO. attempting to mount, unable to mount cd rom, should i retry? YES. attempting to mount, unable to mount cd rom, should i retry? endless loop. this looks like a bug to me. 
i couldn't get back to the boot menu.
 
questions:
1. if i preformat the USB drive into EXT4 will i get arround the 33% freeze? 
2. should i destroy the raid array and setup a new one?
3. how do i see actual formatting progress? i can't believe ubuntu installer can't handle this. i mean MS-DOS could show percentage of formated disk space 30 years ago.
4. if i install the OS on another PC (only /) would the raid and other partitions be picked up

Anyone knows the solution to all this?

plenty of forums threads and other "solutions" on internet. mostly for old versions of the OS. and mostly had to do with bad disk. which i dont' think it's the case here since USB drives are brand and different models.

---

### Post by Habitual on 2015-06-08
I think you should use ext4 as the partition type during a reformat.
USBs tend to come in 2 flavors of System "Requirements" - Windows and MacOS.
I always nuke the supplied partition and go ext4 for all my USBs.
Never had an issue.

---

### Post by mastablasta on 2015-06-09
I did go ext 4 and it gets stuck at formatting. that is the whole issue here.

also, USB is Linux compatible (i.e. specifically stated by manufacturer that it supports Linux from kernel 2.6 onwards).

---

### Post by mastablasta on 2015-06-11
I found some similar case with old Debian: [http://unix.stackexchange.com/questions/46060/debian-stucks-at-formatting-33](http://unix.stackexchange.com/questions/46060/debian-stucks-at-formatting-33)

this all looks very much like a bug to me. and perhaps best solution would be to install OS without swap on system disk, take out the raid and then add it later (in some way). would that be possible?

I am still having hard time getting through the fact that the images of the OS I had appear to be rubbish. - at the same time newly created images show md5sum as ok bt fail on disk test, no matter what prog I used to create them.

UPDATE: issue is definitelly not with USB disk. i did read & write test and it had no errors.

---

### Post by mastablasta on 2015-06-12
solved by preformating the system disk to ext 4 and then selecting "do not format". installer continued at the usual fast speed afterwards. new problem though - i think i may have missed a step. another thread....

---

