---
title: "mounting NTFS drive"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by da_unruled on 2005-07-26
I just formatted my win comp and made it into a dualboot machine with winxp pro and ubuntu.

Now I have read that I can mount the NTFS partition as read only, and I want to do so.
the starter guide (unofficial), says:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
now, hda1 in my case, IS the ntfs partition, so thats all good.
however, when I add that line to the fstab, nothing happens on boot. Its not mounted.

when I go to the manually mounting part to try and do it myself:
> unruled@unruled:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
unruled@unruled:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
unruled@unruled:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /media/windows
unruled@unruled:~$
however, when I go to look at 'places, computer', its not there.
Before, I dont remember exactly where it told me to check something, and then it said something about not understanding the 0222 part.

Sorry guys..Im a noob in help  :-#  :|

---

### Post by ubuntp on 2005-07-26
Have you checked in /media/windows? It may not appear in Places -> Computer.

---

### Post by da_unruled on 2005-07-26
[QUOTE=ubuntp]Have you checked in /media/windows? It may not appear in Places -> Computer.[/QUOTE]
sorry.... I feel stupid now  ](*,) 

I did applications->run app-> /media/windows and then it popped up.
Is there  a way to show it in places computer though?

thanks a lot for the quick reply :-P

edit: or to make  a shortcut to it on the desktop

---

### Post by ubuntp on 2005-07-27
right click on the desktop, click create launcher. then choose type directory, enter /media/windows in the URL field and that's it.

---

### Post by da_unruled on 2005-07-27
[QUOTE=ubuntp]right click on the desktop, click create launcher. then choose type directory, enter /media/windows in the URL field and that's it.[/QUOTE]
 alright, thanks. I will try that once I get back to linux (since I just formatted Im busy re-configging winxp).

edit: okay, its fine now. Thanks again.

---

