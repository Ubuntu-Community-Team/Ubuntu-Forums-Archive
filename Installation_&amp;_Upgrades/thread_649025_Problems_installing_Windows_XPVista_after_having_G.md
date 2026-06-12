---
title: "Problems installing Windows XP/Vista after having Gutsy Installed"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by chimera007 on 2007-12-24
Thank you for reading this post.

Let's jump straight to the problem. I have a 120GB HDD, 3 partitions. I installed windows xp on the first, vista on the second, gutsy gibbons amd64 on the third. 

For some weird reason, windows xp failed to load up after i had installed rubbish software. Vista started acting up by just reading hdd, like if it were a virus scanner, never stopped. 

As I want usable Operative Systems, I tried reinstalling Windows XP. I thought it would be just reinstalling xp and fixing up GRUB afterwards. Well, to my surprise Windows XP didn't want to install, half way after it is installing, some c0000005 error is being spit out. I checked the cd out, it was good, the test was to copy paste all the files onto the hdd. Still doesn't explain why does the vista dvd not work. When trying to install Vista, there is a part where you actually copy the data into the disk and then expand it. Coping surprisingly lasts only 3 seconds. Then when extracting it complains about not having all the files copied to the drive. 

You might all say it is just the disks that have gone to sleep with the fishes. I have to disagree with that. Disks work perfectly on a system where linux isn't installed. I don't want to take out ubuntu just because XP is on that time of the month.

Is there any known issues in installing windows xp/vista after ubuntu has been installed on one of the partitions prior to windows?

If so 

By the way, there is some times when Win XP, never loads the setup, it sits on a black screen with I/O HDD light being lit all the time. 

To solve all these problems, even though it is out of the range of this post, could anyone tell me if it is possible to install WinXP on a 6 GB and then use ubuntu to make an image of that partition and to be able to overwrite anything on that partition with the freshly installed windows xp image? What if I repartition the drive and try to "burn" that image into a bigger partition? 

Or even better, if it is possible to install windows on a virtual machine, and then make an image of that installation and then "burn" that image into a real partition on the computer's HDD?


Thanks for your time.

---

### Post by chimera007 on 2007-12-24
Ah, forgot the hardware i have.

Motherboard is:   Asus M2N32-SLI Delux
Processor is:       AMD Athlon 64 6000+ X2 3.0GHz
HDD is:              Western Digital 160GB WDC WD1600AAJS-0 
Gfx card is:        XFX GeForce 7600 GT 256MB
Ram is:              2GB dual channel sli ready memory ( don't have the brand name in my brain right now, sowwy :) )

---

### Post by chimera007 on 2007-12-24
I actually got windows xp to install. 

To skip all these problems in the future, what could be wiser to do:

Option 1) dd if=/dev/(partitionname) of=/home/chimera/winxpimg bs=1024k

And then if i need to put back to original state, just reverse the process. For Ex: dd if=/home/chimera/winxpimg of=/dev/(partitionname) bs=1024k

Option 2) Mount the partition, and gzip it. That would make it so that when i past it back it is all the same.

Any opinions? Suggestions would be great!

---

