---
title: "Cannot access documents from Windows 7 partition"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-10-05
For some reason, when I try to access my NTFS partition that has Windows 7 and my Documents folder in Beta, I cannot. I can open the folder but nothing is there. 

Any ideas?

thanks,

---

### Post by Reiger on 2009-10-05
In order of increasing likelihood & assuming you have Karmic beta installed (i.e. it's not a live CD environment you are having problems with):

(1) You inadvertently wiped the partition, e.g. you opted to format the drive during installation.
(2) You set up Windows 7 to use encryption on the partition which Ubuntu is unaware of. As a result the partition cannot be read.
(3) You have chosen to mount the NTFS volume with root:root as owner (used e.g. /windows as mount point) : your premissions do not work out. I.e. if you do that with your music library you will be unable to play music using e.g. mpd from the location directly. If it is only one folder, you may be able to fix that using a symbolic link from your home directory to the windows 7 drive (ln -sT /windows/7/partition/folder ~/win7docs). Alternatively sudo chown -R <user_name>:<user_name> /windows/7/partition/folder will transfer ownership of the folder from root to you.

---

### Post by psyke83 on 2009-10-05
> **Reiger said:**
> 
(3) You have chosen to mount the NTFS volume with root:root as owner (used e.g. /windows as mount point) : your premissions do not work out. I.e. if you do that with your music library you will be unable to play music using e.g. mpd from the location directly. If it is only one folder, you may be able to fix that using a symbolic link from your home directory to the windows 7 drive (ln -sT /windows/7/partition/folder ~/win7docs). Alternatively sudo chown -R <user_name>:<user_name> /windows/7/partition/folder will transfer ownership of the folder from root to you.

It's not a good idea to mess with permissions on NTFS volumes, especially system volumes.

bridgetothesun,

Can you see any files on the Windows 7 partition? I suspect you're trying to look inside the equivalent of "C:\Documents and Settings\$YourUser", but it's only a symlink in Windows 7 and Vista. Your documents are really located in C:\Users\$YourUser\Documents.

---

### Post by MacUntu on 2009-10-06
> **psyke83 said:**
> Can you see any files on the Windows 7 partition? I suspect you're trying to look inside the equivalent of "C:\Documents and Settings\$YourUser", but it's only a symlink in Windows 7 and Vista. Your documents are really located in C:\Users\$YourUser\Documents.

+1

A buddy recently asked me the same question and that was exactly what he tried to do.

---

### Post by JessicaD on 2009-10-07
Bridgetothesun,
Microsoft does have an official Windows 7 Support Forum located here <Beep> . It is supported by product specialists as well as engineers and support teams. You may want to also check the threads available there for additional assistance and feedback regarding this particular issue.
Jessica
Microsoft Windows Client Team

---

### Post by bridgetothesun on 2009-10-08
Wow, wasn't expecting that reply. Thanks Jessica.

I checked the encyptions on the drives, and there is none. 

Funny thing is is that I can see all the files and folders in the other sections of my windows partition in Ubuntu, I just can see anything in the Documents and Settings folder.

Could this have something to do with permissions?

---

### Post by Aearenda on 2009-10-08
Just in case you missed, it, are you sure you are looking in the right place, as psyke83 has pointed out?
> I suspect you're trying to look inside the equivalent of "C:\Documents and Settings\$YourUser", but it's only a symlink in Windows 7 and Vista. **Your documents are really located in C:\Users\$YourUser\Documents**.

---

### Post by bridgetothesun on 2009-10-08
Yeap, found em. Why is it so confusing? Even in the Users folder there was a "My documents" folder and a "Documents" folder. Ridiculous. Or maybe there is a purpose?

---

### Post by hikaricore on 2009-10-08
After many years Mickysoft discoverd the joys of symlinking, and they @&%#ed it up. :p

---

### Post by seeker5528 on 2009-10-09
> **bridgetothesun said:**
> Yeap, found em. Why is it so confusing? Even in the Users folder there was a "My documents" folder and a "Documents" folder. Ridiculous. Or maybe there is a purpose?

If you view these while you are in Windows using explorer, it shows you they are links. Permissions on them are set so they are not user accessible, even when you right click the launcher for explorer and choose 'Run as administrator', because MS doesn't want you to use them, they are only there to provide backward compatibility for older software.

Normally when using NTFS-3g to access NTFS from Linux, permissions are not an issue because NTFS-3G is normally set up in a way that gives you full access, so I would guess if it is not following the symlinks in Karmic it is probably because the ability to do so is a recent addition to NTFS-3G and the version in Karmic is not new enough.

When I use [RIP](http://rip.7bf.de/current/) to do clean up, hunt for suspicious files, etc... it does follow these symlinks, but I think it is often using pre-release versions of NTFS-3G.

Later, Seeker

---

