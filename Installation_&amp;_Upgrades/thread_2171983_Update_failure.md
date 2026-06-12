---
title: "Update failure"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by ka2012 on 2013-09-02
I have a Hp pavilion dm1 that is(was) dual booting windows 7 and ubuntu 12.04. I earlier today, I tried to update it to 12.10. The update process was going fine (except I kept getting a bunch of lines similar to this during the update process: "Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not work" but I didnt think it was harmful and had to do with duplicate files or something...) The updater finished, I selected to remove obsolete files, and then I restarted. GRUB menu came up fine, only difference was ubuntu was renamed to just "ubuntu"(before it was "ubuntuGeneric then the version number) and now theres an "other options" choice. I tried to boot Ubuntu and a black screen came up. I waited about 10 minutes, but it didn't do anything, so I turned off the computer and tried to boot into windows. I get a message that said "a disk read error occured. press control alt delete to restart". I booted into my live cd that I used to install, and all my partitions look fine in gParted, so I don't know whats wrong. Help?

---

### Post by TheFu on 2013-09-02
Don't know what happened. Check that you didn't fill the disk for / up completely. Full partitions are bad.  Check the links in my sig for boot-repair and give that a try.

---

### Post by ka2012 on 2013-09-04
How do I check to see if the / disk is completely filled up? I tried boot repair and after it said it was reinstalling grub, it is giving me a screen that says "LDM-blocker detected, please backup your data, do you want to continue" What will it do to my computer if I click yes? I tried googling the message and found this thread, which seems like a pretty similar problem to mine:  [http://ubuntuforums.org/showthread.php?t=2102908](http://ubuntuforums.org/showthread.php?t=2102908)  (it also suggests several workarounds in one of the links, one of which is boot-repair)

by the way, here's the link to my boot-repair summary, if it helps:  paste.ubuntu.com/6056171/

---

### Post by TheFu on 2013-09-04
Two types of "full"
* df -i
* df -k
Check both.

I'll come back later to look at the links.

Never heard of LDM [https://en.wikipedia.org/wiki/Logical_Disk_Manager](https://en.wikipedia.org/wiki/Logical_Disk_Manager) before.  Scary. Linux can span volumes over multiple disks too - the only time I had any data loss was when I did that and 1 of the 3 disks involved failed.  All the data on all 3 drives was lost. I didn't have backup religion back then.  That loss is what convinced me to get backup religion.

I'd backup all the partitions 100%, wipe everything, then restore being careful NOT to use LDM anything. There is probably a better solution.

---

### Post by ka2012 on 2013-09-04
From what I found when I searched it, this has happened to a few people...it only seems to happen in 12.10 and one of the posts said it had something to do with grub 2.00 (which would make sense since I was installing a new Ubuntu version and it really shouldn't have affected windows at all) The link has a couple workarounds/fixes that seem to have worked for other people, so I think I'll probably try those before resorting to wiping everything...

Heres a screenshot of the results from those commands...I don't really know what much of it means, but it looks like the / are only 1% and 4% full, so that's good...
[ATTACH=CONFIG]246010[/ATTACH]

---

### Post by ka2012 on 2013-09-05
One of the bug reports suggested using boot repair to replace GRUB2 with GRUB Legacy ( [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255) )...do you think if I installed GRUB legacy, it would fix my problem?

---

### Post by ka2012 on 2013-09-07
Ok, so ldm-blocker message was caused by something that happened with windows when I was installing ubuntu for the first time a couple months ago (I accidentally converted my hard drive to a dynamic disk and back) I still have no idea why ubuntu 12.10 gave me a black screen. I found a solution to get windows working, but I couldn't figure out how to fix ubuntu, so I just reinstalled it with 12.04 and now both ubuntu and windows are working fine. Thanks for your help!

---

