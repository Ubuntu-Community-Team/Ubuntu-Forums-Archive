---
title: "Upraded Ubuntu 12.04 to 14.04 BIG uglies !"
date: 2014-11-07
forum: Installation &amp; Upgrades
---

### Post by Peter_Bartolovich on 2014-11-07
three months ago, my two One-year old 32 bit ASUS boxes that shipped-from-the-factory loaded with Ubuntu 12.04  (***_Only_*** Ubuntu !)/Google Chrome browsers computers were upgraded to 14.04, one went absolutely fine, the other really messed its pants.
 
My computer dumped Google, and installed with Firefox (I detest Firefox), I have spent many-many hours (sometimes 8 hours at a time) in terminal, the software center, and _many _online forums trying to load up Google again... but, Firefox blocks every attempt. LOCKED !

A six hour "get lucky" session yesterday got rid of Firefox, still unable to reload Google Chrome like on the other computer, I loaded Chromium, but now I can only use it if I "Sign on in a new window with a temporary profile", go to the Google hash bars, and sign in with my Google ID, then go manually load up Chrome . . .  and all is well (whew ! but NO Firefox or Microsoft here !).

I can live with **_this_** Chromium aggravation, but, over on Bluefish my preview button <preferences/external/default browser settings as: Chromium/ Chromium-browser '%p'&   or,   Google/ Google-chrome '%p"&  DO NOT work as "Default browser" ... I now have NO preview whatsoever.

So, I am open to continue listening to what to do next.... 14.04 has ruined my computer, and has frustrated me with Ubuntu.....

---

### Post by lukeiamyourfather on 2014-11-07
Have you tried to install Chrome using Google's package and repository?

[https://www.google.com/chrome/browser/?platform=linux](https://www.google.com/chrome/browser/?platform=linux)

Set the default browser?

```
sudo update-alternatives –config x-www-browser
```

---

### Post by Peter_Bartolovich on 2014-11-07
this gives me  ....   whazammo@earthport1:~$ sudo update-alternatives &#8211;config x-www-browserupdate-alternatives: error: unknown argument `&#8211;config'

---

### Post by Peter_Bartolovich on 2014-11-07
I have now installed googles package  un-installed, re-installed and installed from terminal 14 times.

---

### Post by Impavidus on 2014-11-07
> **Peter_Bartolovich said:**
> this gives me  ....   whazammo@earthport1:~$ sudo update-alternatives &#8211;config x-www-browserupdate-alternatives: error: unknown argument `&#8211;config'

I guess that should be **--config**, not **&#8211;config**. A double dash instead of an en-dash. So, as usual.

Edit: to make it clear (as a bold double dash looks almost the same as an en-dash):```
--config, not &#8211;config, nor -config
```

---

### Post by Peter_Bartolovich on 2014-11-07
OK, that worked fine I resetto the Chromium selection, but really nothing has changed.

---

### Post by sp40140 on 2014-11-10
Peter
How are you trying to install Chrome browser? (I did it by downloading the .deb file which I double clicked, and everything went fine, No issues since).
Now, You say "trying to load up Google again... but, Firefox blocks every attempt. LOCKED !" is that only for the default browser or you mean to say that ff doesn't let you install chrome?
Also, when you try to install chrome, do you get any errors during installation? You can also check /var/log folder where all logs are stored.

---

