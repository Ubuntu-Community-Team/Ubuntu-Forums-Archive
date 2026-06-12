---
title: "weird USB behavior since upgrading to 11.04 (HUAWEI E220)"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by lightxx on 2011-05-28
ok. today i upgraded my dad's PC from ubuntu 10.10 to Naty.
everything went well, except for one thing. when it came to installing/upgrading 'udisk', his PC froze (i had the terminal open while upgrading). i had to power cycle the thing and it came up with 11.04.

now my dad uses a huawei E220 USB UMTS modem. whenever the modem is plugged in, his PC behaves extremely weird. there are 4-5 second delays on every keystroke or mouse move. as soon as the modem is plugged out everything goes back to normal.
thing is, everything worked as supposed pre-upgrade, plus my dad needs to get his internet connection working again.

any ideas?

thanks,
Tom

---

### Post by lightxx on 2011-05-29
c'mon guys. this is really important to me. anyone?

what's the easiest way to roll back to Maverick?

---

### Post by awam66 on 2011-05-29
> **lightxx said:**
> c'mon guys. this is really important to me. anyone?

what's the easiest way to roll back to Maverick?

You need to do a clean install of Maverick.

---

### Post by lightxx on 2011-05-30
does "clean install" mean i'll lose all my settings, desktop icons, and whatever else? is there some convenient way to back up user settings and restore them later?

---

### Post by awam66 on 2011-05-30
> **lightxx said:**
> does "clean install" mean i'll lose all my settings, desktop icons, and whatever else? is there some convenient way to back up user settings and restore them later?

There are several things you can do but it depends on your installation. If you installed Maverick originally with a separate partition for "Home" then upgraded to Natty, doing a clean install of Maverick do not format the home partition. Do a manual partition and format the / partition only.
If you want to back up your settings copy tour home folder, including all hidden files to a memory stick or external hard drive, do a clean install then copy back the home folder.
Hope that helps.

---

