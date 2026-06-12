---
title: "Bug during migration from 23.10 to 24.04"
date: 2024-05-28
forum: Installation &amp; Upgrades
---

### Post by phantoine on 2024-05-28
Hello,
My kubuntu 23.10 propose me the migration to 24.04. 
Then i have this error : [COLOR=#000000][FONT=UICTFontTextStyleTallBody]Failed to fetch [/FONT][/COLOR][http://no.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/ubuntu-release-upgrader-qt_24.04.18_all.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/ubuntu-release-upgrader-qt_24.04.18_all.deb)[COLOR=#000000][FONT=UICTFontTextStyleTallBody] 404  Not Found.  during the migration.
On the archive the file ubuntu-release-upgrader-gt_24.04.17_all.deb. Existe but not the .18
Any idea about this problem ?
Thank you

[/FONT][/COLOR]

---

### Post by coffeecat on 2024-05-28
That's interesting. The ubuntu.com server for Norway (the one you link, the one you are getting a 404 with) appears to have stale information as of the time of this posting. This is the link to the relevant page on the Norway server:

[http://no.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/](http://no.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/)

Apart from showing the .17 version of the ubuntu-release-upgrader-qt package, the last package listed is also now superceded.

Compare with the main server:

[http://archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/](http://archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/)

The server for Sweden:

[http://se.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/](http://se.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/)

And a randomly chosen third party mirror in the UK:

[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-release-upgrader/)

Those three are showing the .18 package you need.

You can either wait a few hours and try again, hoping the Norway server has synced to the main one by then, or you can change your download source to the main server or one of the many around the world that are up to date. In Ubuntu with the gnome desktop you can do that in an app called Software & Updates (first tab = "Ubuntu Software") but I don't know whether that comes with Kubuntu. I'm not at all familiar with KDE so someone else may be able to advise.

**Edit:** with regard to the Software & Updates app, when opened in Ubuntu that starts the process software-properties-gtk. I see that the manifest list for a Kubuntu ISO includes software-properties-qt, so I assume Kubuntu does come with that app.

---

### Post by phantoine on 2024-05-28
Thank you for your help
I change the servers to French server fr.xxxx. In /etc/apt/sources  No problem with the migration now
It seem to be a syncing problem with the Norway server because i try to migrate last week, so it is not a question of hours ?
I don't know why the configuration in 23.10 is made with the Norway server and not with the French server.

---

