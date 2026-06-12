---
title: "[SOLVED] restoring /usr/lib"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2007-03-04
Hi All,

Don't ask, but I removed all the files in /usr/lib trying to fix an upgrade to firefox.

I'm trying to find a way to restore these without re-installing.  The only thing working right now is dpkg, but I can't see man pages, etc to see if it will work to re-install all the packages that were installed.  Any ideas using dpkg?

apt-get is missing a library, so that won't work.

Is there someway to suck most of these libraries off of the install cd?  That may at least get apt-get working and I can go on from there.

Also, if I do re-install how do I keep /home as it is?  I seem to remember that the installer makes you reformat all file systems.  Anyway around this?  I have almost everything backed up, but can't get ssh or rsync to work since they're missing libraries, too!

HELP!!:lolflag:

---

### Post by kidders on 2007-03-05
Hi there,

Oh no! I just answered a thread by a guy who accidentally chmod-ed his entire /usr. I thought *that* was unlucky ... this is worse. :-(

Linux systems tend to arrange files according to purpose, rather than origin, making it very complicated to solve an issue like this. On top of that, /lib, /usr/lib and usr/local/lib are sort of special, in that they tend to contain intricate structures of symlinks. In order to be sure you had everything back the way it's supposed to be, you would have to reinstall every application on your system, in the correct order. Reinstalling the OS would ... well ... it would just be easier.

> **DantePasquale said:**
> if I do re-install how do I keep /home as it is?That depends on where it is. If your /home is on a separate partition (which many users do to save themselves from accidents like this), you don't have to do anything. Once the reinstallation is complete, you can simply tweak your /etc/fstab to put /home back where it should be, and you're done.

Alternatively, you may have some unallocated free space on one of your hard disks, that you can use to temporarily store /home, while you reinstall Ubuntu.

---

### Post by DantePasquale on 2007-03-05
Hi, I figured re-install would be the way to go.

Is there a file or something I can extract to feed into synaptic, or apt-get to re-install all the software I've added on top the o/s?  That would make my life easier.

BTW, I do have a backup, but it's 500 miles away and no one is there, so it's not doing me any good!

Dante

---

### Post by kidders on 2007-03-05
> **DantePasquale said:**
> Is there a file or something I can extract to feed into synaptic, or apt-get to re-install all the software I've added on top the o/s?

I've never needed to do that before, but it looks as though /var/lib/dpkg/status might be able to help. You could probably manipulate the contents of that file into one humungous "apt-get install" command, to return your system to its original state, after reinstalling.

---

