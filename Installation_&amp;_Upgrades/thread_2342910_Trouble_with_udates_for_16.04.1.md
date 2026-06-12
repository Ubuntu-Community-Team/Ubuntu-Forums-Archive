---
title: "Trouble with udates for 16.04.1"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by Aries01 on 2016-11-11
Hello

  Updating 16.04.1 became terribly slow on my computer after I activated the Canonical Partners repository in order to install adobe-flashplugin for Chromium and Firefox. Many attempts simply fail. I also activated the repository titled cdrom:[Ubuntu 16.04.1 LTS_Xenial xerus_Release amd64 (20160719)]/ xenial, and a failed update attempt gave me the following message:

W:The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Some index files failed to download. They have been ignored, or old ones used instead.

 As advised on a forum post, I activated the Canonical Partners repository and then install the Flash plugin in the terminal. The plugin works, but I got the problem described above. Should something else be activated too, or installed? 

  There used to be an alternative for Adobe flashplugin called Pepperflash, but apparently it is no longer supported. Flash has such a bad reputation- is there any alternative to Adobe's plugin that would be better?

---

### Post by CantankRus on 2016-11-11
The "cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial" source uses your liveCD, if you have one inserted, as a Repository.
Not normally needed and suggest you disable.

The adobe-flashplugin is about all you can use for flash sites.
The package installs...
[LIST]
[*]NPAPI: 11.2.202.644
[*]PPAPI: 23.0.0.207
[/LIST]
versions of adobe flash.

I believe firefox uses NPAPI and chromium based browsers use PPAPI flash.

The state of flash is pretty confusing at the moment.
Perhaps someone can explain or provide a link that explains it clearly.

---

### Post by oldos2er on 2016-11-11
Thread moved to *Installation & Upgrades*.

---

