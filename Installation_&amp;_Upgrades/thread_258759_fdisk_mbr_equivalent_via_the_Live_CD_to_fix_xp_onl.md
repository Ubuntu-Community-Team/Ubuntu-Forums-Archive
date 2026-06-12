---
title: "fdisk /mbr equivalent via the Live CD to fix xp only system"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by Lor Boo on 2006-09-16
How can I / Can I.. boot via Live CD and wipe the MBR?

My loving win98 boot disk just gave up the ghost...
I wish to know because it's my preferred first step to Wipe a system and start over from scratch.

All my searching is finding ways to restore dual boot systems, restore grub bla bla bla...
I don't wish to restore or fix anything...clean wipe to the ground.

!Plus!
I've found a couple of times (Twice in 3 years) with win2k & xp... 
that if it (CD or 4 boot disks) cannot see partitions on a hard drive...
oddly wiping the MBR (via my win98 disk) just fixed everything?

it's a bit beyond my level of know-how why etc... C'est la vie..

Thank you much.

---

### Post by pradeepadapa on 2006-09-16
hi,
    would be more specific as to what ur mail problem is,,

whether u want to wipe the MBR of windows completely or u want to delete the GRUB nd install WIN98 on the MBR,

---

### Post by Lor Boo on 2006-09-16
I've never really been compleatly comfortable with Win2k / Winxp to erase the MBR clean (other than using 'makediskraw').

I've always been comfortable using fdisk /mbr
My win98 boot disk is down....and honestly how many more of them am I going to make. So I thought I'd learn how it can be done in linux.

Plus if i'm going to really learn linux..I should get started.
I'd really love it if I could use it (liveCD's) as a recovery tool with the windows boxes which come through here (large family all with computers and young children).

Nice if I could use it to run a virus scan...etc... 
I'm still just a dumb noob with it yet...
but not longer a complete noob! :biggrin: 



At this moment - I've got a Winxp box sitting here which is refusing to boot.  makes it about 2/3'rds way..restarts 
(safe mode/normal/last known good...all the same.  
In normal boot the winxp logo screen does comes up for 8-12 seconds).

Booted with Live CD...but really not sure what i'm to yet...
attempted to mount the drive.. got message that HDA is busy...
Not sure if via the live CD the live CD disk becomes HDA1?
or if HDA1 is still the actual  Harddisk...?

I booted via winxp cd..
it says the partition's (single partition/single HD) file system is not recognized and wants to partition.  Not able to get to the recover console.

Had an issue like this twice before with win2k... 
both times Fdisk /mbr did the trick.  
Thought I'd roll the dice and try it again until my boot disk died....
I can make another one, but instead let's have a daily lesson in linux! =D> .

If anyone has any idea's... great..
but I would like to know about the linux = for fdisk /mbr.

Thanks.

---

### Post by confused57 on 2006-09-16
You can make another Win98SE boot floppy:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

There are instructions provided in this link, I believe you have download the Win98SE oem file.

---

### Post by randell6564 on 2006-09-16
> **Lor Boo said:**
> How can I / Can I.. boot via Live CD and wipe the MBR?

My loving win98 boot disk just gave up the ghost...
I wish to know because it's my preferred first step to Wipe a system and start over from scratch.

All my searching is finding ways to restore dual boot systems, restore grub bla bla bla...
I don't wish to restore or fix anything...clean wipe to the ground.

!Plus!
I've found a couple of times (Twice in 3 years) with win2k & xp... 
that if it (CD or 4 boot disks) cannot see partitions on a hard drive...
oddly wiping the MBR (via my win98 disk) just fixed everything?

it's a bit beyond my level of know-how why etc... C'est la vie..

Thank you much.
Hi!  You can just go [here]("http://www.bootdisk.com/") and download another 98 boot disk! Go for what you know! Use it to wipe your drive!

---

### Post by Lor Boo on 2006-09-16
Tanks guy.  
I looked over the site... I see a few way to manage / edit the mbr and learned a few things there too!...

This said...
With a Win98 disk I can boot and run Fdisk /mbr.
How (can) I do this with Linux?

---

### Post by Lor Boo on 2006-09-16
> **randell6564 said:**
> Hi!  You can just go [here]("http://www.bootdisk.com/") and download another 98 boot disk! Go for what you know! Use it to wipe your drive!

Thanks randell6564.
It's starting to sound like the Linux Live CD 
is not going to be able to replace my Win98 boot disk at this time..

Any other takers?

---

### Post by cabotp on 2006-11-01
I believe this is the info your looking for

[http://www.brunolinux.com/04-The_File_System/MBR_Harddisk_layout.html]("http://www.brunolinux.com/04-The_File_System/MBR_Harddisk_layout.html")

---

