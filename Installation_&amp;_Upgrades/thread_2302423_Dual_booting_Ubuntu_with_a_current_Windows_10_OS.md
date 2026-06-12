---
title: "Dual booting Ubuntu with a current Windows 10 OS"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by Skywalker# on 2015-11-10
Hi all,

I have been dipping in and out of Ubuntu for years (normally when stuff goes wrong) and this time I'm thinking of sticking with it and I want to learn and explore the Linux world more.

The issue I had last time with dual booting is that I couldn't get back into Ubuntu or Windows when the machine started up - I don't think I had RF** boot loader (can't remember what it was called) like I did when I had it on the map - could this be why?

If I remember correctly I had to do some kind or MBR command and find an ID to get it to load my windows partition again.

Also in BIOS I think there was a 'legacy' option or something? Are there different boot modes and will Ubuntu work in the same that swindles is using?

Thanks,
~Luke

---

### Post by Cavsfan on 2015-11-10
> **~Luke said:**
> Hi all,

I have been dipping in and out of Ubuntu for years (normally when stuff goes wrong) and this time I'm thinking of sticking with it and I want to learn and explore the Linux world more.

The issue I had last time with dual booting is that I couldn't get back into Ubuntu or Windows when the machine started up - I don't think I had RF** boot loader (can't remember what it was called) like I did when I had it on the map - could this be why?

If I remember correctly I had to do some kind or MBR command and find an ID to get it to load my windows partition again.

Also in BIOS I think there was a 'legacy' option or something? Are there different boot modes and will Ubuntu work in the same that swindles is using?

Thanks,
~Luke

You could check out my wiki for customizing grub. I boot Xubuntu 16.04, Arch Linux and Windows 10 myself.
Here is the last link on the thread with a picture of what my grub screen looks like.

[http://ubuntuforums.org/showthread.php?t=2076205&page=39&p=13380533#post13380533](http://ubuntuforums.org/showthread.php?t=2076205&page=39&p=13380533#post13380533)

It never fails to boot into any system I have. Grub only recognizes the first 4 partitions and this method can use any number of partitions.
I used to have like 6-7 systems on here now down to just 3.

---

### Post by yancek on 2015-11-10
The default for window 8 and later is to install in UEFI mode.  If this was a direct install of windows 10, that is likely what you have.  If you upgrade from 7, that may not be the case so the first thing you should check is if you have an EFI partition on the disk.  If windows is UEFI, then Ubuntu must be also and I believe there should be an option to select this on the installation medium.  The link below explains UEFI in dual boot so it might be worthwhile to read that before starting.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Cavsfan on 2015-11-10
If you have Windows installed in UEFI mode then yancek's link will help .

But, if you did like I did and upgraded from windows 7 to 10 then the grub wiki will work wonders.

---

### Post by Mark Phelps on 2015-11-10
Win10 continues the default hibernation policy of its predecessor -- Win8 -- using something called Fast Startup. 

FastStartup forces Windows to go into hibernation even if you choose Shut Down and when this happens, all open partitions remain mounted, preventing access to those partitions from outside the Windows OS that was running. This will prevent mounting Windows filesystems in Linux and, in some cases, will prevent the Linux installer from even seeing Win10.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by Skywalker# on 2015-11-10
Thank you all for your responses and great boot loader cavsfan!

Just to confirm these are the options I have selected:

In boot order it says UEFI next to HDD and in 'boot mode selection' it says UEFI and legacy.

I assume that is fine.

I'll go and install it shortly and I'll disable the fast startup like you suggested Mark.

Thanks :)

---

### Post by Cavsfan on 2015-11-10
Good! Glad you're getting it all sorted out.

Just remember you can view the windows partition from Linux but you never want to write or delete anything.
Trust me I've been there and done that. In Arch I can mount my C: drive read only which is ideal to me.

Xubuntu 16.04 gets errors trying to mount my windows 10 partition and won't do it. But, I don't care.

---

### Post by Skywalker# on 2015-11-11
Thanks again for the tips. I sorted it but on my MacBook Pro - it now dual boots using RFind.

I'll do it on my PC soon. I don't remember seeing an option to install Ubuntu in UEFI when I used the DVD though.

---

