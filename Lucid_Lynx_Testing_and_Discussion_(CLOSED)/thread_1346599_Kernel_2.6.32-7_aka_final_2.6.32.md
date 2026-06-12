---
title: "Kernel 2.6.32-7 aka final 2.6.32"
date: 2009-12-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by plun on 2009-12-05
Is available with Synaptics, linux-image and linux-headers

Meta package comes later.


Linus Torvalds about this kernel:
[http://lkml.org/lkml/2009/12/3/11](http://lkml.org/lkml/2009/12/3/11)

Kernelnewbies:
[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

Ubuntu update:
[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001253.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001253.html)

No problems on my testbox....

---

### Post by hikaricore on 2009-12-05
Wonder if NFS works properly yet, I'll have to test after I wake up.

---

### Post by xebian on 2009-12-05
Works great even in karmic.

---

### Post by autocrosser on 2009-12-05
Working very well here--"looks" like it has even taken care of my startup problems.....

---

### Post by Gina on 2009-12-05
Interesting - I'll give it a go. Thank you :)

---

### Post by plun on 2009-12-05
More about Ubuntu and kernels, 10.04 will use 2.6.32 but maybe with a backport to 2.6.33

From Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA](http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA)


..

---

### Post by Gina on 2009-12-05
I added the new kernel, ran update-grub and rebooted but can't see any difference so far.

---

### Post by cecilpierce on 2009-12-05
boots faster, no usplash though and when i run usplash in a terminal it grays out gdm and then dies and have to reboot, never seen anything like that before ???

---

### Post by amano on 2009-12-06
> **plun said:**
> More about Ubuntu and kernels, 10.04 will use 2.6.32 but maybe with a backport to 2.6.33

From Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA](http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA)


..

Hmm. I read it that only kernels from stable ubuntu releases would be backported. Only when 10.10 is released we we see the backported kernel in 10.04. That's not too exciting for us as we will certainly switch to 10.10 directly...

---

### Post by xebian on 2009-12-06
> **Gina said:**
> I added the new kernel, ran update-grub and rebooted but can't see any difference so far.

Try moving iso's around.  For me it's huge.  At least in dolphin.

---

### Post by xebian on 2009-12-06
> **amano said:**
> Hmm. I read it that only kernels from stable ubuntu releases would be backported. Only when 10.10 is released we we see the backported kernel in 10.04. That's not too exciting for us as we will certainly switch to 10.10 directly...

I'm using it on karmic now.  Why wait when you can get the debs and install it to karmic or jaunty.

---

### Post by plun on 2009-12-06
> **amano said:**
> Hmm. I read it that only kernels from stable ubuntu releases would be backported. Only when 10.10 is released we we see the backported kernel in 10.04. That's not too exciting for us as we will certainly switch to 10.10 directly...

Yup, you are right....


> We have decided to experiment with backporting newer kernels onto LTS releases for Lucid.  This will involve provision of kernel from later
cycles into Lucid, supported on certified platforms.  The policy here is
being firmed up now.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html)



---

### Post by zika on 2009-12-06
As far as I can see 2.6.32-7.10 came without third part. linux-headers-2.6.32-7, it is still ..9 ... The difference I see between ..10 and ..9 is that ..10 doesn't give me nice screen in tty.
Update: third part came through upgrade but my tty is, still, ugly ...
I find 2.6.32-999 from [kernel.ubuntu.com]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/") as of yestarday noticably faster than 2.6.32-7-10 on my ATI machine. Appart from the problem with scren at gdm start (using radeon.modeset=1, since 999 defaults to non-KMS) that is easily solved by escaping to tty1 and restarting gdm.

---

### Post by volanin on 2009-12-06
I am using this kernel in karmic, and I am seeing a few glitches with
Intel 945GM graphics. The display flickers for a fraction of a second
from time to time, and sometimes everything goes black requiring a
restart. Anyone else with the i915 intel driver experimenting the
same?

:sad:

Edit: Same thing happens if I compile the source from kernel.org

---

### Post by Reiger on 2009-12-07
I guess that this is KMS; try researching the relevant boot parameter for your intel hardware to disable KMS at boot.

E.g. for **ATI cards that use the radeon driver** it is **radeon.modeset=0**.

---

### Post by DougieFresh4U on 2009-12-07
I have 2 Lucid partitions running the .32 kernel. One I am using the 'fglrx' and the other I am using the 'xorg-edgers ppa'.
Compiz seems to be working great with both. I have the ATI Radeon HD3200.
Don't know if this means any thing, but thought I would just throw it out there :p

---

### Post by Yofel on 2009-12-07
My issues with 2.6.32 so far:

NFS server broken. ("No support in current kernel") Filed a bug at Launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493145](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493145)
seems to be a userspace issue.

Intel 945GME suspend broken. After wakeup I get glitches every few minutes and after a while the screen turns black. (same issue as vloanin I guess). There is a intel driver update pending in lucid, maybe that will fix it.

KDE segfaults everywhere. Well, the kde4.4beta (aka 4.3.80) uploads are getting uploaded so that should get better.

---

### Post by jerrylamos on 2009-12-07
Today's update brought in -7.   Oops.  "System > Preferences" and "System > Administration" drop down menus are essentially wiped out.  Only a couple or three items, and in particular no Synaptic.

?

Is there such a thing as "sudo apt-get install Preferences" or "sudo apt-get install Administration"?

Thanks, Jerry

---

### Post by xebian on 2009-12-07
> **jerrylamos said:**
> Today's update brought in -7.   Oops.  "System > Preferences" and "System > Administration" drop down menus are essentially wiped out.  Only a couple or three items, and in particular no Synaptic.

?

Is there such a thing as "sudo apt-get install Preferences" or "sudo apt-get install Administration"?

Thanks, Jerry

apt-get install <pkg-name>

You need to find out which package contains what you are missing.  I doubt the kernel has anything to do with preferences/admin
If you use kde then it would be kdeadmin.

---

### Post by ranch hand on 2009-12-07
I didn't like the look of the remove list and so I just upgraded to the new kernel and anything to do with mesa and let the rest stay back.  I did this on my clean install that has been having the same udevadm problem as this 9.04>9.10>10.04 upgrade.  It boots like a real OS now.

My 9.10>10.04 upgrade is the only one of the three that did not have this problem.

Am upgrading this one the same way now.  Hope for the same result, this booting to recovery>return to normal boot>CLI log in>startx works but gets old.

---

### Post by cariboo on 2009-12-07
@ranch hand if you use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

you don't have to pick and choose what you update, it won't install anything that has missing dependencies.

---

### Post by ranch hand on 2009-12-07
> **cariboo907 said:**
> @ranch hand if you use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```you don't have to pick and choose what you update, it won't install anything that has missing dependencies.
Thank you.  I am aware of this.

I have just about gotten the buggers running in as stable a manner as can be expected at this point.

All three have been giving me little problems.  Daily now seems straight.  Lounge Lizard has been fine except for a bad flicker during boot up and I haven't been in that one yet (just did the same update in it chrooted in).  Stoned Lizard now seems fine but USC will not start.

I would like for all of them, for the first time in about 10 days to be pretty much on the same page.

After I check Lounge Lizard I will probably just do whatever synaptic wants to do in Daily and an Apt upgrade in Lounge and see what happens.

Stoned Lizard may wait as it is my production box in the day time with boinc(alpha) running.  I have almost gotten boinc to run stable as long as it is not on an active screen.  Some problem with my ATI card perhaps.

Anyway I am being real careful today with the updates.  Usually one of the installs just gets whatever is offered and one is handled more carefully and the Stoned Lizard is pampered (kind of a laid back OS anyway).

Tomorrow I will be back on track.

I am just really pleased not to have to boot to recovery>return to normal boot>CLI log in>startx on 2 of 3 installs.  Big improvement.

---

### Post by btn21 on 2009-12-08
It used to take about 25-40 seconds to resume from suspend, but with this kernel it's almost instant. :popcorn:

I'm using this kernel on Karmic

---

### Post by jerrylamos on 2009-12-08
-7 boots to command line only on this IBM ThinkCentre with i845 graphics.  

Select the -6 kernel and boots to full GDM.

?

Jerry

p.s.  With todays 12/09 updates it's booting sort of.  Screen is really wild during boot however it did settle down.

---

