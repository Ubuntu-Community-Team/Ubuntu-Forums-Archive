---
title: "Karmic Login Screen Paint Issues"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-08-05
I'm seeing painting issues with the login screen. When the login form resizes after selecting the user, there is a black section that doesn't get repainted to match the rest of the background.

Here is an example of what it looks like to give a general idea:
[http://img26.imageshack.us/img26/2305/screenshotowb.png](http://img26.imageshack.us/img26/2305/screenshotowb.png)

Anyone else seeing this with the latest nvidia 185.18.14-0ubuntu3 installed? Or any other video drivers?

---

### Post by wayne_cat on 2009-08-05
> **kyleabaker said:**
> I'm seeing painting issues with the login screen. When the login form resizes after selecting the user, there is a black section that doesn't get repainted to match the rest of the background.

Here is an example of what it looks like to give a general idea:
[http://img26.imageshack.us/img26/2305/screenshotowb.png](http://img26.imageshack.us/img26/2305/screenshotowb.png)

Anyone else seeing this with the latest nvidia 185.18.14-0ubuntu3 installed? Or any other video drivers?

a GDM bug 

[http://ubuntuforums.org/showthread.php?t=1224445&highlight=gdm](http://ubuntuforums.org/showthread.php?t=1224445&highlight=gdm)

---

### Post by taavikko on 2009-08-05
> **wayne_cat said:**
> a GDM bug 

[http://ubuntuforums.org/showthread.php?t=1224445&highlight=gdm](http://ubuntuforums.org/showthread.php?t=1224445&highlight=gdm)

bug in gtk to be exact.

---

### Post by wayne_cat on 2009-08-05
> **taavikko said:**
> bug in gtk to be exact.

you are right!

and still no fix available:

[http://bugzilla.gnome.org/show_bug.cgi?id=589369](http://bugzilla.gnome.org/show_bug.cgi?id=589369)

---

### Post by Darkshade on 2009-08-05
I fixed that by setting compiz as window manager for GDM. Seems to load just a little bit slower though...

---

### Post by kingborel on 2009-08-05
I'm getting the same thing on Intel with xorg-edgers drivers. Annoying, but I can live with it for the moment

---

### Post by forumache on 2009-08-06
> **Darkshade said:**
> I fixed that by setting compiz as window manager for GDM. Seems to load just a little bit slower though...

How did you do that?

---

### Post by wayne_cat on 2009-08-10
Todays GTK+ update fixed this bug

---------------
gtk+2.0 (2.17.6-0ubuntu2) karmic; urgency=low

  * debian/patches/092_bugzilla_fix_gdm_refresh_issue.patch:
    - upstream change to workaround a gdm refresh issue
      (lp: #405392)

-- Sebastien Bacher <seb128@ubuntu.com>   Sun, 09 Aug 2009 22:17:11+0200

---

### Post by phenest on 2009-08-10
Yeah. Much nicer.:)

---

### Post by Darkshade on 2009-08-10
Yup, just noticed it on my laptop and switched back to metacity on my main PC :)


> **forumache said:**
> How did you do that?

By running gconf-editor as gdm user. I don't recommend it though, I screwed up my GDM while tweaking stuff from there and had to purge and reinstall, which didn't go as smooth as I expected. Seriously, now that it's fixed - don't mess with that stuff unless you know what you're doing :D

---

