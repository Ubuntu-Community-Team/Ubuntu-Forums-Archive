---
title: "Gusty Upgrade -&gt; Pidgin: No account types"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by ture_atlantis on 2007-11-08
Upgraded to Gusty, and it seems that Pidgin does not work.

It looks like the package is not configured correctly.  When running with the '--debug' flag, i get these errors.  It looks like Pidgin is looking for 2.1.x plugins, but it is getting 2.2.x plugins.  Which is weird because the pidgin that executes is version '2.2.1'  

Has anyone else experienced this?  Thanks

```

(11:39:07) plugins: probing /usr/lib/pidgin/iconaway.so
(11:39:07) plugins: /usr/lib/pidgin/iconaway.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/musicmessaging.so
(11:39:07) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: undefined symbol: purple_dbus_register_bindings
(11:39:07) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/timestamp_format.so
(11:39:07) plugins: /usr/lib/pidgin/timestamp_format.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/ticker.so
(11:39:07) plugins: /usr/lib/pidgin/ticker.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/pidginrc.so
(11:39:07) plugins: /usr/lib/pidgin/pidginrc.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/notify.so
(11:39:07) plugins: /usr/lib/pidgin/notify.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/cap.so
(11:39:07) plugins: /usr/lib/pidgin/cap.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/gevolution.so
(11:39:07) plugins: /usr/lib/pidgin/gevolution.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)
(11:39:07) plugins: probing /usr/lib/pidgin/gestures.so
(11:39:07) plugins: /usr/lib/pidgin/gestures.so is not loadable: ABI version mismatch 2.2.x (need 2.1.x)

```

---

### Post by jmagsho on 2007-11-09
Have you tried uninstalling Pidgin and then reinstalling the latest version from the repositories (via synaptic or a Terminal window)?

---

### Post by ture_atlantis on 2007-11-09
yes, multiple times.

---

### Post by silverpig on 2007-12-04
Any solution to this? My pidgin stopped working after a reboot. I'd go to start it and nothing would happen. Starting from the terminal did nothing either (pidgin just exits).

I did a remove --purge on pidgin and gaim, reinstalled pidgin, nothing. I now have compiled 2.3.0 from source and get the same thing.

pidgin -d gives messages like:

(18:39:34) plugins: /usr/local/lib/pidgin/markerline.so is not loadable: ABI version mismatch 2.3.x (need 2.2.x)

solutions?


UPDATE: purged libpurple0 and the abi stuff went away.

---

