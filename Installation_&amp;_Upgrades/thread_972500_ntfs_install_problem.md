---
title: "ntfs install problem"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by mrmaster on 2008-11-05
hello,

I'm trying to install ntfs-config tool but i can't b/c the add/remove program says that ntfs-config conflicts with other programs. The problem is I don't know what programs it conflicts with so i can't really uninstall them. 

Also when I try to update and click on "check" i keep receiving this messages: 

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/Release.gpg](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/Release.gpg)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/i18n/Translation-en_US.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/i18n/Translation-en_US.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Some index files failed to download, they have been ignored, or old ones used instead.

I was wondering how I may get rid of them. 

Thanks

---

### Post by cariboo on 2008-11-05
Remove the:

> [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info)

Entry from your /etc/apt/menu.list. You don't need them as the the ntfs programs you need are installable using Add/Remove Programs or Synaptic Package Manager.

The reason you can't install the the version from the ntfs-g3 repositories is that they are probably a newer version.

Jim

---

### Post by mrmaster on 2008-11-05
I still can't install the ntfs tool but it did get rid of those messages when i try to update. I couldn't find the menu.lst when i went to ect/apt/ but there was source.list which i went into and unclicked ntfs-3g.sitesweetsite.info/ubuntu/dapper.

By the way does that mean I won't get updates if i get the ntfs tool installed?

I have hidden files feature turned off and i was still nto able to see the menu.list file.

---

