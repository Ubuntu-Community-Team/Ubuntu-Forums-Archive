---
title: "Synchronizing two Ubuntu installs"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by ugopozo on 2007-01-05
I have a fully functional Ubuntu installation on a virtual machine running under Windows. I want to take this installation and make it dual boot with Windows in the same machine. I thought of two approaches to accomplish that:

1) Hard-copy (possibly using dd) the virtual machine hard disk to the new partition on the real disk drive, and deal with possible (and probable) hardware conflicts after booting Ubuntu for real;

2) Install a fresh Ubuntu on the new partition, copy my home directory and install all extra packages after that.

For each approach, I can think of some problems. Copying the hard disk makes me unsure about how to make this new partition bootable, and it's possible that video card, sound card, CD drive and Ethernet card conflicts makes the system virtually unbootable.Not to mention that I have installed VMWare tools on that machine, so it's specifically tuned to be runned as a VMWare guest.

On the other hand, a new fresh install would require me to locate each and every "system" file I have ever modified (sources.list, httpd.conf etc.) and manually copy them after installing the new system. And I also would have to identify all the packages I have installed on the virtual machine to install them again on the real partition.

Which way do you suggest I go? Which one seems less trouble to you, locating and copying tons of files I don't even remember to the new partition or manually solving hardware conflicts?

**Or, better, is there a way to "synchronize" the packages from the original installation with the new one?** I mean, some tool that identify all the installed packages on the old installation, downloads them on the new one and installs them?

Thank you all in advance.

---

### Post by jkzubu on 2007-01-05
Do the fresh install.  A proper install will place the necessary files in the MBR - master boot record portion of the hard disk.  This is necessary for proper boot. Easy.

You are correct - copy the /home directory as you stated.  Also copy the /usr directory to the new install.  The /usr directory should contain all of the applications, manuals and etc.  It may help that you read a bit more about the contents of each of these directories.

---

### Post by ugopozo on 2007-01-05
Thank you for your prompt reply.

One question, though. If I copy my /usr directory to get all my apps, won't I break a lot of dependency rules on the package manager?

---

