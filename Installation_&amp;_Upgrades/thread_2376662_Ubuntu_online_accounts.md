---
title: "Ubuntu online accounts"
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by ds-mailbag on 2017-11-04
Ok; just upgraded to 17.10

I had a google account setup in 17.04 but it's not listed in gnome settings online accounts after the upgrade.

However, if I open calendar and go to calendar->calendars its listed there; if i open it there's no delete button shown.

Did a grep search and it threw up references in the following locations:-
~/.config/libaccounts-glib/accounts.db
~/.config/evolution/sources/name@MACHINE.source
~/.config/signond/signon.db

The link is live in calendar because data syncs correctly.

Why is this NOT listed in online accounts??? If I add the account there it's listed TWICE in calendar - delete it and it's still listed once in calendar!!!

Any ideas??

---

### Post by william.hua on 2017-11-05
I'm not sure from a technical aspect why that happened. However, I would just delete all that local data and try to setup your Google Account again in Ubuntu. That data is synced to the cloud, so you should have to worry about losing it.

---

### Post by ds-mailbag on 2017-11-14
> **william.hua said:**
> I'm not sure from a technical aspect why that happened. However, I would just delete all that local data and try to setup your Google Account again in Ubuntu. That data is synced to the cloud, so you should have to worry about losing it.

Did that, but it all kept reappearing until I downloaded DB Browser and deleted the credentials in ~/.config/signond/signon.db

After that everything fine

---

