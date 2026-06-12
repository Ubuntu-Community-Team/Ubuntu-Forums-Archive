---
title: "Upgrade questions"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by peppermint on 2006-08-13
Hi, Iv got a server running Ubuntu 5.10. Installed from an install CD with the word “server” typed in at install. A few weeks ago I downloaded version 6.06, server edition. Before I go off and upgrade my server, please answer these two questions.

My server is updated by a weekly cron job i set up a few months ago, before 6.06 was released. Is my system still getting updates?

Will installing the latest release destroy the current LAMP configuration I've setup?

---

### Post by Jussi Kukkonen on 2006-08-13
> My server is updated by a weekly cron job i set up a few months ago, before 6.06 was released. Is my system still getting updates?
If your script works, sure. Normal Ubuntu releases are supported for 18 months.

> Will installing the latest release destroy the current LAMP configuration I've setup?
Configuration file changes you've made should not get lost. During the upgrade procedure you'll be asked if you want to use your modified version or the updated version -- both will be saved as far as I can remember, and you can later edit them.
Of course this doesn't guarantee that the upgrade will go 100% smooth... Let's say an apache config file changes in ways that can't be automated -- you'll end up with borked Apache until you fix the config file by hand.

---

### Post by peppermint on 2006-08-15
> **Jussi Kukkonen said:**
> If your script works, sure. Normal Ubuntu releases are supported for 18 months.

Thanks for the reply. Knowing that, I might as well wait until the next release :)

---

