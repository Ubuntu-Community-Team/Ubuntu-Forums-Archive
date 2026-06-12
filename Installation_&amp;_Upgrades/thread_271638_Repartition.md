---
title: "Repartition"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by TheFlamingBush on 2006-10-05
Ok so ive been using Ubuntu for a week now, and im solidly impressed. Not just with the distro, but also the community, who seem to be both onto it, and helpful in every matter ive raised so far.

Here's my dillema though, i set aside 8 gigs in my major Unix partition, and a 14 gig (fat32) partition for swapping and sharing stuff between my Linux (ex3) and my XP on my primary partition (nfts). I have since discovered that the 8 gigs was conservitive, and want to extend that out. I downloaded Gparted, and resizing my two other partitions is no problem at all, although i have only resized the Fat32 for now, leaving a sector of 3.5 gigs free to add to my Linux primary partition. I have an extra Partition as well, which has an extended and a logical partition, adding up to 4.5 gigs, but ive left that mostly unused as it appears that most of the apps ive been downloading seem to be installed on the Primary linux partition...

I wanted to add a serious graphical game, NWN, to test out the enviroment for gaming, with my ATI card, but the entire install is going to take about 3.5 gigs, and i dont want to use all my space up, so wanted to add the extra 3.5 that i have trimmed of the Fat32 share partition.....problem is i cant unmount the Linux partition with Gparted whilest being in Ubuntu, and i wondered how i was going to add the 3.5 gigs i have free now to the 8 gigs i already have in the Linux primary partition. 

Any suggestions?

---

### Post by K.Mandla on 2006-10-05
There's a [GPartEd live CD]("http://gparted.sourceforge.net/livecd.php") that sounds like it might be perfect for what you want. I've used it a number of times, and it's saved my bacon even more times than that.

But remember to back everything up, because there's always the chance things will get seriously messed up. ;)

---

### Post by TheFlamingBush on 2006-10-05
yep i have backed up my data on the fat32 partition and popped a copy of it on the nfts partition.

I saw the Gparted livecd, but wondered if there was another way.....either through the live distro, repartitioning tool or somehow running it in the recovery mode and running Gparted from there and adding the free space to the main ext3 8 gig partition. I was a bit worried that running the Gparted from the live cd might interfere with the data on the (ext3)linux and (NFTS) xp partitions!....which would be tragic!

all i want to do is add the 3.5 gig i now have free to the 8 gig on the main Linux partition wthout losing data!....:-/

any chance?.....i guess i just burn the iso of the Gparted livecd and start it from boot after changing the boot protocols to CD/DVD?

---

### Post by TheFlamingBush on 2006-10-05
ok any idea what program i use to burn an ISO image onto CD?

I had a look at K3b and gnomebaker but neither seem to do this. Gnomebaker does burn a dvd ISO image, but i only have cd's!.....oh wait it does burn ISO's onto cd, i just didnt look under tools! 

DOH!

---

### Post by TheFlamingBush on 2006-10-05
> **TheFlamingBush said:**
> ok any idea what program i use to burn an ISO image onto CD?

I had a look at K3b and gnomebaker but neither seem to do this. Gnomebaker does burn a dvd ISO image, but i only have cd's!.....oh wait it does burn ISO's onto cd, i just didnt look under tools! 

DOH!



Well damn....i tried burning the iso onto a cd, but it just failed.....i must bedoing something wrong, any other suggestions?

---

### Post by Pjotr123 on 2006-10-05
I use K3b for all that stuff. K3b even does an MD5checksum check automatically, which is very cool. 

I rather dislike Gnomebaker; it looks like a Russian car model of the seventies, compared to the modern Mercedes Benz look of K3b.

Modus operandi for K3b: open K3b, point it at the ISO (click it) and just go with the flow.

Greeting, Pjotr.

---

### Post by Herman on 2006-10-05
Whenever I want to write an .iso file to a CD or DVD in Ubuntu, I just right-click on the .iso file and click 'write to disk'.
That has always worked for me. :D
I prefer to  use CD-RW disks for software, and you do not even need to erase the CD-RWs first. IF the software senses any data on the CD-RW it will ask you if you want to try another disk or erase this one.
For data CDs I just use the standard issue CD/DVD Creator, ('Places'-->'CD/DVD Creator'.)

I highly recommend GParted LiveCD, and you will find that it is very easy to use, you won't even need to worry about mounting or umounting. it's automatic.
The latest versions of GParted have 'move' support for Linux filesystem type partitions now too, which is really handy. :D

Regards, Herman :D

---

### Post by TheFlamingBush on 2006-10-05
> **Herman said:**
> Whenever I want to write an .iso file to a CD or DVD in Ubuntu, I just right-click on the .iso file and click 'write to disk'.
That has always worked for me. :D
I prefer to  use CD-RW disks for software, and you do not even need to erase the CD-RWs first. IF the software senses any data on the CD-RW it will ask you if you want to try another disk or erase this one.
For data CDs I just use the standard issue CD/DVD Creator, ('Places'-->'CD/DVD Creator'.)

I highly recommend GParted LiveCD, and you will find that it is very easy to use, you won't even need to worry about mounting or umounting. it's automatic.
The latest versions of GParted have 'move' support for Linux filesystem type partitions now too, which is really handy. :D

Regards, Herman :D

Thanks...but i just reinstalled from scratch in the end.

---

### Post by ingo on 2007-02-19
well, you probably partitioned your drive a little better this time, but in case the need arises again have a look at the first link of my signature :)

---

