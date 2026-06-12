---
title: "grub 2 software raid problem fixed?"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by cgb223 on 2009-12-11
hey guys quick question, was the lack of software raid support ever fixed for grub 2? want to upgrade, answers greatly appreciated.

ty

charlie

---

### Post by Fafler on 2009-12-12
I've been using grub with software RAID since 320 gb harddrives was the biggest ones around. What problems have you experienced?

---

### Post by demizer on 2009-12-12
I have windows 7 installed (for gaming only) on a intel software raid and when ubuntu updated the kernal images, it put grub2 onto the array. Grub2 doesn't detect windows 7 on the raid array, it doesn't even show up on the list.

---

### Post by cgb223 on 2009-12-12
grub 2 for me seemed to disregard my fake raid (last time i tried installing was with the karmic alt install disk for ubuntu) all together and failed to install after the rest sucessfully installed, base system, and all, including the disk recognizing the raid array. is this fixed? it would be nice to know. ty

---

### Post by darkod on 2009-12-12
> **cgb223 said:**
> grub 2 for me seemed to disregard my fake raid (last time i tried installing was with the karmic alt install disk for ubuntu) all together and failed to install after the rest sucessfully installed, base system, and all, including the disk recognizing the raid array. is this fixed? it would be nice to know. ty

Can this help?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Or it doesn't work for grub2?

---

### Post by cgb223 on 2009-12-13
it does not work on grub 2, ive read that link, didnt help, my question is, does Grub2 not grub 1, but Grub 2, have intel fake raid support now, last time i installed it, with my fake raid working fine, (did it via synaptic package manager) it screwed it up and although dmraid was setup like it should be and everything was installed like it should minus grub 2 (seeing as it didnt work) i then could not boot in to my OS. this was 1 month ago, does it still have this problem???

---

### Post by darkod on 2009-12-13
> **cgb223 said:**
> it does not work on grub 2, ive read that link, didnt help, my question is, does Grub2 not grub 1, but Grub 2, have intel fake raid support now, last time i installed it, with my fake raid working fine, (did it via synaptic package manager) it screwed it up and although dmraid was setup like it should be and everything was installed like it should minus grub 2 (seeing as it didnt work) i then could not boot in to my OS. this was 1 month ago, does it still have this problem???

I'm far from an expert for raid, but I'm reading a lot about it since I want to make raid0 to check how much it will speed up hdd transfer. So first of all, you need it to work on software raid or fakeraid? Because you used both terms here and I believe although motheboard onboard fakeraid is usually softraid in essence, the term software raid is used when ubuntu is creating the raid.
Anyway, did you try with small /boot partition outside the array? I've seen articles that there is a way to install grub on both fakeraid and softraid but in both cases a /boot partition outside the array seems to remove the headaches.

---

### Post by realzippy on 2009-12-13
...confirm that software RAID runs fine with seperate /boot.Grub *and* Grub2.

---

### Post by quequotion on 2009-12-14
> **realzippy said:**
> ...confirm that software RAID runs fine with seperate /boot.Grub *and* Grub2.

Could you clarify this?

Do you mean
1. the grub and grub2 packages
2. actual files "/boot.Grub" and "/boot.Grub2"
3. two distinct /boot directories
4. two distinct /boot directories on two distinct partitions

Also, are you saying that both are required?

---

### Post by darkod on 2009-12-14
> **quequotion said:**
> Could you clarify this?

Do you mean
1. the grub and grub2 packages
2. actual files "/boot.Grub" and "/boot.Grub2"
3. two distinct /boot directories
4. two distinct /boot directories on two distinct partitions

Also, are you saying that both are required?

I will take the liberty to reply. I assume what was meant is that both grub1 and grub2 work with separate /boot partition outside the array. It's up to you if you want to create the same size /boot partition on the other drive too, especially if creating raid1 array. There are even ways to make the /boot partition and grub sync from disk1 to disk2 to be like real raid1 where if one disk fails the other keeps working, and your system. If you have /boot on disk1 only, and it fails, there goes your booting capability. But I'm not an expert and don't know how to sync them (yet). :)

---

### Post by phillw on 2009-12-14
> If you have /boot on disk1 only, and it fails, there goes your booting capability. From my dim and distant memory of RAID, actually booting from a RAID array, via RAID with a borked drive was done differently to data RAID. The boot RAID was done as a mirrored stripe, so one of the drives could fail, as opposed to the redundancy checking to allow a drive in a data RAID to die & a new one be re-built with the extra information stored on the other drives.

But, that **was** then - mebbie they've gotten around it.

You used to need to set the system up with two different types of RAID - one for mirroring / striping and one for general data protection.

One of these days, I'll get my-self upto date with the RAID options, but I don't think normal MotherBoards & BIOS support both types of RAID at the same time.

I am going back *some* years ... we were running UNIX - lol

If someone could tell me that I'm wrong in my knowledge of using the two types of RAID system for boot & data - I'd be happy for you to do so.

Regards,

Phill.

---

### Post by darkod on 2009-12-14
> **phillw said:**
> From my dim and distant memory of RAID, actually booting from a RAID array, via RAID with a borked drive was not possible. The boot RAID was done as a mirrored stripe, so one of the drives could fail, as opposed to the redundancy checking to allow a drive in a data RAID to die & a new one be re-built with the extra information stored on the other drives.

But, that **was** then - mebbie they've gotten around it.

You used to need to set the system up with two different types of RAID - one for mirroring / striping and one for general data protection.

One of these days, I'll get my-self upto date with the RAID options, but I don't think normal MotherBoards & BIOS support both types of RAID at the same time.

I am going back *some* years ... we were running UNIX - lol

If someone could tell me that I'm wrong in my knowledge of using the two types of RAID system for boot & data - I'd be happy for you to do so.

Regards,

Phill.

It all depends. Back when I was IT in London, on our Dell servers with proper hardware raid, I was using 2 drives in RAID1 for the OS, 3 drives in RAID5 for data. Now I'm talking from home user point of view.
And yes, most ordinary mobo bios raid will allow you either raid0 (no protection from failure) or raid1 (protection but having only half capacity available, one drive from two for example).
I think there are some mobos with 0+1 but not sure. And I guess you need minimum of 4 drives for that too. Two will be like raid0 and then mirrored. A bit too much for ordinary home setup.

---

### Post by phillw on 2009-12-14
> **darkod said:**
> It all depends. Back when I was IT in London, on our Dell servers with proper hardware raid, I was using 2 drives in RAID1 for the OS, 3 drives in RAID5 for data. Now I'm talking from home user point of view.
And yes, most ordinary mobo bios raid will allow you either raid0 (no protection from failure) or raid1 (protection but having only half capacity available, one drive from two for example).
I think there are some mobos with 0+1 but not sure. And I guess you need minimum of 4 drives for that too. Two will be like raid0 and then mirrored. A bit too much for ordinary home setup.

Yeah, it's why I posted the thread onto 10.04 - people do seem to be having issues with raid at the moment - I'm also recalling things as they were. 2 machines - collectively called ccs, one was called ccs1 and the other ccs2. ccs1 was in charge and would send a 'heart-beat' to ccs2. If ccs2 failed to receive a heart-beat' for greater than 60 seconds It would take over the data RAID array & 'take charge' automatically.

The root drives were internally mirrored on each machine, the data array was plugged into the both of them.

also, I'm still not 100% sure why people are running down the RAID route - It looks pretty on the box, but unless you are running a server environment that needs 24/7 up time ... It's a case of ..... WHY? - what's wrong with a decent backup schedule. RAID was brought out when hard drives used to die regularly ... Things have moved on ... the I in RAID is a lot lower than it was - but the drives have far, far more hours of MTBF.

My idea of RAID ? -- Get the disk unit and rsync to it - lol

Phill.

---

### Post by darkod on 2009-12-14
> **phillw said:**
> Yeah, it's why I posted the thread onto 10.04 - people do seem to be having issues with raid at the moment - I'm also recalling things as they were. 2 machines - collectively called ccs, one was called ccs1 and the other ccs2. ccs1 was in charge and would send a 'heart-beat' to ccs2. If ccs2 failed to receive a heart-beat' for greater than 60 seconds It would take over the data RAID array & 'take charge' automatically.

The root drives were internally mirrored on each machine, the data array was plugged into the both of them.

also, I'm still not 100% sure why people are running down the RAID route - It looks pretty on the box, but unless you are running a server environment that needs 24/7 up time ... It's a case of ..... WHY? - what's wrong with a decent backup schedule. RAID was brought out when hard drives used to die regularly ... Things have moved on ... the I in RAID is a lot lower than it was - but the drives have far, far more hours of MTBF.

My idea of RAID ? -- Get the disk unit and rsync to it - lol

Phill.

Well personally, from enthusiast point of view, I want to compare raid0 disk transfer speed with a single drive. Not planning raid1 for home setup, I agree regular backup is enough. And probably I'll have to use softraid because with the prices these days I'll probably buy 500GB hdd and I have 250GB now. If I use the mobo fakeraid the second half of the 500GB can't be used, to the best of my knowledge. :) Softraid would allow me to use the full disk.
As soon as I buy the new drive, I'll try fakeraid first, to confirm if the rest of the drive will remain usable. If not, softraid is next in line. :)

---

### Post by cgb223 on 2009-12-15
Wow just listening to these nostalgic comments is pretty cool. I'm just starting my jouney into the world of computing, (off to college next year for comp sci/ software engineering degree. 

So does this mean that grub 2 does not work yet?  phillw said he posted a 10.04 note on that. Does this mean that the fix will most likely come out in 10.04? And lastly does the seperate out of raid /boot partition work? And how do I do that? 

Thanks, 
Charlie

---

### Post by darkod on 2009-12-15
> **cgb223 said:**
> Wow just listening to these nostalgic comments is pretty cool. I'm just starting my jouney into the world of computing, (off to college next year for comp sci/ software engineering degree. 

So does this mean that grub 2 does not work yet?  phillw said he posted a 10.04 note on that. Does this mean that the fix will most likely come out in 10.04? And lastly does the seperate out of raid /boot partition work? And how do I do that? 

Thanks, 
Charlie

With /boot partition out of the raid array, it definitely works. For other options I don't know, waiting to buy my new hdd to check (but that will be after the holidays).
Lets say you have two 250GB drives and you want to use raid0 for faster performance.
First on disk1 create 200MB partition to be used as /boot partition. Then for example create 20GB partition for /, 6GB for swap and the rest for /home.
To make it identical, on disk2 also create the same scheme, but the 200MB partition will not get used (at least not for raid0). It's different task if you want to mirror the /boot from disk1 to the partition on disk2 also.
When creating the softraid during the install process, you will just specify the identical /, swap and /home partitions to be used as raid0 (not /boot). And that's it, in general terms.
There are reports and tutorials that it should work even without separate /boot, but this is the most straight forward way.

PS. Something on the subject:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by AlexanderDGreat on 2010-05-08
Hi I'm using Adaptec HostRaid U320 and 2 Cheetah Seagate 37gb for my /boot swap and / plus 1 tb seagate for my /home.

I noticed, if I use the Adaptec Hardware to create a raid0 or raid1 - Lucid won't let me install, I forgot the error message, so I just used software raid on both my hard disks.

Grub2 works fine, however, sometimes it complains, it cannot mount the /boot partition, yes I have it separate, but I just restart and it's ok again, weird, any ideas why?

Here's mine: /boot swap / /home

---

