---
title: "Install Edgy Dell GX280"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-04-06
Hello, I picked up a Dell Optiplex GX280 and want to install Ubuntu on it.  It has a 160G SATA hard drive and when I install the LiveCD it does not see the hard drive.  If I type sudo fdisk -l ro use Gnome Partition Editor there is nothing.  When I try to install there is no hard drive that appears to install to.

I know for a fact that the hard drive is in good working condition as it has a copy of XP on it that boots into XP.

Is there something special you need to do to install Ubuntu on a SATA hard drive?  My laptop has an 80G SATA hd and no problem there.  The Dell has a hard drive model number st3160023as.

Thanks

---

### Post by stchman on 2007-04-09
bump.  Anyone?

---

### Post by h0ax on 2007-05-02
Hey sorry no one has responded to your request.

I am working on a GX280 - and if you're having trouble getting ubuntu to see it
(you shouldn't if you have the latest version 7.04 compiled kernel includes support for SATA)

as a last ditch effort - you could change the way the BIOS presents the SATA disk
go into the bios for the machine and change the SATA operation from normal to the alternative.  it may degrade performance, but it will probably be visible

---

