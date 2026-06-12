---
title: "Synatptic not working (showing error)"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by kapil1312 on 2007-03-03
whenever I open synatpic,I get the following error window..i am not able to update anything on my machine.please help..

W: Duplicate sources.list entry [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)

W: Duplicate sources.list entry [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)

W: Duplicate sources.list entry [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages)

W: Duplicate sources.list entry [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)

W: Duplicate sources.list entry [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)

---

### Post by zvacet on 2007-03-03
Find in your sources list doubled lines and in front of one put #
Another way is to replace your source list with other one.
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

