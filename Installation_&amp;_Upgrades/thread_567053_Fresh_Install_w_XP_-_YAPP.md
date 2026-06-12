---
title: "Fresh Install w/ XP - YAPP"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by ricster on 2007-10-04
( Yet Another Partition Post )

I used Partition Logic boot CD to create some partitions on my new seagate 160GB HD, 10GB for XP, 10GB for ubuntu, 1GB for swap and the rest for data.

Installed XP to first parition, no problem

Ran ubuntu liveCD and it would not see any partitions in manual parition mode.

Tracked down GParted, it too would not see the partitions. 

But XP can see all of them, even the unformatted ones. Nice.

Neither PL or GP have a "fix my partition table" button so I guess I'll just be starting over but with GP this time.

Might have had something to do with the fact that I created them all as "primary" partitions. According to what i can find in these forums you have to create an extended partition and more partitions inside that one. Sounds odd to me, why so many different partition flavours!?

Could someone explain to me what to do, already wasted two days of my life on this and dont want to mess about installing windows and resizing that partition when it seems simpler to me to just set the ones I want up in the first place.



Sorry if I sound a bit moody, just deflated after last nights efforts i guess, loving ubuntu, and the wife did not like having to use XP again for a few days so we're definitely converts!

---

### Post by ricster on 2007-10-04
Seems to be working so far, here's how I've done it

1. get the GParted Boot CD iso - burn and boot
2. Create a primary partition "formatted" as NTFS of the size you want (in my case 10000MB) 
3. Create an extended partition - this will by default be the size of the rest of the drive
4. create your ext2 partitions inside this, using 1GB + the random few MB left at the end of your drive for the linux-swap partition

My 160GB drive now looks something like this:

primary : 10000MB - ntfs
extended
{
   logical: 10000MB - ext2
   logical: 65000MB - ext2
   logical: 65000MB - ext2
   logical: 1500MB - linux-swap
}

5. click "apply", wait for it to bake and then reboot
6. boot the ubuntu live CD and begin the install process,when you get to the partition stage select "Manual" and verify that the partitions are there
7. quit out of that, reboot, this time with your XP install CD 
8. install XP on the ntfs partition
9. install ubuntu on the ext2 partition of your choice - again using the Manual partition option, it will automagically see the "linux-swap" partition, you don't have to assign it
10. install the driver from fs-driver.org to use the ext2 partitions from XP

enjoy!

(at the mo I'm at stage 8 of the above process, here's hoping the rest works out OK)

---

