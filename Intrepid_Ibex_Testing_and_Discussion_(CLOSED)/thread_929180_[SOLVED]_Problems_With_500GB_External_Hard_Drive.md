---
title: "[SOLVED] Problems With 500GB External Hard Drive"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-24
I have a USB external hard drive that I thought was working fine, but it seems to be mounted as root. Whenever I try to run Unison, Unison can't do anything because of the permissions. The folders are set to root ownership. Even if I chmod or chown the files on the drive, all the new folders are created under root ownership.

This drive won't be connected to my computer all the time, only when it's being used. (About once a week or so). For that reason I don't want to add it to fstab because that would be unnecessary for something that's only attached once in a while.

Do you guys know a way around this so I can back up my files?

---

### Post by andrewabc on 2008-09-24
Are you using it to only/mostly to backup data?
what program are you using to do so?

Might I suggest trying [rsync](http://rsync.samba.org/resources.html) with possibly [grsync](http://www.opbyte.it/grsync/)?
I tried them and it seemed to work good for backing up files. You could set it up to easily backup directories and stuff.

But I don't think they will solve your permissions problem :(

---

### Post by alphacrucis2 on 2008-09-24
> **andrewabc said:**
> Are you using it to only/mostly to backup data?
what program are you using to do so?

Might I suggest trying [rsync](http://rsync.samba.org/resources.html) with possibly [grsync](http://www.opbyte.it/grsync/)?
I tried them and it seemed to work good for backing up files. You could set it up to easily backup directories and stuff.

But I don't think they will solve your permissions problem :(

Looks like he said he is using Unison to do his backups

---

### Post by andrewabc on 2008-09-24
> **alphacrucis2 said:**
> Looks like he said he is using Unison to do his backups

Oh sorry, I had no idea what that was :P
I figured it was some program that was on the hard drive.

Gonna look at that program now. :)

---

### Post by alphacrucis2 on 2008-09-24
> **andrewabc said:**
> Oh sorry, I had no idea what that was :P
I figured it was some program that was on the hard drive.

Gonna look at that program now. :)

Yeah I only knew about it because I was reading about it around an hour ago. Seems like there is a Windows version of it too which could be useful for backing up between Linux and Windows. As far as the OP's original problem, I thought of a dirty workaround. He could reformat the external USB drive as vfat/fat32 which IIRC doesn't support file permissions:lolflag:.

---

### Post by jlacroix on 2008-09-24
Yes, it is Unison. 

The problem isn't Unison itself, if I go into the file manager and try to create folders they're created under root. Everything already there is mounted in the file manager as root as well.

Also yes, this drive is used ONLY for backups. The drive is formatted as NTFS because I need large file support under Windows (40+ GB hard drive images).

---

### Post by jlacroix on 2008-09-24
Here is the error code I get:

> Failed to set permissions of file /media/Backup/jeremy-desktop/Backup/.unison.CD Images.8bf06d936549f322b5bd477bf31a4137.unison.tmp/Linux/Ubuntu to rwxr-xr-x: the permissions was set to rwxrwxrwx instead. The filesystem probably does not support all permission bits. You should probably set the "perms" option to 0o1755 (or to 0 if you don't need to synchronize permissions).

You know what? It totally dawned on me that (duh) of course it's a problem with permissions since NTFS is stupid and doesn't understand permissions of copied files from Linux.

The one outstanding confusing thing I need help with is why the files are mounted as root. It is letting me read and write to the drive just fine, but either I never noticed that root mounts external drives or its a bug.

---

### Post by BwackNinja on 2008-09-24
I'd say the whole thing about it being mounted as root while still allowing you to do stuff is just a byproduct of it being NTFS. NTFS lacks both permissions and file ownership, so the owner not being set probably just defaults to root.

---

### Post by jlacroix on 2008-09-24
> **BwackNinja said:**
> I'd say the whole thing about it being mounted as root while still allowing you to do stuff is just a byproduct of it being NTFS. NTFS lacks both permissions and file ownership, so the owner not being set probably just defaults to root.

That makes sense. Thanks to all, I think I got it sorted out.

Once you get the hang of it, Unison is pretty darn swell!

---

