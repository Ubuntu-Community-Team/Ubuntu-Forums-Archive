---
title: "update manager NOT detecting new release"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by paul99 on 2007-08-07
Hi,

I'm finally getting around to upgrading to FF from Edgy.  The instructions I tried to follow were:

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

However, when I click on Update Manager, it says everything's up-to-date; it **doesn't** say:

[IMG]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager-upgrade.png[/IMG]

:confused:

Any ideas?!

Thanks,

Paul

---

### Post by benanzo on 2007-08-07
I think you'll need tell **update-manager** to check for distribution upgrades manually.
Open a terminal and do:
```
gksu "update-manager -c"
```
The **-c** flag is equivalent to **--check-dist-upgrades**.  You should then get the chance to upgrade to Feisty.

---

### Post by paul99 on 2007-08-07
> **benanzo said:**
> I think you'll need tell **update-manager** to check for distribution upgrades manually.
Open a terminal and do:
```
gksu "update-manager -c"
```
The **-c** flag is equivalent to **--check-dist-upgrades**.  You should then get the chance to upgrade to Feisty.

Great, thanks!

---

