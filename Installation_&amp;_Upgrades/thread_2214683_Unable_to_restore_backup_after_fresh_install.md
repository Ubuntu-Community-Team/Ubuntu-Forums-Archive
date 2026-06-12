---
title: "Unable to restore backup after fresh install"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by dubrewski on 2014-04-02
Sorry if this is a repeat, I couldnt find anything that answred my questions and Im sure its probably something extremly obvious.

On my laptop I have a dual boot with Vista and 12.04. Yesterday I did a backup of /home and stored it on my vista partition then reinstalled 12.04. When I open up the backup utility and chose the restore option I will either get "Restore failed, no items to restore" or a permission denined message. I have tired mulitiple duplicity commands in the terminal with no luck, I can see all the files there, I just dont know how to restore them. I also created a list of installed packages before I reinstalled and I am unable to use that to reinstall the packages. Any help is much appreciated.

---

### Post by dubrewski on 2014-04-06
I still have yet to figure out why I am unable to restore my backups. If anyone out there could at least give me a clue on what to do that would be great.

---

### Post by Mark Phelps on 2014-04-07
> Yesterday I did a backup of /home and stored it on my vista partition

I have done image backups of Linux installs and saved those to NTFS partitions -- and restored from the same. But that works because permissions on the backup image file don't matter.

NTFS does not understand, nor does it retain, Linux filesystem permissions.  When you copied the files from /home to your Vista NTFS partition, you effectively stripped away all the Linux filesystem permissions.  That's probably why you can't copy it back.

In future, if you're going to save a folder or files from Linux, you need to do that to a partition formatted with a Linux filesystem.

---

