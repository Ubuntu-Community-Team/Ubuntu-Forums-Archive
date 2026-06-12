---
title: "Upgrade manager Crashed half way through"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by taddy_porter on 2008-05-16
I went to upgrade to Hardy and downloaded everything. Halfway through the install upgrade manager crashed while installing phpbb.

I rebooted and ran dpkg --configure -a to fix phpbb but the other half of the items didn't get fixed. Now when I reboot I get errors about reading the customizations or config files, I get a "corba/comm_failure when opening anything and I get debconf errors about a damaged database table.

I'm left with a blank default desktop with no panel. I went into the terminal and did an apt-get update && upgrade and got a few updates, but I think some of the original items in the upgrade didn't get installed.

Any idea what my problem(s) now are, and how to fix them?

---

### Post by prshah on 2008-05-16
> **taddy_porter said:**
> I went to upgrade to Hardy and downloaded everything. Halfway through the install upgrade manager crashed while installing phpbb.

Any idea what my problem(s) now are, and how to fix them?

See my (solved) thread with the same problem:
[http://ubuntuforums.org/showthread.php?t=780531&highlight=hardy+wonderful](http://ubuntuforums.org/showthread.php?t=780531&highlight=hardy+wonderful)

Summary: From recovery mode```

dpkg --configure -a --force-all

```

---

