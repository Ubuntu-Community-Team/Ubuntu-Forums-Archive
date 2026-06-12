---
title: "How do I reset my GDM appearance?"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-10-07
I've been tweaking my GDM settings, but I'd like to reset them to default.

How do I do this?

---

### Post by tawmas on 2009-10-07
> **Starks said:**
> I've been tweaking my GDM settings, but I'd like to reset them to default.

How do I do this?

I just renamed my /var/lib/gdm/.gconf directory out of the way... I didn't have any side effects, but keep the old directory around just in case.

---

### Post by ranch hand on 2009-10-07
Ok, I have just checked all five of my 32bit 9.10 installs and they all have /var/lib/gdm and no further, this is an empty directory.

I admit to just changing the background by changing the /usr/share/images/xsplash/bg_2650x1600 and being satisfied with that.  This may be why I do not have the file mentioned.

Could someone tell me if that assumption is correct?

I a just a noob trying to follow the path to linux enlightenment.  Better eye sight and a higher IQ might help but I muddle along and try to HAVE FUN.

---

### Post by FuturePilot on 2009-10-07
> **ranch hand said:**
> Ok, I have just checked all five of my 32bit 9.10 installs and they all have /var/lib/gdm and no further, this is an empty directory.

I admit to just changing the background by changing the /usr/share/images/xsplash/bg_2650x1600 and being satisfied with that.  This may be why I do not have the file mentioned.

Could someone tell me if that assumption is correct?

I a just a noob trying to follow the path to linux enlightenment.  Better eye sight and a higher IQ might help but I muddle along and try to HAVE FUN.

Everything in /var/lib/gdm is hidden since all the directories contain a . in front of them. Just move that directory out of the way as the poster above said.

---

### Post by ranch hand on 2009-10-08
Well I'll be hornswoggled. so it is.

Thank you very much for the info [FuturePilot]("http://ubuntuforums.org/member.php?u=178962").

---

### Post by Darkshade on 2009-10-08
I had messed a lot with GDM too so I tried renaming the folder. Now my gdm uses the default wallpaper as a background and the login box is light grey (like it used to be some time ago).

---

