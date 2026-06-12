---
title: "How can I change the login screen background in Karmic?"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nechus on 2009-08-15
Hello

I suffer from a severe case of versionitis and couldn't resist the temptation to upgrade to Karmic Alpha 4 from SuperOS Jaunty.  I'm very impressed, but I can't figure out how to change the login screen background. There's no way to change the GDM in System>Preferences>Login screen now!:confused:

Everything else is working remarkably fine on my Acer Aspire 5738. Even the usplash found the correct screen size, and it's not stretched to she sides anymore.

Thanks

---

### Post by VMC on 2009-08-15
> **nechus said:**
> Hello

I suffer from a severe case of versionitis and couldn't resist the temptation to upgrade to Karmic Alpha 4 from SuperOS Jaunty.  I'm very impressed, but I can't figure out how to change the login screen background. There's no way to change the GDM in System>Preferences>Login screen now!:confused:

Everything else is working remarkably fine on my Acer Aspire 5738. Even the usplash found the correct screen size, and it's not stretched to she sides anymore.

Thanks

There's several threads at the [Karmic Koala Testing]("http://ubuntuforums.org/forumdisplay.php?f=359") on this subject right now. Check them out.

---

### Post by overdrank on 2009-08-15
Moved to Karmic Koala Testing and Discussion

---

### Post by wayne_cat on 2009-08-15
> **nechus said:**
> Hello

I suffer from a severe case of versionitis and couldn't resist the temptation to upgrade to Karmic Alpha 4 from SuperOS Jaunty.  I'm very impressed, but I can't figure out how to change the login screen background. There's no way to change the GDM in System>Preferences>Login screen now!:confused:

Everything else is working remarkably fine on my Acer Aspire 5738. Even the usplash found the correct screen size, and it's not stretched to she sides anymore.

Thanks

The feature to change the GDM background via gdmsetup is still missing but you
can change it from the command line. Have a look at this:

[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

---

### Post by nechus on 2009-08-16
Thank you all, guys.  I solved this problem the "caveman" way: I just went to /usr/share/backgrounds and copied there my favorite wallpaper, giving it the name of the image the GDM was using. That did the trick.
\\:D/

---

### Post by ranch hand on 2009-08-16
That is currently pretty much the "trick".

---

