---
title: "X &amp; File permissions [AKA a lot of trouble]"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Tobi Vollebregt on 2005-04-18
I got myself in a _lot_ of trouble today, the only thing I was trying to do is to combine my /home (reiserfs) partition with the next (fat32) partition. So I booted a live cd cp -R 'ed all my stuff to a temporary folder in / (my HD root of course). Unmounted the harddisk partitions. Deleted the /home partition and the fat32 partition and created a new one in the free space using fdisk. After writing the table it said I should reboot because the kernel might be confused, so I did that -- into the Live Cd again. Changed /etc/fstabs of my HD partition and rebooted again...

Now the trouble began, as grub gave me an "Error 22". Booted into the Live Cd again, finally found out how to reinstall grub:
sudo grub-install gave an error: couldn't read /boot/grub/stage1

I asked on #ubuntu: I should manually reinstall grub. So I typed:
grub
grub> root(hd0,6)
grub> setup(hd0)
grub> quit

This solved part 1  :wink:  now onto part 2.
So grub was fixed and Linux boots up fine (note that I cp -R'ed my stuff back to the new /home partition). Only when I log into X the trouble starts. I could fix the first problem by sudo chown -R tobi tobi, but now I'm getting the following error when starting Gnome (also in Failsafe):

> GConf error: No database available to save your configuration: Unable to store a value at key '/apps/nautilus/preferences_version', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

I suppose it has something to do with file permissions or so. I realise I should have tried harder to keep them (instead of cp -R).

Does someone know how to fix this (the file permissions probably) ??
Or would it be easier to do a clean install? I only installed a few days ago and I still remember which modifications I made. I might wipe out W98 in that case too  :smile:

---

### Post by diebels on 2005-04-18
Wild guess:
rm -rf ~/.gconf*

For another time it would be better to use "cp -a" or tar

---

### Post by Tobi Vollebregt on 2005-04-19
> rm -rf ~/.gconf*I'll try that if I am at home again. If that doesn't work then I'll probably do a clean install.

> For another time it would be better to use "cp -a" or tarHeh, I learned it the hard way :)

---

### Post by Tobi Vollebregt on 2005-04-19
Erm, this is weird I just booted up again after a night sleeping and some university stuff... and everything just works fine  :???:  I really don't understand how that is possible but it saves me some time at least  :) 

To continue on the permissions, all my /home files are now owned by myself and in group root, could someone check what's normal? Are /home files in root group normally?

---

### Post by diebels on 2005-04-21
My files are in a group with the same name as the user by default. It's up to you which groups you share files with, but group root is kind of pointless since root already has access to everyting. You can use chgrp -R ~/ to change it.

---

