---
title: "Upgrading from 10.04 LTS"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by Zammael on 2012-05-06
Hello!

Since I'm no longer able to play certain videos (10-bit) with mplayer, I was told to upgrade, that my distro was 2 years overdue/out of date. Hence I was using an obsolete version of mplayer. :mad:

But I'm not so gung-ho about upgrading to the latest Ubuntu version, given all the bugs, and want to know if I can just upgrade to other versions (11.04 or 11.10) instead of the most recent one (12.04)?

My specs: 
CPU: AMD Athlon 64 3800+
Memory: 2 GB RAM
Graphic Card: GeForce 7800 GT
2 HDD (320 GB & 250 GB)

Thanks in advance! ):P

---

### Post by tiloubrunet on 2012-05-06
the 12.04 is a lts version,so its very stable ;)
Even more stable than the previous one ;)
so you can have your system for 5 years and it will be up to date :guitar:

---

### Post by uriel1998 on 2012-05-06
Okay, but I think I've got the same issue as the first poster.  I've tweaked out 10.04 exactly the way I want it.  I've taken out all the cruft I didn't want.  I have no desire to change WM, app indicators, or anything else - I'm simply too busy to learn a new workflow at this point in the year.  (They might be kludges, but they're *my* kludges, you see? )

What I essentially want are updated versions of the packages I already have.  Is there a way to achieve this *without* going through a full upgrade/install?

---

### Post by Cavsfan on 2012-05-06
I'm sticking with Ubuntu 10.04 Lucid Lynx. It will be supported until April 2013. I have it setup exactly like I want it.
I have heard many problems with nVidia drivers. I have a Geforce 9800 GT with driver 295.49 and have zero problems with it.

I will think more about it when 12.04.1 comes out in July.
But, until then I am staying put. I used to immediately jump to the next version but, my HP printer, copier, scanner wouldn't work or some other problem would arise.
I went to 10.10 but, then came back to 10.04 for the above reason.

I would suggest a clean install rather than an upgrade. There are just to many old things left on you system after the upgrade.
I did an upgrade once and it appeared to have gone very well but, later it began to fall apart and I ended up doing a clean install any way.

I am not in the mood for all of the backing up, etc to install 12.04 right now. I have a 1TB USB drive that I back up both Ubuntu 
when I am getting ready to do a clean install and windows 7 does a once a week back up to the drive.
But, why fix something that isn't broken?

---

### Post by Cavsfan on 2012-05-06
Does this help at all?

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1484138_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1484138)

---

### Post by Old_Grey_Wolf on 2012-05-06
> **Cavsfan said:**
> Does this help at all?

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1484138_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1484138")

Fixed your link in above quote.

---

### Post by Zammael on 2012-05-06
> **Cavsfan said:**
> Does this help at all?

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1484138_[/COLOR]]("http:http://ubuntuforums.org/showthread.php?t=1484138")

I think your URL is broken, but I figured it out. Thanks, will read more before making any decisions.

---

### Post by Cavsfan on 2012-05-06
> **Old_Gray_Wolf said:**
> Fixed your link in above quote.

Thanks **Old_Gray_Wolf** the link some how had quotes around it!

> **Zammael said:**
> I think your URL is broken, but I figured it out. Thanks, will read more before making any decisions.

I have also fixed the link. There shouldn't be any problems with any type of video on 10.04. 
I can look at/listen to any type of audio with Rhythmbox or video with Mplayer (Totem).
If there is, it is a codec problem and that link will show you how to add them.

---

### Post by wilee-nilee on 2012-05-06
The general advice is to wait until the official 12.04 lts is released, then it is actually a lts to lts upgrade. This release should be around the 26th of this month. 

If it was me I would dual boot it and tweak the new 12.04 then remove the 10.04, and if upgrading be sure to clone the lucid first to be safe.

This will give you a list of all the installed packages in 10.04 if needed it will be in home.

dpkg --get-selections > installed-software

---

### Post by Old_Grey_Wolf on 2012-05-06
> **wilee-nilee said:**
> ...If it was me I would dual boot it and tweak the new 12.04 then remove the 10.04, and if upgrading be sure to clone the lucid first to be safe...

That is how I do it. 

*It sounds simple to us after many years of experience working on Linux under-the-hood; however, someone that is inexperienced with Linux in that way may have problems doing that.*

For example, I have 10.04 and I want to migrate to 12.04. I set the computer up to dual boot. I tweak 12.04 the way I like it, and copy my Documents, Music, Videos, Pictures, Downloads, Email, etc. from 10.04 to 12.04. Then I use gparted to remove 10.04. Next time I reboot, I get a Grub error; because, Grub can't find 10.04 in the file system. There is a simple solution; however, it may not be simple for someone that is less experienced with Linux.

:)

---

### Post by wilee-nilee on 2012-05-06
> **Old_Gray_Wolf said:**
> That is how I do it. 

*It sounds simple to us after years of experience; however, someone that is inexperienced with Linux may have problems doing that.*

For example, I have 10.04 and I want to migrate to 12.04. I set the computer up to dual boot. I tweak 12.04 the way I like it, and copy my Documents, Music, Videos, Pictures, Downloads, Email, etc. from 10.04 to 12.04. Then I use gparted to remove 10.04. Next time I reboot, I get a Grub error; because, Grub can't find 10.04 in the file system. There is a simple solution; however, it may not be simple for someone that is inexperienced with Linux.

Yeah if the 12.04 does not put the grub in the mbr it can happen. Grub is a awesome bootloader, can be purged and reloaded and installed to the OS if you want the boot on the previous installs, but can be confusing to some.

Many don't know how to load the mbr from the running OS as well so that is why we are here. :)

---

### Post by Old_Grey_Wolf on 2012-05-06
> **wilee-nilee said:**
> The general advice is to wait until the official 12.04 lts is released, then it is actually a lts to lts upgrade. This release should be around the 26th of this month. 

The 12.04.1 LTS point release is scheduled for July. I don't think that 12.04 will show up in Update Manager until 12.04.01 is released if "Long term support releases" is selected in Software Sources. According to Ubuntu Engineering team, "Upgrades between LTS releases are not *enabled by default* until the first point release".

---

### Post by Cavsfan on 2012-05-07
> **Old_Gray_Wolf said:**
> The 12.04.1 LTS point release is scheduled for July. I don't think that 12.04 will show up in Update Manager until 12.04.01 is released if "Long term support releases" is selected in Software Sources. According to Ubuntu Engineering team, "Upgrades between LTS releases are not *enabled by default* until the first point release".

Thanks! That is good to know. I had my setting to "Long term support releases" selected in Software Sources and was afraid 
that it would try to do that and changed it to "never".
Sometime after July I will probably install 12.04.1 with a clean install. But, there is no hurry as 10.04 is supported until April 2013.

I won't wait until the last moment though.

Just out of curiosity, how safe would you think upgrading from 10.04 to 12.04 will be in July?

---

### Post by dicegeorge on 2012-06-29
when will the 12.04.01 happen?
early July or late July?
[george]

---

### Post by Cavsfan on 2012-06-29
> **dicegeorge said:**
> when will the 12.04.01 happen?
early July or late July?
[george]

August 23, 2012

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule/](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule/)

I may even wait until 12.04.2 comes out on January 31, 2013. Support for Lucid Lynx ends in April 2013.

---

