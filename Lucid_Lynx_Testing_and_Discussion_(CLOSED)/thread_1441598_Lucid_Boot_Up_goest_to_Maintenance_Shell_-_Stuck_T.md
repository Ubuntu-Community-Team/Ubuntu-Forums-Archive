---
title: "Lucid Boot Up goest to Maintenance Shell - Stuck There"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2010-03-28
I'm currently stuck in the maintenance shell, I think since the upgrade to 2.6.32.17.

I've tried pretty much everything I can find on these forums.  KMS disabled, nomodeset, plymouth splash file deleted, plymouth package removed, nouveau disabled, no xorg,conf file, then xorg.conf file with nv driver, removed and reinstalled plymouth, mountall and several other packages I thought might be relevant.  I also checked all my packages for errors.

Nothing has worked.  However, I do still notice a couple things:

I get the initial login screen with graphics, so X and gdm seem to be working.  I log in and then get the maintenance shell screen in the upper left corner.  Gdm is running and if I restart it, same thing.  Same with startx, it's running also.

During the boot up I still get a message that plymouth is terminated with status 1.  I've reloaded plymouth.

When I pull the logs, the xorg log looks OK, but I keep getting a message in the syslog:

gdm-session-worker[1538]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

I haven't figured that out.

So I'm stuck, and can't think of anything else to try except wait around for package updates.  Anybody else figured this out?

---

### Post by seattle vic on 2010-03-29
Well, just before giving up for the night, I was going through bug reports related to this and came across one that suggested to install gnome-session.  I did not look to see if I already had it installed, but presume that I did.

Anyway, it worked.

---

