---
title: "Xubuntu noobie"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by r6mile on 2006-10-18
I have just installed Xubuntu (before I had Ubuntu) on my Pentium III 450, 384 MB RAM. Everything goes fine, I just love Xfce and everything. But there are some things I still don't know how to do.

How can you enter a Windows Workgroup and have access to the shared folders of other Windows PC's in the workgroup? I know you could do that with Ubuntu.

How can you install a printer? My printer is an Epson Stylus Photo 890, and the printer driver I actually have, gutenprint, supports it. Is there an "add printer" menu in Xubuntu?

I have just installed Wine. Where can I access it from?

If I have any more doubts I will post them here

---

### Post by mssever on 2006-10-18
To admin printers, open up a web browser and go to [http://localhost:631](http://localhost:631).

After installing wine, you need to type winecfg. Then, to run a program under wine, cd to the program's directory and type ```
wine programname &
```It's best to post unrelated questions in different threads, using descriptive titles, so that those who know how to answer the question can more easily find it.

---

### Post by K.Mandla on 2006-10-19
For a printer, I usually install gnome-cups-manager, which will give you the same printer interface as in Gnome (Ubuntu).

You should have a "Shared folders" option under Applications > System. Otherwise, you might look for [a howto on Samba]("http://www.ubuntuforums.org/showthread.php?t=202605").

Perhaps you already saw the wiki page about Wine.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

