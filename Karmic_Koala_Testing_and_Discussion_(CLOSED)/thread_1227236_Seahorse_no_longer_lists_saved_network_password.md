---
title: "Seahorse no longer lists saved network password"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-30
Opening seahorse 2.27.5 shows absolutely nothing listed under "Other Keys" tab. Previously I was able to add, delete and view all my saved network passwords and wireless network secrets. Is this still working properly for everyone?

---

### Post by tekstr1der on 2009-07-30
Tested this with a fresh user profile. Set up a wireless network connection. Launched Applications>Accessories>Encryption and Keyrings. Observed absolutely nothing is listed.

I know this was working fairly recently.

---

### Post by tekstr1der on 2009-07-30
Furthermore, launching seahorse from the terminal yields:

```
$ seahorse

** (seahorse:4271): WARNING **: DNS-SD initialization failed: Daemon not running
** Message: init gpgme version 1.1.8

** (seahorse:4271): WARNING **: could not find widget password-tab for seahorse-key-manager.xml

** (seahorse:4271): CRITICAL **: initialize_tab: assertion `self->pv->tabs[tabid].widget != NULL' failed
```

Looking at the changelog, I see there is supposed to be a passwords tab now. That is not displaying for me and the above error makes that much clearer now. I reinstalled seahorse, but still the same. Is this just broken for me?

---

### Post by BCurtisWX on 2009-07-30
File a bug, but remember to search for one already reported beforehand

---

### Post by tekstr1der on 2009-07-30
Yeah, I filed [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/407063](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/407063) as the password tab is new, there would be no older bug. Just was hoping someone here would confirm the issue.

---

### Post by wayne_cat on 2009-07-30
> **tekstr1der said:**
> Yeah, I filed [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/407063](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/407063) as the password tab is new, there would be no older bug. Just was hoping someone here would confirm the issue.


confirmed by "This bug affects me too"

---

### Post by autocrosser on 2009-07-30
> **wayne_cat said:**
> confirmed by "This bug affects me too"

Also confirmed....No tab for passwords here...

---

### Post by scaine on 2009-08-04
Looks like Gnome has just picked this up now :
[http://bugzilla.gnome.org/show_bug.cgi?id=590331](http://bugzilla.gnome.org/show_bug.cgi?id=590331)

Andreas Moog appears to have jumped onto the launchpad report from a duplicate, then reported it upstream.

---

### Post by tekstr1der on 2009-08-04
Actually, he bumped it upstream the same day I reported it. There just hasn't been any activity until today when someone confirmed the issue with fedora rawhide as well.

---

### Post by scaine on 2009-08-06
And now it's fixed.  I have no idea how long before we see this in Karmic though.  Will update tonight and test.

[EDIT : Midday Sunday and no sign of a new Seahorse in Karmic.  Hopefully it will hit the repos before the Alpha4 freeze]

---

### Post by scaine on 2009-08-13
That seems to be the latest Seahorse available now and I've successfully gotten my login passwords to show up again.  All good.

---

