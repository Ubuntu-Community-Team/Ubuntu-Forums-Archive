---
title: "Help! Gusty install froze halfway through"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by allspiritseve on 2007-10-25
Ok, I decided to upgrade, and everything worked great up til 13 minutes before it was done installing. The  installer warned me that mysql may not work properly after the update, and then when I clicked on the button to submit a bug report, everything froze. After a while I could still use other programs, but the installer didn't change after an hour, so I restarted. Now, I can't connect to the internet (no device found) and adept/system settings each crash when I try and load them.

What can I do to either 1. finish upgrading or 2. Downgrade so I can try again?

Thanks,

Cory

---

### Post by allspiritseve on 2007-10-25
OK, I take it back... started up recovery console, tried sudo apt-get install, and got this:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

That worked. I'm all set.

---

### Post by allspiritseve on 2007-10-25
As far as I can tell, everything works now except mysql:

```
071025 22:10:48  InnoDB: Started; log sequence number 0 43655
071025 22:10:48 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
071025 22:10:48 [Note] Starting crash recovery...
071025 22:10:48 [Note] Crash recovery finished.
071025 22:10:48 [ERROR] mysqld: Incorrect information in file: './mysql/user.frm'
071025 22:10:48 [ERROR] mysqld: Incorrect information in file: './mysql/user.frm'
071025 22:10:48 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect information in file: './mysql/user.frm'

```

Any ideas?

---

