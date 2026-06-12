---
title: "Remove Kubuntu, reinstall Ubuntu"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by racsw on 2006-10-14
Hi,
  I made the mistake of trying Kubuntu, which I didn't like, and now I can't get rid of it.  I've tried command line, Synaptic, you name it.
I have a simple request.  Can someone tell me how to completely get rid of Kubuntu, **including** the Kubuntu startup screen and login, and get Ubuntu back to normal?

Also, in Ubuntu, I can't figure out how to bypass the login screen.  I think I did it before, but I must be having a senior moment.

Thanks,
Robert

---

### Post by taurus on 2006-10-14
Try

```
sudo aptitude kubuntu-desktop
(assuming you used aptitude to install it before...)
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by racsw on 2006-10-14
I uninstalled, reinstalled, uninstalled again, using both apt-get and synaptic.  I have not used aptitude.

I don't see an aptitude command on your first line.

Regards,
Robert

---

### Post by taurus on 2006-10-14
Oops.  Sorry not to include "remove" in there...

```
sudo aptitude remove kubuntu-desktop
```

---

### Post by racsw on 2006-10-14
It's not as simple as that...
I have removed the Kubuntu Desktop, and all KDE using both apt-get and Synaptic, yet when I start the computer, the Kubuntu logo comes onscreen while it scrolls down through the system booting process, and then I get to the KDE login screen.
  I can't get rid of either one.

I can still use Ubuntu, but I have to select it from the menu on the KDE login screen.
I have both the KDE window manager and the GDM window manager running.

Robert

---

### Post by racsw on 2006-10-14
Said one thing incorrectly.
The login screen says " Welcome to Kubuntu robert-desktop"
So Kubuntu is still lurking on my system.

Robert

---

### Post by taurus on 2006-10-14
You only need either kdm or gdm.  You don't need both to run.  Therefore, remove the kdm then...  And your other question has to do with splash screen...  There is a command to get it back to default but I am kind of brain dead right now so need to look around!!!

---

