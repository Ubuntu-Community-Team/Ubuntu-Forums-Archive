---
title: "[SOLVED] Firefox 3 failed upgrade"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by LilYoda on 2008-07-25
Hey y'all

Today I noticed that I had a failed upgrade.  I just clicked next like an idiot, and got firefox 3 erased

I tried to reinstall, and noticed it was impossible to do so because of failed dependencies.  It was complaining the versions of libpango and xulrunner were too old.

I found out that I had only enabled the security updates in the package manager. ** So the firefox update is pushed via security updates, but not its dependencies.**

To make it work, temporarily allow important updates in the package manager, install FF3, and rollback to your previous settings.

Hope this helps

L8r

---

### Post by High Roller on 2008-07-25
> **LilYoda said:**
> Hey y'all

Today I noticed that I had a failed upgrade.  I just clicked next like an idiot, and got firefox 3 erased

I tried to reinstall, and noticed it was impossible to do so because of failed dependencies.  It was complaining the versions of libpango and xulrunner were too old.

I found out that I had only enabled the security updates in the package manager. ** So the firefox update is pushed via security updates, but not its dependencies.**

To make it work, temporarily allow important updates in the package manager, install FF3, and rollback to your previous settings.

Hope this helps

L8r

I had this same problem as well.  On my parents computer, I have only the security repo active under System Updates and it automatically pulls updates and installs them.

So, I get a call from my parents this morning that their internet isn't working.  And I arrive to find out that Firefox is magically missing.  I couldn't uninstall or reinstall.  Nothing worked.

So I figured it must be the repos and I switched from the Canadian repo to the "Main" one..  refreshed and then all of the sudden the dependencies were met and the installation completed.

---

