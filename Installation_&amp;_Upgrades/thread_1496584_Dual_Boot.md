---
title: "Dual Boot ???"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by BobbyDing on 2010-05-29
Hi Folks,
I have two physical drives. One has Ubuntu 10.04 and one has XP. Each was set up on the same machine, only separately (only one of them in the machine at a time). I would like to install them both in the machine and have the option to boot to either. Once I install the drives, how do I get Grub to recognize and set itself up for dual booting to either OS?

Thanks!

Bob

---

### Post by darkod on 2010-05-29
After you connect both disks and you power on, go into BIOS right away and set the ubuntu disk to be first in hdd boot order, to make the computer boot from it, instead of going straight into windows.

You will still not see any OS choice menu on the first boot, because ubuntu is still unaware of windows. Once it boots into ubuntu, in terminal run:

sudo update-grub

That should report your XP found and will create the boot menu offering choice for Ubuntu and XP. So, just keep booting the ubuntu disk as first choice, grub2 on it will handle the boot menu and booting.

---

### Post by donaldt on 2010-05-29
I have a very well mannered Ubuntu 9.10 operating system working on my portable Acer.  Also, dual booting from Grub, a windows XP pro os, working as it should.  

I would like very much to upgrade to Ubuntu release "10.04 LTS", which has been lurking in update manager waiting for me to press the "upgrade" box.  I believe I could sort out any issues that may come with the new and still not totally "Ready for prime time" 10.04".  However, I know I will lose my XP and will have to re-configure the Grub boot to go find XP once again.

I could alternatively upgrade via a live CD, but don't want to fuss with the swapping of CD's to accomplish that task. 

I want to keep my dual boot (from my one internal hard drive) that is working without problems, but realize that if I upgrade I will then have to repair the loss of Windows XP by performing all types of unnatural acts to recover the proper boot sequence.

Has anybody come up with a way to make changes to the grub boot up PRIOR to doing an upgrade.  It would seem to me that would be preferable, but perhaps it is impossible.

I even have Canonical paid support and they don't support that type of software issue.  Why does it have to be so damned complicated to move from one iteration to another?  Anybody care to tackle this subject?

---

### Post by darkod on 2010-05-29
> **donaldt said:**
> I have a very well mannered Ubuntu 9.10 operating system working on my portable Acer.  Also, dual booting from Grub, a windows XP pro os, working as it should.  

I would like very much to upgrade to Ubuntu release "10.04 LTS", which has been lurking in update manager waiting for me to press the "upgrade" box.  I believe I could sort out any issues that may come with the new and still not totally "Ready for prime time" 10.04".  However, I know I will lose my XP and will have to re-configure the Grub boot to go find XP once again.

I could alternatively upgrade via a live CD, but don't want to fuss with the swapping of CD's to accomplish that task. 

I want to keep my dual boot (from my one internal hard drive) that is working without problems, but realize that if I upgrade I will then have to repair the loss of Windows XP by performing all types of unnatural acts to recover the proper boot sequence.

Has anybody come up with a way to make changes to the grub boot up PRIOR to doing an upgrade.  It would seem to me that would be preferable, but perhaps it is impossible.

I even have Canonical paid support and they don't support that type of software issue.  Why does it have to be so damned complicated to move from one iteration to another?  Anybody care to tackle this subject?

I have no idea what are you talking about. You do not lose dual boot capability in grub2 when upgrading.

However, during the upgrade, it seems there is a window asking where to install grub2, offering choice for all DISKS and all PARTITIONS. Users who don't know the difference, or what they should do, can select ALL THE PARTITIONS which will make your windows unbootable from the grub2 menu. I guess you are referring to this.

So, unless you install grub2 to all of your partitions, you are safe. Grub2, as bootloader, goes to the MBR of a disk, except in special situations. Not on partitions.

In upgrades, unfortunately, other things can go wrong, which I can't predict for your specific machine. But not being able to boot windows usually happens only in the situation I described above. Don't do that, and you're fine.

Also, it's a good practice to burn 10.04 image to a cd and use the Try Ubuntu mode. It will show any possible incompatibility with your machine. If there is such, you can expect problems after the upgrade. So 10.04 not running nice in live mode is a sign to hold on with upgrading, at least until you find out what's bothering it and how to fix it.

---

### Post by donaldt on 2010-05-31
DarkOD,

Despite the fact you didn't know what I was talking about, your information was very useful.  There are many horror stories about losing the windows part of a dual boot configuration while upgrading to 10.04.

I guess I was spooked.  Anyway, as you correctly stated that does not need to happen.  I downloaded 10.04 last night.  I chose the box in update manager and it only took 1.5 hours.  All went well and it is up and running with minimum help from me.  Thanks for your help.  I still have my dual boot capability and XP is working as before.

I have a couple of issues.  When changing from 10.04 to XP, the grub menu is slow to come up.  When changing back to 10.04, the grub menu is slow to appear (one wonders if it will show up at all?) and the boot into 10.04 is much slower than in 9.04.  I have heard these complaints before.  Anything that can be done, or is that an already documented bug?

Thanks again for your assistance.  It is much appreciated.

donaldt::P

---

### Post by darkod on 2010-05-31
> **donaldt said:**
> DarkOD,

Despite the fact you didn't know what I was talking about, your information was very useful.  There are many horror stories about losing the windows part of a dual boot configuration while upgrading to 10.04.

I guess I was spooked.  Anyway, as you correctly stated that does not need to happen.  I downloaded 10.04 last night.  I chose the box in update manager and it only took 1.5 hours.  All went well and it is up and running with minimum help from me.  Thanks for your help.  I still have my dual boot capability and XP is working as before.

I have a couple of issues.  When changing from 10.04 to XP, the grub menu is slow to come up.  When changing back to 10.04, the grub menu is slow to appear (one wonders if it will show up at all?) and the boot into 10.04 is much slower than in 9.04.  I have heard these complaints before.  Anything that can be done, or is that an already documented bug?

Thanks again for your assistance.  It is much appreciated.

donaldt::P

Do you have them on two disks or sharing the same disk? And do you have other disks at all?

If grub2 is on another disk from ubuntu, it can have delays searching for it. For fastest loading, it's always recommended to have grub2 on the ubuntu disk. Not that it won't work otherwise.

---

### Post by BobbyDing on 2010-05-31
That did the trick!!  Thanks!

---

