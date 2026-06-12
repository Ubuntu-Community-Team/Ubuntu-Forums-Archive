---
title: "Windows Partition Unknown MBR messed up"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by masaharustin on 2011-11-17
I was trying to install Kubuntu earlier with a live usb. I installed it on an ext4 partition in an extended partition. The install said it was done but the computer could not find an operating system upon reboot. I booted to the kubuntu desktop on the live usb and tried to erase the whole extended partition and merge it with the windows partition and then have kubuntu automatically resize it for me upon reinstalling.

Long story short, the partition manager stopped responding and now my windows partition is unknown.

Help please, I love linux but windows (right now) is a necessity.

Thanks,
masaharustin

---

### Post by jjex22 on 2011-11-17
sounds like the first thing to do is find out what the current partition map is - load up the live cd and run gparted. 

This should show you how the partition map is looking. It may also be worth seeing if you can mount the windows partition at this time.

If you don't have a back up of your windows partition that's gotta be the next step - if possible use the windows cd to fix boot problems and back up. in the unlikely event that this doesn't resolve the issue - you should then be able to use the kubuntu live cd to access the windows partition and copy your files to an external drive.

if you did make a backup before trying to install, or you've managed to make one now, try again with kubuntu - check the md5 sum of the kubutnu you downloaded, and re-copy to the usb stick; you could have had a bad copy. If you get any problems again then let us know!

Edit: are you trying to install ubuntu to a usb HDD? this can cause the 11.10/11.04 installer to crash out and may have effected the windows mbr.

---

### Post by masaharustin on 2011-11-17
Thanks for the reply!

I don't have any backups of the partition. I've booted the cd I used to install windows and it was unable to repair. I also tried something called ntfsfix in ubuntu (didn't work). Is my last option to recover my data and reinstall windows?

Thanks,
masaharustin


EDIT: It looks like the former windows partition is not mounting. How do I mount it so I can back up my files?

Also, partition manager says there are 0 MBs taken, or its 100% free...

---

### Post by jjex22 on 2011-11-17
Afraid so, if the windows cd can't fix it, (ntfsfix is more for filesystem error checking and repair) then it's a reinstall job - can the ubuntu live cd open the windows partition? If so it'll make it a lot easier as you can litterally just copy your users folder out and leave it to run, depending on devices involved and size over night, you can also recover some programs  that use launchers - such as world of warcraft if you use it by just copying it from program files - always worth googling any programs you have on there that are a pain to reinstall as there are sometimes ways to save them!

---

### Post by darkod on 2011-11-17
You can try to scan the HDD and recover the old state with testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

But be careful, it's a powerful tool. Also ask some friend for help if you can, if you are not sure you can do it yourself.

This is a good lesson for the future, don't try too many resize operations at the same time, the risk is higher. Also, it doesn't make any sense to enlarge the windows partition just so you can shrink it for the next ubuntu install.

You should have simply used the manual partitioning method when installing the second time and that's it. It works much better. Don't be afraid to manually install, the automatic procedures can often mess it up more, depending on the situation. As you saw...

---

### Post by masaharustin on 2011-11-17
> **darkod said:**
> You can try to scan the HDD and recover the old state with testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

But be careful, it's a powerful tool. Also ask some friend for help if you can, if you are not sure you can do it yourself.

This is a good lesson for the future, don't try too many resize operations at the same time, the risk is higher. Also, it doesn't make any sense to enlarge the windows partition just so you can shrink it for the next ubuntu install.

You should have simply used the manual partitioning method when installing the second time and that's it. It works much better. Don't be afraid to manually install, the automatic procedures can often mess it up more, depending on the situation. As you saw...

Thanks, at this point there isn't much to lose so I'll try testdisk. At first I tried a manual install, it didn't work for some reason. Because of this I tried an automatic install and thats where the problems started. Lesson learned, don't mess around with partitions too much.

masaharustin

---

