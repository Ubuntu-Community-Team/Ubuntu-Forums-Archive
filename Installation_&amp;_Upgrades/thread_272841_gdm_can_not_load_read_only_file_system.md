---
title: "gdm can not load: read only file system"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by olaf_noehring on 2006-10-07
Hi

after updating Ubuntu I can not load GDM anymore.
I set ubuntu to autologin myself, but GDM does not load.
I have seen the error message which looks like this:

> /etc/gdm/Xsession: Beginning session setup ...
mkdtemp: private socket dir: read-only file system

Starting in recovery mode does not help either - same problem.

Well, I am a newbie to Linux so I can not use Ubuntu anymore ... without anyone here helping me.

Olaf

---

### Post by pay on 2006-10-07
I'm not sure how much I can help but can you post your /etc/fstab file?

---

### Post by olaf_noehring on 2006-10-07
Hi

well - how do I display the file?
I can change to the /etc directory, but trying "edit fstab" the system tells me "read only file system" ....
Is my root file system read only?
Olaf

---

### Post by pay on 2006-10-07
```
sudo nano /etc/fstab
```
And yes the root file system is read only to anyone other than the root. Using sudo makes you the root.

---

### Post by olaf_noehring on 2006-10-08
Hi

well, strange things happen: I tried to start Ubuntu - it did some corrections while booting with the file system, rebooted - and - now I am back in GDM.
Nevertheless, since this happens more often, I would like to figure out why this happens.
Here is my
/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /60gb           ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       /tausch         ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Olaf

---

### Post by pay on 2006-10-08
I'm no expert but the lines 
/dev/hdb1 /60gb ntfs defaults,nls=utf8,umask=007,gid=46 0 $/dev/hda6 /home ext3 defaults 0 2
and
/dev/hda1 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 $/dev/hda7 none swap sw 0 0
Don't look set up properly. Why does it have the extra options after <pass>:confused: Maybe someone else with more knowledge can shed some light. Sorry I couldn't be more helpful.

---

