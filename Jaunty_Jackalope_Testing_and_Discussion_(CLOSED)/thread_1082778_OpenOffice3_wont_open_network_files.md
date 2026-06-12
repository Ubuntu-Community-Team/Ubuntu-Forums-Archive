---
title: "OpenOffice3 wont open network files"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by old_salt on 2009-02-28
Been playing around with Oo3 on various other distros and have learned that under Jaunty, Oo3 will not open a document over the network. The file must first be copied locally to the system before it will open the file. 

There is no mention of this issue on the Oo3 forums nor does this issue occur with any other distro (Suse, Fedora).

My test was against both Microsoft and Linux Samba shares.

Any feedback would be appreciated.

Thanks
T

:confused:

---

### Post by The Cog on 2009-02-28
I noticed that on 8.10. I can't think why it should be. 
Maybe it's trying to do a windows thing and get a write lock on the file? Just guessing.

---

### Post by cariboo on 2009-02-28
OpenOffice3 will open files on my server. To edit the document, once it is open, I have to right-click and select Edit. The document is just on a regular samba share.

Jim

---

### Post by nanog on 2009-02-28
oops -- reading comprehension skills lacking.

---

### Post by nanog on 2009-02-28
samba works but even if properly configured it has problems with permissions. i switched to NFS. its seemless and blows every file/volume share system out of the water.

---

### Post by albinootje on 2009-02-28
> **old_salt said:**
> 
My test was against both Microsoft and Linux Samba shares.

For me OpenOffice never managed to open files through Nautilus, or through Konqueror. The same with OpenOffice trying to open files on a webdav share through Konqueror afair.

If you manually mount the samba share with the mount command on the command line or through /etc/fstab, or use autofs + cifs, then OpenOffice should have no problems.

---

### Post by albinootje on 2009-02-28
> **nanog said:**
> samba works but even if properly configured it has problems with permissions. i switched to NFS. its seemless and blows every file/volume share system out of the water.

NFS works, it's fast and easy to set up, but it is primitive, not secure at all, and you will likely have permission problems when two or more users need to write to the same "share", even when you decide to use (the  very ugly solution to chmod) 777 for all files and directories with a setgid parent directory.

I only use NFS for /home for my users, and Samba for their shared files. Samba is very good for a "multi-user read/write share".

---

### Post by old_salt on 2009-03-01
Anyone have any ideas how to get this looked at? The OOo devs will claim the issue is specific to E/K/Ubuntu and to proceed that route having no reports from any other flavor. It was an issue for me as well when I put OO3 on my Kubuntu 8.10. 


cariboo907 - At least the document opens for you. It doesn't for The Cog and I for starters. I also tested on my network at home and no go. As an Admin in both places, I don't think it's permission related. 

albinootje - I've never had problems with opening office documents from local or network locations (Samba/Windows) with previous versions of Open Office. Dolphin, Konqueror and Nautilus all had no problems. As for nfs, that's not an option on a Windows 2008 Domain. 

I'm open to suggestions.

---

### Post by albinootje on 2009-03-01
> **old_salt said:**
> I've never had problems with opening office documents from local or network locations (Samba/Windows) with previous versions of Open Office. Dolphin, Konqueror and Nautilus all had no problems.
Perhaps I should have been more clear.
I have seen problems in the past with OpenOffice in Nautilus and Konqueror when you would use Nautilus and Konqueror to open the Samba-share. That includes the "Connect to Server" in Gnome in Ubuntu.
I've just tested it on Ubuntu 8.04 with both Nautilus and Konqueror, and OpenOffice 2.4 opens documents from the Samba-share without problems.
In the past OpenOffice would ask for some password, and then it would always fail to open the document.
Glad to see that this is apparently solved now.

---

### Post by bgriggs75 on 2009-03-05
I had this problem also with OOO 3.0.  I downgraded to 2.4 to fix the problem, but now am having the same problem with 2.4 on Ubuntu 8.10

---

### Post by yther on 2009-03-05
The problem is not peculiar to Jaunty, or even to Ubuntu.  I think that OOo relies on the OS to deal with filesystems, including networked ones.  Notice that you can't browse to a random Samba share using the *native* OpenOffice file picker, but you can using a KDE or Gnome one—however, OOo will give an error when trying to actually open or save the file there.

To solve this, you need to mount the share into your system somewhere.  Check [**dmizer**'s guide]("http://ubuntuforums.org/showthread.php?t=288534") for some good information on how to do that, and note that "_netdev" and "nobrl" may be good options to add.

Once that is done, all applications will be able to access those files transparently.

---

### Post by bgriggs75 on 2009-03-05
Thanks for the reply!  Too many commands for me, though.  I'll just use to copy-to-desktop-for-edit option until Ubuntu makes it easier.

---

### Post by calc on 2009-03-17
> **old_salt said:**
> Been playing around with Oo3 on various other distros and have learned that under Jaunty, Oo3 will not open a document over the network. The file must first be copied locally to the system before it will open the file. 

There is no mention of this issue on the Oo3 forums nor does this issue occur with any other distro (Suse, Fedora).

My test was against both Microsoft and Linux Samba shares.

This should have shown up on other ooo-build (non-Fedora) linux systems using OOo 3.0.1. It appears to be some sort of bug in ooo-build gnome-vfs support and I have already filed a bug report about it. Fedora uses gio instead of gnome-vfs so probably should work, gio does not work under ooo-build due to unknown reasons and the bug has already been filed about that issue as well.

To solve the problem for Jaunty I decided to turn off both gnome-vfs and gio support in Ubuntu OOo and use Gnome gvfs fuse which looks like part of the normal filesystem to OOo. There were still several bugs in gvfs fuse support but the most annoying issues have been resolved by gvfs 1.1.8 which is now in Jaunty. There is more information about the issue and links to the relevant bug reports at my blog link below.

[http://chrischeney.wordpress.com/2009/03/13/ubuntu-openofficeorg-using-gvfs-fuse-now/]("http://chrischeney.wordpress.com/2009/03/13/ubuntu-openofficeorg-using-gvfs-fuse-now/")

---

