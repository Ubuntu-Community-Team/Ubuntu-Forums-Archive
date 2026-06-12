---
title: "Loading BusyBox on startup?"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by mogsmar5 on 2008-06-23
Hi 

After two failed Ubuntu installations I think I need to know what is going on!  I know Linux has a reputation for stability, but the impression I've got has not been very good.  I installed it ok (twice) as a dual-boot with Vista on my Dell Inspiron 530.  However, in both cases it eventually stopped loading and started loading BusyBox every other boot.  Eventually it did this more and more often until I could no longer get it to work.  I can not type into BusyBox as every letter I type comes up twice... like 'hheellpp'.  In the end I deleted the Linux partition and fixed my MBR.

Also I cannot boot from the LiveCD anymore... the same thing happened - every other boot would bring up BusyBox and now I cannot load at all.  For the Kubuntu CD it is the same (though I could load OpenSUSE - maybe it is an Ubuntu specific problem?)  The problem is I need to use GParted and OpenSUSE doesn't have it.

I want to start using Ubuntu again but as I am literally starting out in Linux I don't want an unstable system as I am not used to diagnosing problems with Linux and won't understand what is going on.  Please can someone help?

-Christopher

---

### Post by prinknash on 2008-06-23
> **mogsmar5 said:**
> Hi 

After two failed Ubuntu installations I think I need to know what is going on!  I know Linux has a reputation for stability, but the impression I've got has not been very good.  I installed it ok (twice) as a dual-boot with Vista on my Dell Inspiron 530.  However, in both cases it eventually stopped loading and started loading BusyBox every other boot.  Eventually it did this more and more often until I could no longer get it to work.  I can not type into BusyBox as every letter I type comes up twice... like 'hheellpp'.  In the end I deleted the Linux partition and fixed my MBR.

Also I cannot boot from the LiveCD anymore... the same thing happened - every other boot would bring up BusyBox and now I cannot load at all.  For the Kubuntu CD it is the same (though I could load OpenSUSE - maybe it is an Ubuntu specific problem?)  The problem is I need to use GParted and OpenSUSE doesn't have it.

I want to start using Ubuntu again but as I am literally starting out in Linux I don't want an unstable system as I am not used to diagnosing problems with Linux and won't understand what is going on.  Please can someone help?

-Christopher

There's a known problem with the Inspiron 530 and Ubuntu Hardy which sounds like what you describe and can be solved in two ways. 

One is to go into the BIOS and change the SATA setting from IDE (the default) to RAID. That should fix it - but the downside for people who dual-boot is that Windows won't then boot unless you change the setting back again. Which is tedious. (It's fine for me, though, because I only have Ubuntu on my Inspiron 530N - no Windows at all.)

The other way to solve the problem is to use the GRUB boot option all_generic_ide when starting up Ubuntu - preferably by adding it in the appropriate place to the file menu.lst.

Try Googling Inspiron 530 SATA IDE and you'll find references to this issue.

p

---

