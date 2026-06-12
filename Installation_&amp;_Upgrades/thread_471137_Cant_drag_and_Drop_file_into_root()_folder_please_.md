---
title: "Cant drag and Drop file into root(/) folder please help!!!"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by azndreamer781 on 2007-06-11
i need help really nadly i have a 6.06 edubuntu computer and i cant seem to drag and drop and file in to the folder inside the root(/) folder, a window will pop up givin me a you dont have the permission error. how can i fix this problem and o yea im the only user of this computer( only 1 login) thanx

---

### Post by merlinus on 2007-06-11
I think the easiest thing, although probably not the most secure, is to log in as root and change the permissions.

But more to the point:

Why do you need to place files in the /root folder in the first place?

-merlin

---

### Post by One Quick Question on 2007-06-11
/ is owned by the superuser, which you are not.  You can always use `sudo mv ...` or `sudo cp ...`, but if you want to drop and drag from /, you'll need to start your file browser with superuser permissions.
`kdesu konqueror /` would work on KDE.   To be honest, I don't know how to do it on Gnome, I suspect it would be `sudo nautilus /` or something.  Don't quote me on that.

Actually, now that I re-read your post, a better solution would be to give yourself permission to use that folder. `chown azndreamer781 /folder` would do that.   But it's not proper to do that for important folders, like /bin or /etc ... or ...basically any of the system folders that reside in /.    I hope you're not messing with the hierarchy, are you?

---

### Post by azndreamer781 on 2007-06-11
i got mame and i want to install some skin and plugin for other software.

none of the konquer or ur crown thing work. is operation is not permitted

---

### Post by azndreamer781 on 2007-06-11
i have try everythin i still cant get it to work do you guys have anymore idea??

---

### Post by jjross on 2007-06-11
sudo nautilus will work but an easier way is to install the Nautilus Scripts from Automatix

---

