---
title: "How can I reinstall Gnone et al from a CD at the command line?"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by ariane5 on 2010-05-22
Re Ubuntu 10.4 - I wanted to reinstall gvfs to fix a network share missing problem and, like a complete noob, I didn't pay attention to the vast list of very important dependencies which were also going to be uninstalled and am now left without Gnome!

I am at the command line, with no networking. I have my own router here which normally works fine - but DHCP seems to not want to play either, and have the Live CD in the drive.

I have tried reinstalling gdm with apt-get but it keeps trying to get the packages from the online repository and I need to get them from the CD.

I tried manually going to the CD, tried to edit my sources.lst with nano (the file ie empty)....and am at a loss now.

I've been trying to fix this for two days and am getting to the stage now where I can't think straight any more from panic....

I also tried Ext2IFS to mount the drives in Windows but mountdiag.exe said they were invalid drives. There is nothing wrong with the drive - I can see my Ubuntu directory structure fine with ls.

I know it's a simple solution - but I can't figure it out. Any help would be hugely appreciated.

EDIT - Could I install gdm to my Ubuntu from the LiveCD desktop - by telling it where to install?

---

### Post by mikewhatever on 2010-05-22
Try the following:

sudo apt-cdrom add

sudo apt-get update

sudo apt-get install ubuntu-desktop

These, if successful, will bring back the default Ubuntu installation.

---

### Post by ariane5 on 2010-05-22
Thanks mikewhatever - I tried it and it is still trying to get the package from the online repository. I think I'm just going to do a clean reinstall. I managed to get my partition mounted in the LiveCD (it wouldn't mount yesterday) and copied my important files over to my Winblows partition.

EDIT I reinstalled. Would have loved to have been able to persevere and fix the previous mess though - just no time left.

---

