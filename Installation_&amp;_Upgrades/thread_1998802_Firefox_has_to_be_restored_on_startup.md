---
title: "Firefox has to be restored on startup"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2012-06-07
Every time I log in I have to restore Firefox (Its embarrassing for firefox but annoying for me!). It doesn't happen with firefox on my other drive on which I have Meverick installed. It happened when I had 11.10 on this drive and now it is happening with Precise. Upgrade to Firefox 13 does not fix.

Any hints?

My system:

Desktop
2 GiB Ram
Dual AMD 5200 processor
32 bit OS
Drive 1: 160 GiB Sata (Maverick)
Drive 2: 53 Gib ADA (Precise)

---

### Post by roelforg on 2012-06-07
You only have to restore ff when it shuts down improperly.
How do you close ff? (use the X, use the file->exit or let it terminate on logout)
The secret's in there.

---

### Post by JohnMac on 2012-06-09
That is true, if I file/exit then I don't need to restore. I usually exit on logout and when I login my fav sites come up. It didn't occurr on Ubuntu Maverick and previous distros.

---

### Post by black veils on 2012-06-09
i don't have access to the specific info at the moment, but there is something which can be disabled in the hidden firefox configuration. i have tried 3 distributions which cause firefox to not shutdown properly, the system is too fast for firefox, i always had that happen until changing the setting. it still allows for on-demand restore of tabs, if firefox is restarted for an extension for example. i have used the method for a while without problems.


Edit:

1.   open firefox

2.   type into the address bar ```
about:config
``` then press the **Enter** key

3.  it will show a warning, but just proceed

4.  in the search bar, paste the following into it ```
browser.sessionstore.resume_from_crash
```5.  under the **value** header, double-click **true** so it changes to **false**.


thats it!  make a copy of this info, in case you ever want to change it back.

---

### Post by JohnMac on 2012-06-25
Thanks that seems to have done the trick.

---

