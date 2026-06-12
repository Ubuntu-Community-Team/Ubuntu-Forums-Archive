---
title: "Update Issue (Not Enough Disk Space in Boot?)"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by troycopes on 2016-07-17
Hello all!

I just recently got back into using Ubuntu on my laptop. I love how it has gotten easier than it was 10 years ago!

This afternoon, I went to update via the Software Updater and I got an error I have never seen before...
[IMG]http://i.imgur.com/OQdLuGW.png[/IMG]
I performed sudo apt-get clean, but it did not resolve the issue. 

I checked my hard drive, and I have almost 300 gigs free... not sure what to do.

Any advice?

Thanks!

---

### Post by oldfred on 2016-07-17
Did you install with full drive encryption, which uses LVM and a separate /boot partition?
Or did you create a separate /boot partition (not recommended unless required like with full drive encryption).

What version did you install. Age old issues with LVM installs as new UEFI systems download several copies of kernel and user must regularly houseclean.
With 16.04 they now automatically only keep two kernel versions, so not an issue anymore.

       /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

---

### Post by &amp;KyT$0P# on 2016-07-17
Your system uses a separate partition on /boot (what you're calling your "hard drive" is actually just the primary system partition).  What is taking up that space is previous kernel versions.  Every version of the kernel is installed separately, on my system each version consist of 4 packages:
```
linux-headers-<version>-generic
linux-headers-<version>
linux-image-<version>-generic
linux-image-extra-<version>-generic
```
So the fix is to [FONT=Courier New]sudo apt-get purge[/FONT] the old kernel versions you no longer need.

Check your running kernel:
```
uname -a
```

Check installed kernel-related packages:
```
dpkg-query -W -f '${binary:Package}\n' | grep -P '^linux'
```
(Note that not all of these listed packages are old kernels - some of them are just "meta-packages" for the latest kernel.  Look specifically at those packages explicitly including a version in the name, and be careful not to delete too much or you won't have a usable system.)

EDIT Oops, posting at the same time as oldfred...

---

### Post by troycopes on 2016-07-17
Thank you all for the quick reply!

OldFred:
I installed Ubuntu 14.04 LTS and I did enable full disk encryption at set up. Not sure what type.

Halogen2:
I typed in those commands and the results are below;

[https://uncommongeek.files.wordpress.com/2016/07/screenshot-from-2016-07-17-164148.png](https://uncommongeek.files.wordpress.com/2016/07/screenshot-from-2016-07-17-164148.png)
[https://uncommongeek.files.wordpress.com/2016/07/screenshot-from-2016-07-17-164226.png](https://uncommongeek.files.wordpress.com/2016/07/screenshot-from-2016-07-17-164226.png)

---

### Post by &amp;KyT$0P# on 2016-07-17
Assuming nothing special about any of the old kernels on your system, here's your fix:
```
sudo apt-get purge linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic linux-headers-4.2.0-34 linux-headers-4.2.0-34-generic linux-image-4.2.0-27-generic linux-image-4.2.0-34-generic linux-image-extra-4.2.0-27-generic linux-image-extra-4.2.0-34-generic
```
It should NOT ask to remove any additional packages, so if it does please post that here in case I might have typed it wrong 8-[

---

### Post by wildmanne39 on 2016-07-17
Please use thumbnails or url's for images.
Thanks

---

### Post by grahammechanical on 2016-07-18
In 14.04 this command will remove one kernel each time it is run and leave the two latest kernels.

```
sudo apt-get autoremove
```

Or, at the Grub  boot menu select Advanced options for Ubuntu and select a kernel with recovery mode. At the recovery menu select Clean - Try to make free space. That action will run both the clean command and the autoremove command.

Regards.

---

### Post by troycopes on 2016-07-18
HaloGen:
That command worked! Thank you so very much!

Grahmmechanical:
Is that something I would need to run after every update? Or would it be best if I upgrade to 16.4 LTS?

---

### Post by &amp;KyT$0P# on 2016-07-18
> **troycopes said:**
> HaloGen:
That command worked! Thank you so very much!
You're welcome!  :KS

> Is that something I would need to run after every update? Or would it be best if I upgrade to 16.4 LTS?
I wouldn't rely on commands like [FONT=Courier New]apt-get --purge autoremove[/FONT] to deal with this.  I've only ever seen old kernels be auto-removable on one 14.04 system.  For example the 14.04 machine I'm posting from right now has a total of 4 kernels atm, and it's had at least 6 before, and none are auto-removable.

Given that you're explicitly prompted before any action is taken, manual removal is the least error-prone way to go about it.

As far as upgrading to 16.04 LTS, that won't help you here unless during the process you adjust the size of your /boot partition to better suit the approximate number of old kernels you want to keep... but, changing the size of /boot doesn't require upgrading to 16.04 LTS. :P

---

### Post by asearle on 2017-01-15
Dear Halogen2,

It's a real shame that you don't recommend "autoremove" as the solution.

I have this problem with several friends for whom I installed ubuntu with (unfortunately) a fixed-size boot partition and now they all pester me ever time their boot sector is full.  (Arrrggghhh!)

And, also, autoremove didn't seem to work for me: I tried installing (```
sudo apt-get autoremove
```) but all it did was create Gzip-archives for the visible kernels and also for several which I had deleted manually. Then as the bootsector became full the process (understandably) crashed due to insufficient disk space.  (Arrrggghhh!)

If I could find a way to have the old kernels automatically removed then there would be 6 very happy Ubuntu users ... i.e. all my friends who are experiencing this problem and therefore think that I am an idiot and that Ubuntu is bad.  (Arrrggghhh!)

Anyway, I hope that someone out there can help me?

Regards,
Alan

---

