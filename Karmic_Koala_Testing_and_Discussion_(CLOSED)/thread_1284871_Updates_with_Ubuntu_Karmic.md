---
title: "Updates with Ubuntu Karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by deancasino on 2009-10-07
Hey guys, I'm new to Ubuntu and love it. I just upgraded to Karmic Beta from Jaunty today and now I'm having trouble installing with Ubuntuzilla (though it may be unrelated, I thought I'd check) also when I run Update Manager an error appears with the following;

W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Absolutely any help in fixing this will be greatly appreciated,

Thanks

---

### Post by deancasino on 2009-10-07
Lol I've solved it, sorry, feel free to delete this thread.

---

### Post by fraser_m on 2009-10-07
When you upgraded, it changed the sources from Jaunty ones to Karmic ones, which apparently haven't been created. Try having a look in Software Sources, or /etc/apt/sources.list.

EDIT: Why are you even using Karmic if you're new to Ubuntu?

---

