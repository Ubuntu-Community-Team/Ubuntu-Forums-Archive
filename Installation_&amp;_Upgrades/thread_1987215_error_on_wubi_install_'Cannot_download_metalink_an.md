---
title: "error on wubi install 'Cannot download metalink and therefore ISO'"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by carsten888 on 2012-05-26
On a win7 pc I installed ubuntu before (via windows), but kept having trouble with the brightness of the screen, nearly pitch black (see this thread [http://ubuntuforums.org/showthread.php?p=11951760](http://ubuntuforums.org/showthread.php?p=11951760)). So I tried a reinstall. In windows I uninstalled ubuntu. When I clicked wubi, first there was a message some Kubuntu install needed to be cleaned up, so I click 'ok' to clean that up, then the wubi install options. 

when try to run wubi I get this:
[IMG]http://www.engelweb.nl/images_online/wubi.jpg[/IMG]

I can not install from cd because the screen turns almost pitch black so I can not see what I'm doing. Thats why I'm trying to instal via wubi.

I have searched this forum and checked for that log file, but can not find it.

---

### Post by bcbc on 2012-05-26
This is a bug ([lpbug]1004173[/lpbug]. Unfortunately the ISOs for Kubuntu were changed and the Wubi installer wasn't updated. The only way to install Kubuntu with Wubi right now is to:
1. Download the Kubuntu Desktop ISO from here: [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)
2. Place it in the same folder as Wubi.exe before running wubi.

---

### Post by Paul.E.T on 2012-05-26
I believe the Wubi install has some issues, ck out the comment on "cmov" needed.  I just tried Wubi install and now have a dead PC,a frozen keyboard leaded to hard reboot now no boot black screen of death.  It's an AMD Athlon XP 3200.  I've got lots of genealogy data on second HDD there and years of work.  I do have backup but it will be no fun trying to rebuild.  I'll be trying to use the Win XP install disk to get to see if it will boot after a live linux look-see.  No More Fun :>(

I started a new thread "Wubi 12.04 install sys crashed" per advice of bcbc below.

---

### Post by bcbc on 2012-05-26
> **Paul.E.T said:**
> I believe the Wubi install has some issues, ck out the comment on "cmov" needed.  I just tried Wubi install and now have a dead PC,a frozen keyboard leaded to hard reboot now no boot black screen of death.  It's an AMD Athlon XP 3200.  I've got lots of genealogy data on second HDD there and years of work.  I do have backup but it will be no fun trying to rebuild.  I'll be trying to use the Win XP install disk to get to see if it will boot after a live linux look-see.  No More Fun :>(
You don't need to hard reboot. If you look in the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide#Warning") it states up front that this is dangerous (in fact it can damage any filessystem). Use Alt+SysRq R-E-I-S-U-B instead.

If you want to recover data from your install, use ext2read or a live CD) e.g. see here [http://ubuntuforums.org/showpost.php?p=11944482&postcount=1040](http://ubuntuforums.org/showpost.php?p=11944482&postcount=1040)

PS in future create your own support thread.

---

### Post by carsten888 on 2012-05-27
> **bcbc said:**
> This is a bug ([lpbug]1004173[/lpbug]. Unfortunately the ISOs for Kubuntu were changed and the Wubi installer wasn't updated. The only way to install Kubuntu with Wubi right now is to:
1. Download the Kubuntu Desktop ISO from here: [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)
2. Place it in the same folder as Wubi.exe before running wubi.
Thank you very much,that made it work. Got it installed. :)

(now the next issue is that the brightness is so low I have to use a torch to see what is on the screen, but I will use another thread for that)

---

