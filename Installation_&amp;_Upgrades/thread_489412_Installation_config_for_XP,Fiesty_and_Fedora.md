---
title: "Installation config for XP,Fiesty and Fedora"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by lancest on 2007-07-01
I previously had Xp and Feisty on this PC. Then I went and installed Fedora 7.  All three systems show in boot menu but
Feisty no longer boots . How should the boot configuration work?

---

### Post by confused57 on 2007-07-01
> **lancest said:**
> I previously had Xp and Feisty on this PC. Then I went and installed Fedora 7.  All three systems show in boot menu but
Feisty no longer boots . How should the boot configuration work?
Here's how to reinstall Feisty's grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Here's how to boot multiple linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You should be able to use a configfile entry to boot Fedora...

What sort of errors are you receiving when you try to boot Feisty...it's possible the UUID of a partition filesystem has changed that Feisty is set to mount at boot(usually you'll get a press ctrl+d to continue):
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

Added:  Found this thread...see the reply by bodhi.zazen...this may be all you need to do:
[http://ubuntuforums.org/showthread.php?t=489415](http://ubuntuforums.org/showthread.php?t=489415)

---

