---
title: "Some 10.04 to 12.04 upgrade questions"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2012-05-30
If running 10.04LTS, I see that it is been recommended to wait until the first point release expected in July 2012. Is that the same as 12.04.1 for which I've seen a release date of 23rd August 2012? Which date is correct for the first point release? Is first point release the same as 12.04.1?

One desktop here runs 32bit 10.04LTS, ext3 and 2gb of ram. I migrated the hard drive last year from a single core CPU to dual core. Are there any foreseeable problems using Update Manager to upgrade to 12.04? I'll keep 32bit and ext3 with 12.04, correct?

I understand a future a fresh install to 64bit seems unavoidable if I'm sticking with Ubuntu beyond 12.04, because support for 32bit will then cease?

---

### Post by dino99 on 2012-05-30
32 bits is correct on such hardware, and 12.04 is supported till 2017, so many hardware/software will be changed before 12.04 ended.

I'm not an update-manager fan, feel to buggy to me, and i prefer synaptic. Changing "lucid" by "precise" inside the sources.list is my way to dist-upgrade (after disabling the third parties like ppa)

---

### Post by lukeiamyourfather on 2012-05-30
First thing is try a live session of 12.04 from a USB flash drive or a CD/DVD to see if all of the hardware works as expected. If that works that's good but upgrading is never certain, only way to know for sure is to try it. I always do a clean install as upgrading in the past has always led to problems (some minor and some major).

Cloning the disk with something like Clonezilla before an upgrade can be handy in case the upgrade doesn't work and you still need the machine to function. Waiting until a point release doesn't make a difference in my opinion. The point releases are just cumulative updates and bug fixes that get applied to the installation media instead of being downloaded after an install. Given the choice between 32-bit and 64-bit, I'd take 64-bit if the hardware supports it.

---

### Post by mikewhatever on 2012-05-30
> **Handssolow said:**
> If running 10.04LTS, I see that it is been recommended to wait until the first point release expected in July 2012. Is that the same as 12.04.1 for which I've seen a release date of 23rd August 2012? Which date is correct for the first point release? Is first point release the same as 12.04.1?

The first point release is not the same as..., it is 12.04.1. The date may change, so keep an eye on the release schedule.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

> One desktop here runs 32bit 10.04LTS, ext3 and 2gb of ram. I migrated the hard drive last year from a single core CPU to dual core. Are there any foreseeable problems using Update Manager to upgrade to 12.04? I'll keep 32bit and ext3 with 12.04, correct?
You've lost me with that migration.;)

> I understand a future a fresh install to 64bit seems unavoidable if I'm sticking with Ubuntu beyond 12.04, because support for 32bit will then cease?

Support for 32bit architecture will continue, but you'll be using a PAE kernel. It's also not a bad idea to stay with Precise for the next five years.

---

### Post by Handssolow on 2012-05-30
mikewhatever, perhaps my use of the term migrate might be misleading. I swapped a hard drive from the old PC and moved it to a newer one with different hardware and being Ubuntu it coped. As it's been a much upgraded Ubuntu with 32bit and ext3 etc. I wondered If I'd have any problems moving to 12.04.

Incidentally, I only recently learnt of the issue I'll have with my old Pentium M based laptop when 12.04 expires. As it's non-pae compatible I'll eventually have to abandon Ubuntu after 12.04 or do I jump ship now.

---

### Post by lukeiamyourfather on 2012-05-30
> **Handssolow said:**
> 
Incidentally, I only recently learnt of the issue I'll have with my old Pentium M based laptop when 12.04 expires. As it's non-pae compatible I'll eventually have to abandon Ubuntu after 12.04 or do I jump ship now.

I personally would look at upgrading to a notebook with a 64-bit processor (or at least PAE capable) and ditch the old laptop rather than ditching the Linux distribution. That's not everyone's bag and I get that. There are other distributions that will continue non-PAE 32-bit support for a while like Debian. Jumping ship now rather than later would give you a chance to get used to another distribution before you have no other options. On the other hand if you like Ubuntu you might as well use it until you can't.

If you look at newer notebooks consider even low end models will run circles around the Pentium M notebooks so it wouldn't take a huge investment to be able to run the latest 64-bit version of Ubuntu.

---

### Post by kansasnoob on 2012-05-30
> **dino99 said:**
> 32 bits is correct on such hardware, and 12.04 is supported till 2017, so many hardware/software will be changed before 12.04 ended.

I'm not an update-manager fan, feel to buggy to me, and i prefer synaptic. Changing "lucid" by "precise" inside the sources.list is my way to dist-upgrade (after disabling the third parties like ppa)

I wish you wouldn't tell people things like:

> Changing "lucid" by "precise" inside the sources.list is my way to dist-upgrade (after disabling the third parties like ppa)

It's much better to follow the proper upgrade procedure because it tries to look for problems, automatically disables PPA's, removes things that will not work with the upgraded OS, etc :)

It's not perfect but it's better than trying to manually upgrade by editing software sources ........... really!!!

---

### Post by kansasnoob on 2012-05-30
> **Handssolow said:**
> If running 10.04LTS, I see that it is been recommended to wait until the first point release expected in July 2012. Is that the same as 12.04.1 for which I've seen a release date of 23rd August 2012? Which date is correct for the first point release? Is first point release the same as 12.04.1?

One desktop here runs 32bit 10.04LTS, ext3 and 2gb of ram. I migrated the hard drive last year from a single core CPU to dual core. Are there any foreseeable problems using Update Manager to upgrade to 12.04? I'll keep 32bit and ext3 with 12.04, correct?

I understand a future a fresh install to 64bit seems unavoidable if I'm sticking with Ubuntu beyond 12.04, because support for 32bit will then cease?

You actually seem to have a pretty good handle on this :D

Please do wait until 12.04.1 is released!

Then before upgrading get a 12.04.1 live CD, either by downloading and burning one or buying one, and run the live environment a little bit to get the general "feel".

Going from 10.04 to 12.04 will be a bit of a shock because the desktop environment has changed to Unity. I like it, but not everyone does, so I started this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Above all just be patient :)

And regarding your Pentium M laptop Ubuntu Precise will give you another five years:

[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

---

### Post by mikewhatever on 2012-05-31
I wonder if anyone will be supporting those non-PAE CPUs in 2017. Read Hat, dropped support already, and Ubuntu will have in 5 years time. Perhaps Debian, by for how long?

---

### Post by mastablasta on 2012-05-31
probably slitaz, puppy, tiny core and the like will still support it. they still support 486 i believe... :-)

---

### Post by lukeiamyourfather on 2012-05-31
> **mikewhatever said:**
> I wonder if anyone will be supporting those non-PAE CPUs in 2017. Read Hat, dropped support already, and Ubuntu will have in 5 years time. Perhaps Debian, by for how long?

Old hardware gets phased out for good reason. :-({|=

---

