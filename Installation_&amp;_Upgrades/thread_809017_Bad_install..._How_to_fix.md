---
title: "Bad install... How to fix?"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by wrybread on 2008-05-27
I installed Ubuntu 7.10 on a Thinkpad T40, and after booting I get a Grub error 18, which apparently means "selected cylinder exceeds maximum supported by BIOS". Apparently this is because Ubuntu writes to the Thinkpad's recovery partition, which then gets overwritten by the Thinkpad bios on the next boot... See this link for more info on that:

[http://www.markwilson.co.uk/blog/2006/03/grub-error-18-when-installing-suse-10.htm](http://www.markwilson.co.uk/blog/2006/03/grub-error-18-when-installing-suse-10.htm)

Anyway, I've fixed the bios so it won't allow the recovery partition to be written to, but now I can't install Ubuntu. I boot from the Live CD then go to install, but on the "Prepare Disk Space" screen I only have the option "Guided - use entire disk" or "manual". When I choose "Guided - use entire disk" it tries to format the whole harddrive, which I don't want to do since I have a Windows partition I want to keep. When I choose "manual" it tells me "no root file system is defined".

I can still see the Windows partition by browsing My Computer from the Ubuntu live disk, but obviously I can't boot to it because Grub is crashing.

Oddly, GParted doesn't see any partitions at all on the computer.

Anyone have any ideas?

---

### Post by zvacet on 2008-05-27
You will find good partition guide [here.]("http://psychocats.s465.sureserver.com/ubuntu/installing#partitioning") Use manual way.

---

### Post by wrybread on 2008-05-27
Unless I'm missing something (which is definitely possible), there's nothing that speaks to my problem on that page. There's like 5 lines about partitioning, all of it pretty obvious.

---

### Post by CameO73 on 2008-05-27
When you choose 'Manual' in the Prepare Disk Space screen, you have to specify at least two partitions: which will be the root (/) and which the swap.

As you can read [here]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html"), this means you have to designate those partitions yourself. You could do this by resizing an existing (Windows) partition or use any partitions already there.

Make sure your swap is at least as big as your internal memory (so that hibernate will work). Another tip would be to separate your user data by using an extra partition that will be mounted as /home.

So, in short:

[LIST]
[*]with manual, you have to specify at least a swap and a root (/) partition
[*]an extra partition for /home is really handy
[/LIST]
I'm a little bit concerned by your 'GParted doesn't see any partitions on the computer'-statement. Be sure to have a backup of all your Windows stuff before proceeding!

Oh, and one final question: why are you installing 7.10? 8.04 is just released and works even better!

---

### Post by wrybread on 2008-05-27
Sorry I should have been clearer: I now only have the option for "guided" and for "manual". Guided wants to nuke my whole drive, while "manual" doesn't work: it tells me I need to specify a root partition but doesn't let me specify one. See my first post for the wording of the error if you're curious.

I imaged my drive before installing Ubuntu, I just restored it and am starting over with 8.04.

Thanks for the help.

---

### Post by CameO73 on 2008-05-27
Ah, I see. It seems that GParted will not show your partitions, if they overlap (see for instance [this bugreport](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/96976)). The solution is to 'fix the partition table' ... but that's easier said than done. I think your re-imaging should have done the trick. Otherwise, you may need another partition manager (e.g. [Paragon Partition Manager](http://www.paragon-software.com/downloads/demo.html)) to fix this problem first.

---

