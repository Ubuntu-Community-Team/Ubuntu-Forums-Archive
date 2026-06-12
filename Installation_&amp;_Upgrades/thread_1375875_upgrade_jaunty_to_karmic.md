---
title: "upgrade jaunty to karmic"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by aslinda on 2010-01-08
Hi guys :D

I'm a newbie to ubuntu and I only used ubuntu less than a month, and I really like it.  I would like very much to upgrade my ubuntu jaunty to ubuntu karmic but I have several concerns.  If I choose to upgrade via update manager:

1.  Will I lose my compilers and configurations?  For example, some of my programs in current ubuntu are using gcc 4.3 and g++-4.3.  I know that Karmic uses higher version of gcc and g++ and I have installed these programs in higher version of gcc and g++ and I got some problems.  I would very much like to stay with my current compilers and configurations.  I mean, do have to install all these previous version of compilers when I upgrade to Karmic?

2.  What about my data in my home folder? Will it be erased?

3.  What about my data in programs such as firefox?  Will it too be erased?

4.  What will happen to all third party software if I upgraded to Karmic?

I really hope anyone could give my a reply.  I don't want to lose all my configurations and data because of the upgrade.

Thanks again

Aslinda
Newfoundland

---

### Post by recluce on 2010-01-08
> **aslinda said:**
> Hi guys :D

I'm a newbie to ubuntu and I only used ubuntu less than a month, and I really like it.  I would like very much to upgrade my ubuntu jaunty to ubuntu karmic but I have several concerns.  If I choose to upgrade via update manager:

1.  Will I lose my compilers and configurations?  For example, some of my programs in current ubuntu are using gcc 4.3 and g++-4.3.  I know that Karmic uses higher version of gcc and g++ and I have installed these programs in higher version of gcc and g++ and I got some problems.  I would very much like to stay with my current compilers and configurations.  I mean, do have to install all these previous version of compilers when I upgrade to Karmic?

2.  What about my data in my home folder? Will it be erased?

3.  What about my data in programs such as firefox?  Will it too be erased?

4.  What will happen to all third party software if I upgraded to Karmic?

I really hope anyone could give my a reply.  I don't want to lose all my configurations and data because of the upgrade.

Thanks again

Aslinda
Newfoundland

First off, after installing/updating Karmic on several computers, I personally will not update from Jaunty to Karmic at all. I will rather wait for Lucid, Karmic just hast to many issues in my opinion.

If you need to move to Karmic, here my suggestion #1:

**Backup _everything_, before you even think of touching that upgrade button.** If you use Clonezilla, you can easily restore your working Jaunty system if you don't like the results of the upgrade process.

Second, be aware that the upgrade from Jaunty to Karmic has a tendency to fail on machines that have seen substantial modification of the "clean" Jaunty install.

As to your questions, as far as I can answer them.

1.) See what the distribution upgrade tells you about packages to remove/add/update. You can see that information before you commit to any changes. In theory, the upgrade should not overwrite packages that are newer than the ones in the upgrade package.

2./3.) Also in theory, the data in your home folder (this includes browser settings) should not be modified or erased by the upgrade. Configuration settings depend on the individual applications, most should me retained. However, your upgrade may fail. A new installation usually wipes your home folder, unless it is on a separate partition, in which case it should be fine. Did I mention that you need a **backup** before you start? ;)  

4.) That depends. Many packages will be upgraded with everything else, some will remain untouched, some will be disabled. Again, the distribution upgrade should give you that information before you commit to the the upgrade. In any case, while making your **backups** use Synaptic package manager to export your list of installed packages, save in a secure place. If you need to do a fresh install, you can "batch-reinstall" from that list (be sure to edit it before you reinstall, to remove outdated kernels and other junk no longer needed - it is plain text).

5.) Good Luck!

---

### Post by Bartender on 2010-01-08
I agree with recluce.  I've installed Karmic on a test PC, but sticking with Jaunty on the two PC's that count, and will wait til 10.4's been out a few months before considering a re-install.  I prefer to wipe the / partition clean and install, not upgrade.

Do you have a separate /home partition?  If so, there are three things that you have to do.

One, you've got to use the manual install option, and be sure to mount /, swap, and /home to the same partitions as before.

Two, make sure to tell the installer to _NOT_ format the /home partition.

Three, use the same username/password as before, or else you'll end up with two /homes.

---

### Post by aslinda on 2010-01-08
Thanks guys for your valuable insights :KS.  I think I'm going with recluce on this and wait for Lucid release.  Besides, my Jaunty is working perfectly fine at this moment, and I don't want to spend too much time installing and tweaking Karmic if anything goes wrong during the process.

Thanks again, I really appreciate it

---

### Post by Rob Maddison on 2010-01-09
Many thanks from me too. I'm fairly new to Ubuntu/Linux and was thinking of the upgrade. I actually found the thread when looking for advice on upgrading with a seperate /home, which I got fromt his thread too.

The advice here has persuaded me to hold off until April. Thanks :-)

---

### Post by slakkie on 2010-01-09
You can backup/restore your disk in under 30 minutes. So why download and burn the clonezilla livecd. Backup your data, upgrade, see how it works.. If you don't like it, restore the backup and you're running jaunty again.

---

### Post by recluce on 2010-01-10
> **slakkie said:**
> You can backup/restore your disk in under 30 minutes. So why download and burn the clonezilla livecd. Backup your data, upgrade, see how it works.. If you don't like it, restore the backup and you're running jaunty again.

Absolutely right - and I wrote that in my post as well. Rule #1: always have a backup! Still, my personal preference is to skip Karmic. Among the problems that convinced me: 

1.) Upgrading a system that has seen many additional packages installed failed miserably on more than one occasion. In some cases, the distribution upgrade just freezes at some point and leaves a totally broken "half Jaunty" "half Karmic" system.

2.) ATI drivers in Karmic are broken, causing issues like the "black screen of death" on resume after suspend. (Fix is to port the Jaunty drivers into Karmic).

3.) Harddisk SMART monitor is broken, warning of failing drives for **all** Samsung HDs.

4.) EXT4 issues with large file corruption are not totally laid to rest. Very touchy subject for me, file system reliability and integrity is a fundamental requirement for me and should not even have the shadow of doubt.

5.) GRUB2 causes suspend/hibernate issues on some systems.

6.) boot from degraded RAID reported broken (this I did not test)

All this and more tells me that Karmic was not sufficiently tested before release. Also, blatantly obvious problems like 2.) and 3.) have not been fixed to this day, which is not a good sign for ongoing product support. I hope and trust that Lucid, being an LTS release, will solve these problems instead of adding new features at break-neck speed.

Since for me personally, Karmic added nothing important but slightly faster boot speed, I decided to skip this release. I realize that there are valid reasons to upgrade (better SSD support, adding support for newer hardware and such), but I wanted to add a word of caution that, if you don't have any need to upgrade, Karmic might well be the version to skip. As always, YMMV.

---

### Post by slakkie on 2010-01-11
> **recluce said:**
> Absolutely right - and I wrote that in my post as well. Rule #1: always have a backup! Still, my personal preference is to skip Karmic. Among the problems that convinced me: 

1.) Upgrading a system that has seen many additional packages installed failed miserably on more than one occasion. In some cases, the distribution upgrade just freezes at some point and leaves a totally broken "half Jaunty" "half Karmic" system.


I cannot say I have the same experience. Since I was a Karmic tester I have upgraded my box many times from both 8.04 and 9.04 to 9.10. And all went fine.

> 
2.) ATI drivers in Karmic are broken, causing issues like the "black screen of death" on resume after suspend. (Fix is to port the Jaunty drivers into Karmic).


I'm not an ATI user, so will not comment on this. But if ATI is indeed buggy it might be a reason not to upgrade. 

> 
3.) Harddisk SMART monitor is broken, warning of failing drives for **all** Samsung HDs.


That is most probably due to libatasmart? I know there were problems with it: [https://bugs.launchpad.net/bugs/387161](https://bugs.launchpad.net/bugs/387161), [https://bugzilla.redhat.com/show_bug.cgi?id=515881](https://bugzilla.redhat.com/show_bug.cgi?id=515881)

> 
4.) EXT4 issues with large file corruption are not totally laid to rest. Very touchy subject for me, file system reliability and integrity is a fundamental requirement for me and should not even have the shadow of doubt.


This is a kernel thing, and you can still decide to use ext3 (Jaunty is the first Ubuntu OS to support ext4). No-one is forcing you to ext4. This in itself has nothing to do with Karmic or Ubuntu. The kernel supports it, so Ubuntu does too. Maybe the pick as default FS is wrong, but if no-one uses it, the product cannot mature. I understand the move to ext4.

> 
5.) GRUB2 causes suspend/hibernate issues on some systems.
6.) boot from degraded RAID reported broken (this I did not test)


Unaware of these issues.

> 
All this and more tells me that Karmic was not sufficiently tested before release. Also, blatantly obvious problems like 2.) and 3.) have not been fixed to this day, which is not a good sign for ongoing product support. I hope and trust that Lucid, being an LTS release, will solve these problems instead of adding new features at break-neck speed.


As a Karmic tester I feel that you are wrong. I know I've tested:
* Upgrades
* libatasmart
* software center
* KDE
* etc

> 
Since for me personally, Karmic added nothing important but slightly faster boot speed, I decided to skip this release. I realize that there are valid reasons to upgrade (better SSD support, adding support for newer hardware and such), but I wanted to add a word of caution that, if you don't have any need to upgrade, Karmic might well be the version to skip. As always, YMMV.

Luckely Ubuntu supports 4 releases at any given point, so pick one you like and stay with that one. Upgrades are not needed to have a running Ubuntu box. But when you don't run LTS you need to upgrade eventually but you can wait at least 18 months before doing so.

---

### Post by recluce on 2010-01-11
> **slakkie said:**
>  
(as to the problem with updates from 9.04 to 9.10 freezing)
 I cannot say I have the same experience. Since I was a Karmic tester I have upgraded my box many times from both 8.04 and 9.04 to 9.10. And all went fine.

I have tried about a dozen upgrades so far. Some of production machines (always with backups), some of Jaunty test installations. I had three freezes / failures, all on machines that have seen many package installs. If you search the forum, I don't seem to be alone.

> 
(as to the problem of "no resume ater suspend")
I'm not an ATI user, so will not comment on this. But if ATI is indeed buggy it might be a reason not to upgrade. 


Fair enough. If it would be the only problem in Karmic, I could live with the workaround, which I posted here: [http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

> 
(as to basically all Samsung HDs being reported failing)
That is most probably due to libatasmart? I know there were problems with it: [https://bugs.launchpad.net/bugs/387161](https://bugs.launchpad.net/bugs/387161), [https://bugzilla.redhat.com/show_bug.cgi?id=515881](https://bugzilla.redhat.com/show_bug.cgi?id=515881)


I do not know for sure where the problem lies. Smartmontools tends to work better, as it has options for Samsung HDs. It seems that most recent Samsung drives have switched the byte order of the raw parameters, which causes Ubuntu to think that there are millions of "Pending Sectors", even though the normalized results (the single byte values counting down from 100 or 253) are normal.

In any case, you can find many reports from irritated people that believe that their drives are failing - or who even replaced perfectly healthy drives.

> 
(as to EXT4 large file corruption)
This is a kernel thing, and you can still decide to use ext3 (Jaunty is the first Ubuntu OS to support ext4). No-one is forcing you to ext4. This in itself has nothing to do with Karmic or Ubuntu. The kernel supports it, so Ubuntu does too. Maybe the pick as default FS is wrong, but if no-one uses it, the product cannot mature. I understand the move to ext4.


I understand that it is a kernel problem, but I would agree that the move to EXT4 as default was premature and should have been removed from the downloadable Live CD as soon as the problem became apparent.

I am all for testing - and I am running a test install of Lucid Alpha right now - but please not with Joe User's important data.

> 
(as to Grub 2 issues with hibernate/suspend)
(as to boot problems with degraded RAID)

Unaware of these issues.


Grub 2 problem seems only to hit on certain machines. I had one notebook where removing Grub 2 and installing Legacy Grub solved a Hibernate issue. There are other reports, but data is sparse, I give you that.

Degraded RAID: as I said, I did not test that one, as I never boot off a RAID system, but use a separate boot device

> 

As a Karmic tester I feel that you are wrong. I know I've tested:

* Upgrades
* libatasmart
* software center
* KDE
* etc


That part of your post I do not understand. I have not reported any trouble with Software Center (don't like it too much, seems to be fine otherwise) or KDE (don't use it).

The upgrade issue has hit many people, just take a look at this forum. I can confirm that there is a relation between the number of installed packages and the probability of the upgrade going south.

libtasmart - I cannot tell you where the problem with Samsung drives is rooted, but it is definitely there and reproducible. Are you using any Samsung drives, especially recent models? 

> 

Luckely Ubuntu supports 4 releases at any given point, so pick one you like and stay with that one. Upgrades are not needed to have a running Ubuntu box. But when you don't run LTS you need to upgrade eventually but you can wait at least 18 months before doing so.

Completely right and I am happy with 9.04 for now. Once Lucid is stable, I will have to do a fresh install, unfortunately.

---

### Post by slakkie on 2010-01-11
> 
Fair enough. If it would be the only problem in Karmic, I could live with the workaround, which I posted here: [http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)


That is a perfect workaround, I use pinning to mix my systems. I don't download the packages manually. I just update one file and downgrade via aptitude install package=version.

> 
I do not know for sure where the problem lies. Smartmontools tends to work better, as it has options for Samsung HDs. It seems that most recent Samsung drives have switched the byte order of the raw parameters, which causes Ubuntu to think that there are millions of "Pending Sectors", even though the normalized results (the single byte values counting down from 100 or 253) are normal.

In any case, you can find many reports from irritated people that believe that their drives are failing - or who even replaced perfectly healthy drives.

libtasmart - I cannot tell you where the problem with Samsung drives is rooted, but it is definitely there and reproducible. Are you using any Samsung drives, especially recent models? 


I'm not aware of having any Samsung HD's. I have WD and Seagate drives. Apart from the issue during Karmic development my WD disks have been working fine.  

> 
I understand that it is a kernel problem, but I would agree that the move to EXT4 as default was premature and should have been removed from the downloadable Live CD as soon as the problem became apparent.


I tend to agree with you. Although I'm running ext4 on my root partition of Lucid (which I hardly use, since Lucid is highly unstable for me atm). 

> 
That part of your post I do not understand. I have not reported any trouble with Software Center (don't like it too much, seems to be fine otherwise) or KDE (don't use it).


You said it was insufficiently tested, I disagreed naming a few packages I tested during Karmic. 
Software Center is nice, but I don't like the GUI that much. I should be able to select which packages I want to install, then hit a button and install them all at once. Not one by one. Aptitude on the command line is much better :)
KDE is really nice,  a real improvement from what I've seen in Intrepid/Jaunty. 

> 
Completely right and I am happy with 9.04 for now. Once Lucid is stable, I will have to do a fresh install, unfortunately.

Why? Don't tell me because of ext4 ;)

---

### Post by recluce on 2010-01-12
> **slakkie said:**
> 
I'm not aware of having any Samsung HD's. I have WD and Seagate drives. Apart from the issue during Karmic development my WD disks have been working fine.

The problem **only** exists with Samsung and I could easily verify that here. No problems with Seagate, WD, Hitachi or Fujitsu, all of which I have here as well.

So if you don't have Samsung HDs, you will not have seen that particular bug.
 
>   
You said it was insufficiently tested, I disagreed naming a few packages I tested during Karmic. 


I never said that each and every package was insufficiently tested. Unfortunately, just a few broken packages are more than enough to ruin your experience of a given Ubuntu release (and convince another batch of fresh trial users to go back to Windows). :(

So even if KDE is perfect, if your Laptop has ATI graphics and a Samsung HD, you will have a hard time with Karmic. ;)

> 
(as to the need to do a fresh install when moving from 9.04 to 10.04)

Why? Don't tell me because of ext4 ;)

Naah, I can't see myself moving my production system to ext4 that soon. ;)
(At this time, on my personal production machine, I use ext3 for home and additional storage media, while my root is still on reiserfs).

But that system is one that freezes during upgrade attempts from Jaunty to Karmic - and since I will not be able to upgrade from Jaunty to Lucid directly, a new install it will be.

---

