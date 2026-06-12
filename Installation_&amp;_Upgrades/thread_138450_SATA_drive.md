---
title: "SATA drive"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by DragonRidr on 2006-03-01
okay i will bet this has been asked before and if so please point me to the thread and i will read the awnsers on there. other wise here is my question.

i bought a new SATA 250gig drive over the weekend becuse my 60 gig drive was getting full. i have figured out how to do the winxp install to get the SATA drive to be the boot drive and still leave a 9 gig ide drive in my pc for file storage for access from both xp and ubantu. my question is where do i find the drivers for the SATA drive when not used in a raid configureation. i figured i would partition the drive into 3 partitions. one for xp one for ubantu and one for storage besides the 9 gig ide drive.

there are drivers on the install cd for the mother board that i think are ment for lunix but am not sure wich one to use as all i could find was referances to redhat and suse but not ubantu.

was going to use a grub boot floppy to get it to dual boot and then burn a bootable cd once i have it set and working right so that i can boot from the cd rather then the floppy drive.

sorry if i ran on and will apprecate any and all help and i will for sure listen better then i did last time i asked as i got lol kind caught with pants down on a hardware problem i was almost sure was software.

thanks anyone that helps :)
DragonRidr

---

### Post by o_fortuna on 2006-03-01
[QUOTE=DragonRidr]okay i will bet this has been asked before and if so please point me to the thread and i will read the awnsers on there. other wise here is my question.

i bought a new SATA 250gig drive over the weekend becuse my 60 gig drive was getting full. i have figured out how to do the winxp install to get the SATA drive to be the boot drive and still leave a 9 gig ide drive in my pc for file storage for access from both xp and ubantu. my question is where do i find the drivers for the SATA drive when not used in a raid configureation. i figured i would partition the drive into 3 partitions. one for xp one for ubantu and one for storage besides the 9 gig ide drive.

there are drivers on the install cd for the mother board that i think are ment for lunix but am not sure wich one to use as all i could find was referances to redhat and suse but not ubantu.

was going to use a grub boot floppy to get it to dual boot and then burn a bootable cd once i have it set and working right so that i can boot from the cd rather then the floppy drive.

sorry if i ran on and will apprecate any and all help and i will for sure listen better then i did last time i asked as i got lol kind caught with pants down on a hardware problem i was almost sure was software.

thanks anyone that helps :)
DragonRidr[/QUOTE]
Ubuntu supported my SATA drive right out of the box -- no driver installation needed. Just go to System--Administration-->Disks and make sure it's there. Then, there are guides in the wiki for mounting drives, like [this one]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29#head-80128df9c1c4215d74e3f016b5cd2c2352da247c").

---

### Post by Coelocanth on 2006-03-02
I don't think you'll need to install any drivers unless you're planning on a RAID setup (depending on your motherboard). If your mobo natively supports SATA drives, you should be fine. I installed Ubuntu as a dual boot with Win XP on my SATA hdd, and had no problems with it at all. Ubuntu jumped on it like it belonged there! :lol:

---

### Post by DragonRidr on 2006-03-03
thanks for the help and info i will respond once i know how things went wich wont be this weekend too much going on and no time to play on pc. again thanks for the help

---

### Post by DragonRidr on 2006-04-02
Hellllllllllllllllllp seam i didnt do enough reading or i messed something up for sure.
i finaly had the time and mind i thought to get ubantu installed today so i started the install. i had finaly got the sata drive in and yes probly wrong order but i installed windows XP first i also formated the 250 gig drive into 3 partations. the first with winxp on it the 2cd and 3rd i set for fat 32 i also still have my 10 gig ide drive.

when i started the install and it got to the partationer part i decided to set the ubantu partation to ext3 since that is what i saw most useing instead of fat32. i also set the 10 gig drive as the swap drive. 

the trouble is that when i told it to write the info to the disks and procced i get an error msg that i have no clue on.

the msg is ....... no root file system defined

in the proccess of trying to get past that i cant boot winxp normaly. luckly i had looked at useing gag to boot the partations and so had put it on a bootable disk and added windows too it. that is the only reason i got on here. 

i am sure it must have unset winxp partation as bootable. i am totaly lost as to what i need to do to get past the msg. any and all help will be greatly apprecated. thanks ahead of time

---

### Post by DragonRidr on 2006-04-02
quick update i got windows to boot not but going back thru the install and setting that partation to bootable.

still have same msg. i found something about setting the mount point to / for the partation lunix is going on but to me it seamed to be saying set the who drive to that. i wasnt sure so i didnt do that. 

least one problem solved. 

will be waiting to hear . thanks for your time

---

