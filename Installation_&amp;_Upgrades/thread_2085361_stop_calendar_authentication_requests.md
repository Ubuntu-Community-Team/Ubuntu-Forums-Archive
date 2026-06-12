---
title: "stop calendar authentication requests"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by brown12 on 2012-11-17
Friends: I upgraded from 12.04 to 12.10 with largely great results.

In a previous version, I had a few web calendars pushing events to the Gnome calendar. Clean install to 12.10. Evolution is no longer installed. Unity has replaced gnome as of ... can't remember, but prior to this most recent upgrade.

Today, on login, several dialogue boxes appear and request calendar authentication from Google Calendars. These are a pain. Can I make them go away?

(Calendar integration with Evolution was created under Gnome and not Unity, in case that helps.)

I do not need web calendars integrated with Unity. Best case: I would be able to purge the local configuration files that are triggering the calendar authentication requests.

Thanks in advance.

---

### Post by the_midnighter on 2012-11-30
I had a similar issue. I deleted the ~/.local/share/evolution directory.

---

