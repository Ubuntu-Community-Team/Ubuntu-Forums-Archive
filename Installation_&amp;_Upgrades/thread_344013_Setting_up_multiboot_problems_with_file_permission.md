---
title: "Setting up multiboot problems with file permissions"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by macogw on 2007-01-22
By not paying attention, I formatted /dev/sda instead of /dev/sdb, but now I'm taking it as an opportunity to set up a weird mutliboot configuration.  One problem remains.  The distros are fighting over who gets permissions on /home.  I *could* make a different username on each and then have file permissions issues between all the different /home/me1 /home/me2 etc, but I want to avoid that (besides that it'd still mean knowing which distro I was in when I saved something).  I would like them all to share the same home drive then (not just the partition), but I get errors in both Fedora and Ubuntu (haven't set any others up yet) regarding permissions on ~/.dmrc and how they have to be 644.  I keep setting them to that, but it seems if I tell Ubuntu to use those permissions, it breaks Fedora and vice versa.  Does anyone know a way around this?  I don't want to have to have multiple home drives.

---

### Post by kidders on 2007-01-22
Hi there,

It looks like you've already taken the first step ... tweaking /etc/fstab on all your distros to make /home the same on them all. The thing you might have forgotten is to sync the UIDs.

In Linux, your username is fairly irrelevant ... when you own something, it's a number (ie not a name) that's stored on the filesystem, to record that fact.  To make life easier in dual boot environments, you should try to ensure that these UID numbers are all (or at least mostly!) the same on all operating systems.

In your case, macogw on Ubuntu probably has a different UID than macogw on Fedora. Say, for argument's sake the UIDs are Ubuntu = 1001 and Fedora = 1000. In the best case scenario, files you own in Ubuntu will not map successfully to a valid user in Fedora, so when you type **ls -l ~**, you see "1001" where your username should be. In the worst case, your Ubuntu UID *does* map to a Fedora user ... say maybe your cron or www-data user ... which has security implications.

To fix things, choose one OS, and make it the "boss". Sync your users' UIDs manually on all other OSs with it, and chown any affected files, to re-map ownership to the new UID numbers. Once you're used to the way things operate, you can try a more permanent (clever) approach ... such as sharing parts of /etc between all your Linuxes. That way, whenever you create (or modify) users, the changes would affect all platforms the same way.

I hope that helps.

---

