---
title: "Ubuntu 8.04 installation thinks its running the latest version of Ubuntu"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2009-12-17
OK, trying to update a friend's Ubuntu installation here..

In the Update manager, there's no button to upgrade the distribution.

When i run, sudo do-release-upgrade

it says "No New Release Found".

When I run sudo update-manager -c

there's no button to upgrade the distribution again.

What else is there to try to upgrade this Ubuntu 8.04 installation to 9.10?

---

### Post by scottuss on 2009-12-17
Don't do it!

Backup all important stuff and do a clean install. You'll hit a world of pain if you do an upgrade, especially 8.04 to 9.10!

Seriously, there are ways, but I wouldn't advise it!

---

### Post by snowpine on 2009-12-17
I recommend a fresh install as well.

If you absolutely need to, you can use the following command:

```
sudo do-release-update -d
```

I tried this a couple of days ago and was updated from 8.04 directly to 9.10 Karmic. This is a temporary testing situation... as 10.04 Lucid comes further along in the testing process, the command above will upgrade to that instead (which I don't think is what you want!) so please double check before saying Yes.

But please, please, please try a fresh install if at all possible. :)

---

### Post by =not4prophet= on 2009-12-17
or if you really want to use the gui update-manager, you will need to change the release upgrade setting in Software Sources from "Long term support releases only" to "Normal releases"

---

### Post by snowpine on 2009-12-17
> **=not4prophet= said:**
> or if you really want to use the gui update-manager, you will need to change the release upgrade setting in Software Sources from "Long term support releases only" to "Normal releases"

That will only get you to 8.10, not 9.10 (unless you go 8.04->8.10->9.04->9.10, which is ridiculous :))

---

