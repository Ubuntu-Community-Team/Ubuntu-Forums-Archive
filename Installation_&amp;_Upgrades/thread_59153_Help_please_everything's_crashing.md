---
title: "Help please: everything's crashing"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by simoncullen on 2005-08-22
Hello Ubuntuers,

I've just installed the lates Hoary on my Centrino based laptop.  I was extremely impressed by the installation process which was totally painless.  

I would really like to get this working, but I've got a seemingly major problem: whenever I load an application from the desktop I get this message:

"[Enter relevant app name] has quit unexpectedly..."  Then I can choose to restart it.  Interestingly enough this isn't effecting things like Firefox, Evolution, Gimp, etc.  But when I try, for instance, to browse a harddisk from the desktop, or open an archive, it crashes with that error.

Any advice with this would be good.

Thanks,
Simon

---

### Post by jasmuz on 2005-08-22
Sounds to me like a Gnome related problem, you could try deleting your .gnome and .gnome2 directories in your /home directory.

---

### Post by simoncullen on 2005-08-22
Thanks,  I think it's Gnome related too.  I tried deleting the .gnome and .gnome2 directories.  It recreated them, and the problem persists...  Any more ideas?  

Thanks


Edit: I deleted my account and recreated it--everything's now okay.  Cheers

---

### Post by Thulemanden on 2005-09-12
Try finding out what the crashed appl. has in common - are the e.g. Gtk? 

You could try reinstall everything or do an upgrade as it might be som faulty libraries somewhere.

---

