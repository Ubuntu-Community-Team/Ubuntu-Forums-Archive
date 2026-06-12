---
title: "attach existing raid 1 array to a new Linux install"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by prioryjim on 2012-12-12
I tried to post this yesterday and was sure it had gone in. But couldn't find it later ??

Anyway to repeat.
I set up as Ubuntu 12.10 64 bit on a small 160G drive.
I have two 1T drives and set them up as raid 1 /dev/md0
The OS seemed to change this to /dev/md127
But it all seems to work OK , I mount it and copied all my "Star Trek videos" to it. All is OK.
I shut down clean.

For one reason or another I want to re-install Ubuntu 12.10 clean.
How can I re-attach the raid array, hopefully without loosing any data ??

Thanks Jim

---

### Post by ttguy on 2012-12-12
So is root (/) on your 160G drive? IE is the non raid drive the one you plan on re-installing linux on?

Because if so - you should be golden. 

You should just be able to re-install and then mount your raid drive as normal.

I have had problems when I had /home on my raid drive if the raid drive does not come up after an upgrade then the machine will not boot because it can't find home.

But if you are not using your raid drive as /home and just mounting it somewhere then this should not be a problem

mdadm is your friend here
eg this will give you info about the state of your array

sudo mdadm --misc -D /dev/md127

If the raid does not start might have to install dmraid and mdadm  using synaptic

this command can put together an array that did not start too
 mdadm --assemble --scan

---

### Post by prioryjim on 2012-12-13
Thanks
Yes the two 1T drives are totally dedicated to the raid.
The 160G is not raid and will be a plain old Linux drive.

Regards
Jim

---

### Post by darkod on 2012-12-13
As mentioned, you can attach it later, or you can also do it during the installation. The live session doesn't recognize mdadm so in order to do this you will need to install the package and assemble the array first in live session, and then start the install with the Install icon on the desktop:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

During the install use the manual partitioning, and after setting up / and swap (also separate /home if you use it) on the single disk, also set up /dev/md0 with the mount point you select for it (you can simply enter a new mount point, it will be created). Make sure you DO NOT tick the format box when setting up the mount point and filesystem for /dev/md0. Also, the filesystem will have to be the same as currently used of course.

---

### Post by prioryjim on 2012-12-14
OK will have a go.
Thanks
Jim

---

### Post by prioryjim on 2013-01-07
Final solution was 
New 160G disk formatted as 80G Vista/2G Linux Swap/78G Linux FS
Installed Vista and the Ununtu 12.10, it now dual boots into Ubuntu by default.
Installed mdadm in Ubuntu.
Shut down, reconnected my two 1T disks that were previously configured as a Raid 1 mirror.

Ran up Unbuntu and didn't have to do anything. It detected my 1T raid disks and configure /dev/md127.
I manually mounted /dev/md127 and there were my files.
Added an entry to /etc/fstab, rebooted and the raid was mounted on boot.

Also install Serviio, which now serves up my media from the 1T raid.
Thanks
Jim

---

