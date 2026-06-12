---
title: "Re-Install / Re-Provision Ubuntu 13.04 Install Help?"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by kenetik on 2013-11-26
Hello,

Thank for you taking the time and interest to this thread.

I recently purchased a dedicated server, located in a colo spot far from my residence. So unfortunately performing a clean install does not seem to be an option. There are some configurations and settings that I would like to revert, it seems as if reverting all configs/settings back to their original or default state would be optimal. Is there a way for me to do this remotely? Thanks again.

---

### Post by kenetik on 2013-11-26
For anyone that searches this, I wanted to provide the information I gained from the IRC channel as well:
--
From wafflejock / Shaun:

> [http://askubuntu.com/questions/48886/how-do-i-list-the-default-installed-packages](http://askubuntu.com/questions/48886/how-do-i-list-the-default-installed-packages)
you can use dpkg --get-selections to see all currently installed packages
dpkg-reconfigure packagename should re run configuration for a package not entirely sure on reverting the network config changes
think you could do a Grub ISO boot but I don't have experience and am not sure I would be comfortable doing this without physical access

Thanks wafflejock

---

### Post by ian-weisser on 2013-11-26
> **kenetik said:**
> There are some configurations and settings that I would like to revert, it seems as if reverting all configs/settings back to their original or default state would be optimal. Is there a way for me to do this remotely?

Without knowing any specifics, you must be able revert the changes to each config, application, or package separately.
There is no magic "restore-factory-settings" app. dpkg -reconfigure comes close, but removal of some types of customizations is not guaranteed.



I log every config/setting change so I can find them again, I backup the default config file, and I liberally link all custom files to my server's ~/custom-configs...for precisely this reason.

Of course, your situation may have an easy-restore option. Some situations do. Rsyslog, for example, encourages you to leave the default alone and add your own separate config file. Reverting is as easy as deleting the custom file.

---

