---
title: "Karmic update crashed KDE (64bit)"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tuxolero on 2009-10-11
Hi there,

I am using Karmic since Alpha 5, up to now without any problems...

But since Friday evening's update, my KDE always crashes while trying to restore my saved session.
It looks like it happens while trying to start Konqueror.
When it crashes, I am logged out and returned to the login screen.

---

### Post by benerivo on 2009-10-11
You could try renaming at least part of the kde4 configuration files in your home directory, so that the next time it tries to load konqueror, it uses a brand new konqueror profile. After it crashes and you are taken to the login screen, do Ctrl+Alt+F1 and login to the command line. Then do...```
mv /home/ben/.kde4/share/apps/konqueror /home/ben/.kde4/share/apps/konquerorOLD
```Then do Ctrl+Atl+F7 to get back to the graphical login screen, and try again. If that fails, then i might just rename the parent .kde4 folder and accept losing all my kde4 setup and preferences (you never actually lose then as they still exist in the renamed folder, and can be restored later by renaming them).

---

### Post by tuxolero on 2009-10-11
Thanks for the reply.
Ctl-Alt-F1 does not work, it makes the **whole system** hang.
The only way to get to a text console is to start the system in recovery mode.
This way, I am doing an apt-get update / upgrade once or twice a day since the problem occured on Friday and hope I get a fix for it.

But with the recent updates it became even much worse:
The screen output is completely corrupted now.

So, I cannot even test your hints at the moment.

I will either have to reinstall or wait and hope for the next fixes.
I'm glad I still have Jaunty on a second partition, although I often stumble on the bugs in that KDE version...

---

### Post by benerivo on 2009-10-11
If you have jaunty on another partition, then you could try and access and change the karmic files from there, but it sounds pretty bad if the screen display is corrupted. You probably should rename your .kde folder for karmic, and then try again. It could be a plasma problem, or less likely a problem with the xserver. You might want to look in the /var/log/xorg.log (i think this is what it will be called), and see if there is anything about a crash.

---

### Post by tuxolero on 2009-10-11
I think I'll go back to using Jaunty until the final release of Karmic is out.
I have renamed .config, .local and .kde without success:
I still have a corrupted screen most times, and when the screen is not completely corrupted, most elements (icons, windows, ...) are.
Thanks for the hints, but I am afraid my system is so broken that nothing helps.

---

### Post by tuxolero on 2009-10-17
Hey, everything is working again.

I left alone my Karmic installatoin and used Jaunty in between, and now I updated the system with the recovery mode, and after all current updates, the problems are gone. :)
I coud even use my old .kde, .config and .local directories.

---

