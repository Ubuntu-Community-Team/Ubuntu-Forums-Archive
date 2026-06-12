---
title: "btrfs"
date: 2009-10-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-10-30
will be btrfs in lucid lynx?

---

### Post by NCLI on 2009-10-30
It will be in the kernel 10.04 ships with, so probably.

---

### Post by whoop on 2009-10-30
Isn't it already supported with the current kernel? Even a few kernels back?

---

### Post by NCLI on 2009-10-30
Yes, but the version in the next kernel is supposed to be stable enough for everyday use.

---

### Post by whoop on 2009-10-30
> **NCLI said:**
> Yes, but the version in the next kernel is supposed to be stable enough for everyday use.

production use?

---

### Post by gnomeuser on 2009-10-30
> **whoop said:**
> production use?

Production use would require years of large deployments to verify stability. 2.6.32's btrfs code base is to be considered stable for early adopters.

I run btrfs on this machine, have done for a while and I am perfectly happy with it. No major problems to report, that is not to say that none exist.

---

### Post by whoop on 2009-10-30
> **gnomeuser said:**
> Production use would require years of large deployments to verify stability. 2.6.32's btrfs code base is to be considered stable for early adopters.

I run btrfs on this machine, have done for a while and I am perfectly happy with it. No major problems to report, that is not to say that none exist.

I understand what you mean, but it's not like that happened to ext4, and I would hardly call that early adoption anymore. Maybe it's because ext4 was based on ext3 and btrfs is more from scratch.

Would it be accurate to say this will be the first stage of people actually using the file system?

---

### Post by gnomeuser on 2009-10-30
> **whoop said:**
> I understand what you mean, but it's not like that happened to ext4, and I would hardly call that early adoption anymore. Maybe it's because ext4 was based on ext3 and btrfs is more from scratch.

Would it be accurate to say this will be the first stage of people actually using the file system?

Ext4 is ext3 in many ways, the codebase and designs are stable, in that sense production readiness is going ot take shorter. Though there is something to be said for stability through superior design like btrfs has, it has proven to mature very fast, the design is solid, the featureset is desirable and the stability is already very good.

I would expect btrfs to be ready for use in the timeframe presented by current development cycles (Fedora 13, Ubuntu 10.04, openSUSE 11.3). When we will see deployments on a large enterprise scale I don't know but I suspect it might be sooner than we think mainly because the feature set is so appealing.

---

### Post by keybuk on 2009-10-30
I think we'll probably make sure we have all the necessary tools, though right now one of the big missing bits is boot loader support.  Obviously it won't be really supported until lucid+1 ;-)

---

### Post by gnomeuser on 2009-10-30
> **keybuk said:**
> I think we'll probably make sure we have all the necessary tools, though right now one of the big missing bits is boot loader support.  Obviously it won't be really supported until lucid+1 ;-)

grub1 patches were posted to the btrfs mailing list, provided that is any help.

---

### Post by whoop on 2009-10-30
> **gnomeuser said:**
> grub1 patches were posted to the btrfs mailing list, provided that is any help.

Doesnt' grub2 work with btrfs, or do I still need an ext(2) boot partition (like I often see on systems)?

---

### Post by gnomeuser on 2009-10-31
> **whoop said:**
> Doesnt' grub2 work with btrfs, or do I still need an ext(2) boot partition (like I often see on systems)?

grub2 does not yet have btrfs support.

---

### Post by whoop on 2009-10-31
> **keybuk said:**
> I think we'll probably make sure we have all the necessary tools, though right now one of the big missing bits is boot loader support.  Obviously it won't be really supported until lucid+1 ;-)

Isn't that because btrfs is still subject to change? I read a discussion on grub irc just now. They stated implementing support for btrfs in grub2 would be a waste of time as the btrfs wiki states that btrfs is still under heavy development and is subject to change.

So that information is keeping them from implementing it, as I understand.

---

### Post by toobuntu on 2009-12-10
Per the [blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support"), btrfs support should land in alpha 3.

Per the [spec]("https://wiki.ubuntu.com/FoundationsTeam/BtrfsSupport"), installer support is currently targeted for lucid+1:
> If we manage to work fast enough to add installer support for Lucid, it will not be presented by default, as it is not clear that the filesystem is stable enough yet ... btrfs supports smooth **upgrades from ext3 and ext4** (and also reverting back!), so that **will be the installation path for adventurous users**. (emphasis added)

---

### Post by om26er on 2009-12-24
will it be possible to make /root btrfs and /boot ext4 in lucid?

---

### Post by gnomeuser on 2009-12-24
> **om26er said:**
> will it be possible to make /root btrfs and /boot ext4 in lucid?

It already is today, it's just a bit of work since the steps are manual. 

Looking at the plan:

Move fsck.btrfs from /usr/bin to /sbin: DONE
Update Fedora patch from GRUB Legacy to GRUB 2, and merge: TODO <-- means you don't have to have a separate /boot
Add basic btrfs support to parted: TODO <-- this 
Add btrfs to supported filesystem lists in casper: TODO <-- and this means you should get the option to pick btrfs in the installer (probably safeguarded with some boot parameter on the install medium or only available in the alternative cd to protect users from making a mistake this time around)

---

### Post by eyelessfade on 2009-12-25
From the btrfs [wiki]("http://btrfs.wiki.kernel.org")

[COLOR="Red"]**Btrfs is under heavy development, and is not suitable for any uses other than benchmarking and review**[/COLOR]

---

### Post by Eclipse. on 2009-12-25
> **eyelessfade said:**
> From the btrfs [wiki]("http://btrfs.wiki.kernel.org")

[COLOR=Red]**Btrfs is under heavy development, and is not suitable for any uses other than benchmarking and review**[/COLOR]

We know. :)

Things are starting to reach the stage where larger scale testing is needed however.

---

### Post by om26er on 2009-12-26
can you plz provide me with a way to install ubuntu on btrfs. btrfs seems to be performing very well on my slow speed ssd so i would love to test its performance on the ssd

---

### Post by gnomeuser on 2009-12-26
> **om26er said:**
> can you plz provide me with a way to install ubuntu on btrfs. btrfs seems to be performing very well on my slow speed ssd so i would love to test its performance on the ssd

The easiest way is very likely to wait for Alpha 3. Outside of that you could probably install onto ext4 with a separate /boot then use the migration tool from the wiki to migrate / to btrfs. 

Remember that when you are using an SSD you may get superior performance from btrfs if you use the ssd mount option. Also I have had great experiences with the compression feature as well.

Now I have so far done all my btrfs testing on Fedora (since both they and openSUSE have support in their installers but not if I recall in their bootloaders) but I will put some effort into finding a way to make it testable under Ubuntu.

---

### Post by iggykoopa on 2009-12-27
I've been running btrfs as my root partition for a little while with karmic now, haven't had any issues except high ram use and I had to downgrade to grub-legacy because os-prober doesn't work with btrfs on grub-pc. Just have to set up a separate /boot partition and a few other steps, there's a howto if you google it.

---

### Post by Slug71 on 2009-12-27
Im curious, 
If Alpha 3 or Lucid final has Btrfs in the installer, or lets say even when Ext4 made it to the installer. And you use it, and then come 6 months down the line and a new Buntu release is out which maybe have fixes to the filesystem and you upgrade to the next version. Does the installed filesystem receive those updates or will/can the filesystem only be updated with a fresh install?

---

### Post by mattduckman on 2009-12-27
from their website
> The Btrfs disk format is not yet finalized, but it will only be changed if a critical bug is found and no workarounds are possible.
so you'll only have to reinstall if there's a big problem and the format has to be changed

ext4, on the other hand, is finalized, so the disk format won't change

---

### Post by gnomeuser on 2009-12-27
> **Slug71 said:**
> Im curious, 
If Alpha 3 or Lucid final has Btrfs in the installer, or lets say even when Ext4 made it to the installer. And you use it, and then come 6 months down the line and a new Buntu release is out which maybe have fixes to the filesystem and you upgrade to the next version. Does the installed filesystem receive those updates or will/can the filesystem only be updated with a fresh install?

The data format has been unchanged since July 2009 and even that migration was automatic. The only problem is that once you migrate your dataformat you cannot boot with a kernel older than the one requiring the new format, not without support being backported that is.

So yes, you can assume that your dataformat changes will be applied even if you switch now. Btrfs has generally been good in this regard and I would say that the developers are very responsible with regards to testing and ensuring correctness.

As for general code changes that fix a bug, naturally like a driver when you boot the new code this will be what is running and thus your system will take advantage of it.

It always pays to keep an eye out for important package changes, but this is prudent with all testing. If the kernel changes, wait a bit, read the changelog, follow the forums, stay informed - in 90% of all cases that will save you headaches

---

### Post by nanog on 2009-12-28
wake me up when they decide to support raid5/6, offline fsck, offline volume management, and extent balancing. the whole point of brtfs was to eliminate the annoyingness of creating and maintaining mdadm/lvm. 

PS: and how about those absolutely abysmal phoronix benchmarks for ext4 and brtfs with recent kernels.

---

### Post by falconindy on 2009-12-28
> **mattduckman said:**
> from their website

so you'll only have to reinstall if there's a big problem and the format has to be changed

ext4, on the other hand, is finalized, so the disk format won't change
Ext4 is a stopgap measure that was thrown together as an extension of Ext3. The maintainer himself, Theodore Ts'o, has stated that btrfs is "the way ahead".
> Despite the fact that Ext4 adds a number of compelling features to the filesystem, T'so doesn't see it as a major step forward. He dismisses it as a rehash of outdated "1970s technology" and describes it as a conservative short-term solution. He believes that the way forward is Oracle's open source Btrfs filesystem, which is designed to deliver significant improvements in scalability, reliability, and ease of management.
*source:* [http://arstechnica.com/open-source/news/2009/04/linux-collaboration-summit-the-kernel-panel.ars](http://arstechnica.com/open-source/news/2009/04/linux-collaboration-summit-the-kernel-panel.ars)

Regardless of the stability of the format itself, kernel 2.6.32 introduced a large regression in performance related to an **ongoing reliability issue** intrinsic to the way Ext4 lazily syncs data to the disk. There exists a large possibility of data corruption/loss during an OS lockup or kernel panic.

---

### Post by ranch hand on 2009-12-29
I have been very good at locking up the system on this install of 10.04.  Using boinc pretty well cranked keeps my cpu usage at about 100% all the time.

Open several windows of FF and it will, in time, freeze solid.

There has been no problem with the ext4 format at all.  Recovers very well indeed.

---

### Post by Gina on 2009-12-30
I havn't had any problems with ext4 AFAIK.  Reading up a bit about btrfs it seems it will upgrade from ext3, but will it upgrade from ext4?  I can't seem to find out!  All these file system changes leave me feeling a bit cautious!  ext4 was heralded as the way ahead and we were all encouraged to use it; now it seems it was only a stop-gap :confused:

---

### Post by gnomeuser on 2009-12-30
> **Gina said:**
> I havn't had any problems with ext4 AFAIK.  Reading up a bit about btrfs it seems it will upgrade from ext3, but will it upgrade from ext4?  I can't seem to find out!  All these file system changes leave me feeling a bit cautious!  ext4 was heralded as the way ahead and we were all encouraged to use it; now it seems it was only a stop-gap :confused:

it will upgrade from ext4 as well so far as I know

---

### Post by Gina on 2009-12-30
> **gnomeuser said:**
> it will upgrade from ext4 as well so far as I knowThat's alright then :)

---

### Post by ezsit on 2009-12-30
RE: ext4
> now it seems it was only a stop-gap

I was under the impression that it always was just a stop-gap. Heck, even ext3 was just a stop-gap as it is nothing more than ext2 with the journaling code from JFS layered on top.

---

### Post by Slug71 on 2010-01-19
Any news on whether or not this will make it for Alpha 3 and hopefully the installer?

---

### Post by antiram on 2010-01-31
there are more things to do. 

1. the fsck at boot time with mountall doesn't work because fsck.btrfs has no option "-a". But debian has no package "mountall", it is from a canonical staff.
if i rename /sbin/fsck.btrfs to /sbin/fsck.btrfs-orig and use this script as /sbin/fsck.btrfs it works
```
#!/bin/bash
if [ $1 = "-a" ]; then
        /sbin/fsck.btrfs-orig $2
else
        /sbin/fsck.btrfs-orig $1
fi

```

2. deleting of snapshots/subvolumes (eg. made from btrfs-convert) with "btrfsctl -D" doesn't work because patch 
btrfsctl: add snapshot/subvolume destroy ioctl
is missing in package btrfs-tools

3. /usr/sbin/grub-mkconfig doesn't work. replaced 
```
GRUB_DEVICE="`${grub_probe} --target=device /`"
```
with
```
GRUB_DEVICE="`${grub_probe} --target=device /`" || true
```
and set the grub device in /etc/default/grub with
```
GRUB_DEVICE=UUID=1234...
```
works now.

if someone use a .33 rc kernel then replace in /etc/fstab the errors remount option with "rw" or so. btrfs doesn't recognize the option and boot fail.

is there a way to list not mounted snapshots/subvolumes? I find nothing.

---

### Post by Slug71 on 2010-02-14
Well, i dont think we'll see this in Lucid.

---

### Post by farrell on 2010-02-14
> **Slug71 said:**
> Well, i dont think we'll see this in Lucid.

+1

required changes for btrfs support have been postponed in the blueprint:[U]

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support)
[/U]

---

### Post by ibuclaw on 2010-02-14
> **farrell said:**
> +1

required changes for btrfs support have been postponed in the blueprint:[U]

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support)
[/U]

But ... still doesn't stop people from trying. ;)

[http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

---

### Post by gnomeuser on 2010-02-15
> **ibuclaw said:**
> But ... still doesn't stop people from trying. ;)

[http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

To bad, btrfs support would have made Lucid very attractive. I am hoping this will go in right after the opening of Lucid +1.

---

### Post by ibuclaw on 2010-02-16
> **gnomeuser said:**
> To bad, btrfs support would have made Lucid very attractive. I am hoping this will go in right after the opening of Lucid +1.

I wouldn't hold my breath.

As mentioned before (but perhaps in not to much detail) - the [s]two[/s] one thing holding that back is that there is no one-to-one relation from a btrfs mountpoint to a device, it's a tree, and therefore there can not be a single major/minor (this is a feature).

This comes as a shock to the system from grub2's detection method, that relies on the device's stat.st_rdev of /mntpoint and corresponding stat.st_dev of /dev/sda1 to return the same value (this is a bug in the way grub probes devices).

Regards
Iain

---

### Post by Longinus00 on 2010-02-17
> **gnomeuser said:**
> To bad, btrfs support would have made Lucid very attractive. I am hoping this will go in right after the opening of Lucid +1.

I don't see how having btrfs would make lucid more attractive considering btrfs still hasn't finalized its on-disk format. Btrfs is still under heavy development and is not ready in any way for the average person.

---

### Post by arbrandes on 2010-02-21
> **Longinus00 said:**
> Btrfs is still under heavy development and is not ready in any way for the average person.

I think gnomeuser's point is that it would be nice to have an Ubuntu LTS release, which is very attractive for sysadmins, with btrfs cooked in.  The next window will only occur in 2012.

Adolfo

---

### Post by Longinus00 on 2010-02-21
> **arbrandes said:**
> I think gnomeuser's point is that it would be nice to have an Ubuntu LTS release, which is very attractive for sysadmins, with btrfs cooked in.  The next window will only occur in 2012.

Adolfo

What is a sysadmin going to do with an alpha release filesystem? How is that attractive? The btrfs developers can't even promise that they won't make backward compatible changes to the filesystem, admittedly they are trying not to.

---

### Post by gnomeuser on 2010-02-22
> **Longinus00 said:**
> What is a sysadmin going to do with an alpha release filesystem? How is that attractive? The btrfs developers can't even promise that they won't make backward compatible changes to the filesystem, admittedly they are trying not to.

Well actually gnomeusers point was that he has been using btrfs for a long time and found it quite pleasing. Selfserving goals aside though btrfs is a major new piece of technology of great importance.

While we should be shipping it as a technology preview like any responsible distribution would. Btrfs however is very solid today, the stability bugs one might encounter would be solvable using post-release bugfix updates and seeing as the code is shipped as a preview one could easily get away with considering these non-critical updates.

It would get us on par with Fedora and openSUSE shipping this support in an early form. Yes, we would have to have a separate /boot for now but it would be an acceptable for now.

BtrFS is a much anticipated piece of technology, given that this is an LTS release it is a good chance to introduce it to corporate environments and giving them a chance to take it for a spin. Perhaps preparing their infrastructure for the change that is very likely to come with the next LTS, a chance they would otherwise only have once we get the full support in a regular Ubuntu release.

---

### Post by Longinus00 on 2010-02-24
> **gnomeuser said:**
> Well actually gnomeusers point was that he has been using btrfs for a long time and found it quite pleasing. Selfserving goals aside though btrfs is a major new piece of technology of great importance.

While we should be shipping it as a technology preview like any responsible distribution would. Btrfs however is very solid today, the stability bugs one might encounter would be solvable using post-release bugfix updates and seeing as the code is shipped as a preview one could easily get away with considering these non-critical updates.

It would get us on par with Fedora and openSUSE shipping this support in an early form. Yes, we would have to have a separate /boot for now but it would be an acceptable for now.

BtrFS is a much anticipated piece of technology, given that this is an LTS release it is a good chance to introduce it to corporate environments and giving them a chance to take it for a spin. Perhaps preparing their infrastructure for the change that is very likely to come with the next LTS, a chance they would otherwise only have once we get the full support in a regular Ubuntu release.

If corporations are going to take btrfs for a spin they certainly aren't going to do it on a production machines (atleast, i would hope not) and therefore don't require a lts version of ubuntu to do so. Until btrfs leaves the alpha stage there is just no way any company is going to consider using it. Corporations don't change filesystems just because a new one is availabls, just look at how long google stayed with ex2.

---

### Post by Slug71 on 2010-02-24
> **Longinus00 said:**
> If corporations are going to take btrfs for a spin they certainly aren't going to do it on a production machines (atleast, i would hope not) and therefore don't require a lts version of ubuntu to do so. Until btrfs leaves the alpha stage there is just no way any company is going to consider using it. Corporations don't change filesystems just because a new one is availabls, just look at how long google stayed with ex2.

That is correct but i dont think you are following. Btrfs needs the kind of testing that Nouveau is now beginning to receive. The only way for that to happen is for it to be available. It is important for sysadmins to give it a spin and see where it is BEFORE it goes onto the production machines so that any bugs or concerns they come across can be addressed. But like i have just said, Btrfs is ready for wider testing to begin and like Gnomeuser and others have stated, it is in a very usable state at this time.

---

### Post by Regenweald on 2010-02-24
> **Slug71 said:**
> That is correct but i dont think you are following. Btrfs needs the kind of testing that Nouveau is now beginning to receive. The only way for that to happen is for it to be available. It is important for sysadmins to give it a spin and see where it is BEFORE it goes onto the production machines so that any bugs or concerns they come across can be addressed. But like i have just said, Btrfs is ready for wider testing to begin and like Gnomeuser and others have stated, it is in a very usable state at this time.

But still, any sysadmin looking to be proactive with their company's data can test btrfs if they want. If I can follow a simple tutorial/blog post and implement butter on my desktop, I hazard to think that an interested sysadmin could implement and test. Btrfs is great, but realistically, it may be 2013/14 when corporations even begin considering mass rollouts. That's a lot of testing time.

---

### Post by kahumba on 2010-02-24
The option to install Btrfs **should** be available with a notice next to it that it's **only** for users who know what they're doing. End of story, anyone's happy.

---

### Post by gnomeuser on 2010-02-24
> **Longinus00 said:**
> If corporations are going to take btrfs for a spin they certainly aren't going to do it on a production machines (atleast, i would hope not) and therefore don't require a lts version of ubuntu to do so. Until btrfs leaves the alpha stage there is just no way any company is going to consider using it. Corporations don't change filesystems just because a new one is availabls, just look at how long google stayed with ex2.

I am thinking that if a corporation uses Ubuntu they are likely to roll out such technology previews with them to let them know what is coming. To let them deploy and play with test setups on the same distribution they are likely used to as well as follow and participate in the progression of btrfs and UBuntu via the incremental releases.

Red Hat e.g. rolled out ext4 first as a very early technology preview like this and I believe they will default to it in the next major release and the feedback from this approach I understand is generally very positive for them. 

Btrfs is also very stable, there hasn't been a dataformat change since July and even that was automatically migrated. It converts existing ext3/4 partitions using a tool (and retains it mountable in the old format I believe though I haven't tried that). Btrfs is definitely solid enough at this point to release to early testers like those that would use technology previews like these. 

It seems very safe at this point to have it as an opt in addition. Fedora currently does this for btrfs with a parameter to the installer and Ubuntu has done it before with encrypted home directories. 

The only thing is that since btrfs currently isn't supported by grub2 (see above) a solution should be found. The easiest solution seems to be denying installation without a separate /boot if / is on btrfs. I also believe there are patches for grub1 so perhaps such installs could use that. Though that would perhaps open a support nightmare for none btrfs errors in that the code surface is vastly increased and bootloaders are as I understand not entirely simple code to maintain.

Such fairly simply support after the firt option might be a good project for a new contributor wanting to get into the Ubuntu installer and related technologies to work on.

---

