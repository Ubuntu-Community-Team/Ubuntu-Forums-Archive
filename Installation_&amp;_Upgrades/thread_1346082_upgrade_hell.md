---
title: "upgrade hell"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by pyromax on 2009-12-04
Hi,

-- begin rant--

Can I say: Linux (or at least Unbuntu) is far from being an alternative to Microsoft Windows. Because I never had to buy a new computer after I chose to install updates in a windows session, but with Ubuntu configuring raid devices (which were never there to begin with) and a faulty boot loader I'm ready to give in.

I did something stupid, I clicked install when that ever present updates window poped-up and did not really pay attention during all the windows and pop-ups that came by. And now suddenly I cannot boot any of the working operating systems I had, because somewhere during this upgrade Ubuntu decided I need a raid device. (There is a reason I have disabled that in my bios, why do you ignore my bios?)

I really think some more thought could have gone to that raid thingy you are so desperate to push on to people. I do not want it. And it took me a lot of reading and downloading of strange versions of ubuntu before I could even find one that I could install.
And in the process of trying to fix everything (instead of reinstalling, I mean, does everyone just throw any everyting?) I probably killed all my changes of ever getting my alternative operating systems to work again (yes, there is a windows in there).

I find this very frustrating. I was just trying to convince my family to start using Ubuntu, when this happens and I cannot sell it anymore as an alternative.
Also I find it very annoying that the upgrade of one OS on one partition (out of many) can damage everything else. (I mean, this is worse than windows: that just ignores everything else, not destroy it).

OK, now for the annoying stuff:

-- end rant --

I have a pc with an amd 64-bit dual core processor. I also have three disks in there:
a - one that is now f***d up and I can play with
b - one that has 3 partition:
  1 - old-messed-up ubuntu
  2 - XP
  3 - linux swap
c - one that has a ntfs filesystem and a lot of data (~600GB which I do not want to lose).
(the numbers have no relation with /dev/sdXY of (hdX,Y))

There seems to be no way in which I can boot from the old-messed-up ubuntu, but suggestions are welcome.

I tried a completely fresh install of ubuntu 9.10 on a partition on the first harddisk, but even then, grub fails (it gives errors about if and fi) and I cannot get it to detect either the old ubuntu installation or windows. Again, any suggestion is welcome.

---

### Post by abdo5705 on 2009-12-04
Did you have 9.04 installed before? If you did maybe you can reinstall it. I had the same problem and it turned out that the CD I made was the problem. I reinstalled 9.04 and everything worked. If that doesn't work... maybe you can run a live session to recover your data.

---

### Post by u.b.u.n.t.u on 2009-12-04
pyromax, hi and welcome to the Ubuntu community.

Sorry don't really have time to read rants, no matter how valid they may be.

Do you have a question? Please make such concise and we can hopefully proceed from there.

---

### Post by pyromax on 2009-12-04
in reply to abdo5705
No I started with ubuntu 8.4 (or 8.10, not really sure) and gradually upgrade from there.
I'm trying to find my old CD now.

in reply to u.b.u.n.t.u.
I know about the rant, that's why I did the start/end thing.
I would like to know how I can recover from a botched up upgrade.

---

### Post by u.b.u.n.t.u on 2009-12-04
Lets start at the beginning.

Q1 What were you upgrading? (HDD capacity, operating system(s) and versions).

Q2 What is the error(s) message and or event that you encountered?

---

### Post by pyromax on 2009-12-04
Lets start at the beginning.

Q1 What were you upgrading? (HDD capacity, operating system(s) and versions).

Q2 What is the error(s) message and or event that you encountered?

Ok,
Q1 Ubuntu has this feature where it scans for updates and apparently this includes kernel upgrades. I had a running ubuntu installation (installed 8.4 but I think it was upgrade to 9 sometime ago). Then suddenly this pop-up appears with the option to upgrade to 9.10, which I did.
So it is only an OS version upgrade. (i cannot be sure from which, because I cannot start anything. this is all typed from a different computer).

Q2 The initial error after upgrade was that the root device could not be found. I think it suddenly thought I had a raid configuration, but I'm not sure. It said something about /dev/mapper_XYY. silicon raid something. I cannot reproduce it anymore.
I tried every option in grub I could think of, but it would just not boot. Then I wiped one of disks and tried to install 9.10 there, but that installation does not even recognize other OS-s in my pc. It also made it impossible to (try to) boot the old ubuntu install (that's why I cannot reproduce the exact errors, sorry).
Do you know of any way which I can use to go back to my old installation?

---

### Post by u.b.u.n.t.u on 2009-12-04
The priority is to ensure that your data is safe. Do you have data on the HDD with the failed Ubuntu update that needs to be rescued? Once this is answered we may be able to proceed.

What is the exact version of Ubuntu you had working, before the update?

---

### Post by pyromax on 2009-12-04
What is the exact version of Ubuntu you had working, before the update?

Hi,
I think the data is safe: I have not touched the disks on which it resides.
And yes, there is data on the disk of the failed ubuntu update. There is a microsoft windows XP partition there, I would like to preserve. And possibly the old ubuntu version although i'm (almost) ready to give up on that one. The third and last partition is a linux swap partition, so that's of no interest.
Most of the data is on a separate disk, so as long as I leave that alone, I'll be ok.
(It would be nice to be able to access it, though. But that's more my fault, than anyone else's, sorry: ranting again).

And I'm desperately trying to get something going to be able to mount my old ubuntu partition and figure out what version I had. I know I once installed ubuntu 8.04, because the cd is lying in front of me (but it's somehow not booting anymore). 
I'm a bit confused by the ubuntu and kernel versions:
I just used an (freshly downloaded) ubuntu 9.04 and mounted the old partition. I have kernels 2.6.27-14, 2.6.28-14, 2.6.31-15 in /boot, but i'm not sure which is which ubuntu version.
The good thing is, using this live cd, I can mount my old partition. I just have to figure out how to undo the upgrade.

Do you know if I can use that partition to install the old grub version?
I assume one of these kernel is one from before the upgrade to ubuntu 9.10 and does not have the raid setup in there. So, all I need is an epiphany about grub to get me there? Or did the upgrade do more than a kernel adjustment? (i'm a simple Solaris adminstrator, and I have never done upgrades on *ix only fresh installs. ubuntu is the first upgrade I tried, i'm sorry, i will be more professional next time)

---

### Post by pyromax on 2009-12-04
HA, 
Thanks,
Using the live cd (ubuntu-9.04) I was able to install the old grub on one of my disks, and if I use the boot menu of my motherboard, I can start my XP installation. That's more than I have been able to do whole of last week.

I'm now also getting more confident in getting an old ubuntu kernel to work. I tried the lowest one, but that gives a flickering screen filled with ata errors. Also messages about a 'device-mapper' and a 'stripe' or 'striped', it's a bit too fast for me. But it still looks like some raid problem to me.
Is this fixable, or is it easier to just install fresh and mount and recover the old partition?

---

### Post by u.b.u.n.t.u on 2009-12-04
> **pyromax said:**
> I think the data is safe:

Good.

> **pyromax said:**
> There is a microsoft windows XP partition there, I would like to preserve. And possibly the old ubuntu version although i'm (almost) ready to give up on that one. The third and last partition is a linux swap partition, so that's of no interest.

So an Ext3 with Ubuntu and NTFS with XP?

Perhaps consider reinstalling Ubuntu to the linux partition.

Provided your data is safe, as you have stated, instead of trying to restore something not needed, a fresh install would be far easier. You will need to decide what path is best. Install or rescue.

> **pyromax said:**
> Most of the data is on a separate disk, so as long as I leave that alone, I'll be ok.

This is best practice and how I use my computer.


> **pyromax said:**
> (It would be nice to be able to access it, though. But that's more my fault, than anyone else's, sorry: ranting again).

Getting your operating systems working will do that, alternatively use a live CD to access the data on the data HDD.


> **pyromax said:**
> And I'm desperately trying to get something going to be able to mount my old ubuntu partition and figure out what version I had. I know I once installed ubuntu 8.04, because the cd is lying in front of me (but it's somehow not booting anymore).

So you want your HDD to be a dual boot with Ubuntu 8.04 and XP - is that correct?

> **pyromax said:**
> I'm a bit confused by the ubuntu and kernel versions:

They are often updated, but being cutting edge may cause some problems.

I posted here about the lasted kernel, 2.6.32 being released. Not relevant to fixing your computer, but may be worth a read after all is sorted.

[http://ubuntuforums.org/showthread.php?t=1344639](http://ubuntuforums.org/showthread.php?t=1344639)


> **pyromax said:**
> .
The good thing is, using this live cd, I can mount my old partition. I just have to figure out how to undo the upgrade.

If the data is safe, the easiest way to fix this is a fresh install of ubuntu 8.04 onto the Ext3 partition.

I take it you have backup your /home you browser bookmarks, ogg files and the like. If not, use a live CD and try to do that now.

> **pyromax said:**
> Do you know if I can use that partition to install the old grub version?
I assume one of these kernel is one from before the upgrade to ubuntu 9.10 and does not have the raid setup in there. So, all I need is an epiphany about grub to get me there? Or did the upgrade do more than a kernel adjustment? (i'm a simple Solaris adminstrator, and I have never done upgrades on *ix only fresh installs. ubuntu is the first upgrade I tried

A lot of questions and this highlights the problem with trying a rescue. Too many "what ifs" and we are limited to the medium of text communication. So rather a disadvantage.

So to conclude:

1. Your data needs to be safe - check this. Make 100% sure.

2. I would think a reinstall of Ubuntu 8.04, your previously working operating system onto the Linux Ext3 partition may present fewer problems than attempting a rescue of the same. This needs to be your decision and I will continue to assist as best as I am able whatever you decide. I make no recommendation.

I think this procedure will return to you a working computer, unless I have missed something.

---

### Post by u.b.u.n.t.u on 2009-12-04
> **pyromax said:**
> HA, 
Thanks,
Using the live cd (ubuntu-9.04) I was able to install the old grub on one of my disks, and if I use the boot menu of my motherboard, I can start my XP installation. That's more than I have been able to do whole of last week.

I'm now also getting more confident in getting an old ubuntu kernel to work. I tried the lowest one, but that gives a flickering screen filled with ata errors. Also messages about a 'device-mapper' and a 'stripe' or 'striped', it's a bit too fast for me. But it still looks like some raid problem to me.
Is this fixable, or is it easier to just install fresh and mount and recover the old partition?

Okay. After reading my post above, please advise.

---

### Post by pyromax on 2009-12-04
I agree, there are limitations to textual communications.
(begin rant)
[INDENT]But is this case it helped a bit: it takes time, so I have to think more instaed of just being annoying. I still think the upgrade is botched (why suddenly introduce raid), but it is also a bit my fault: I should have paid more attention.
[/INDENT](end rant)

I will reinstall the 9.04 version on the old partition, after I have backup-ed (or backed-up) the interesting stuff, as you suggested. And I will make sure my all data is secured on the 'data' disk, to make fixing mistakes easier in the future.

Thanks, for giving me insight and making me answer you and thus forcing me to think.

---

### Post by u.b.u.n.t.u on 2009-12-04
Post how it goes and all the best!

---

