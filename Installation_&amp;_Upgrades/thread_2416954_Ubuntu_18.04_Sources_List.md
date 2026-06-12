---
title: "Ubuntu 18.04 Sources List"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by sundanceactual on 2019-04-18
I have a isolated lan that isn't connected to any outside repo, just an ubuntu 18.04 repo thats hosted on ESXi.


How should my sources list look to point to this repo? 
I have it setup as
deb [http://x.x.x.x./Ubuntu/ubuntu/pools](http://x.x.x.x./Ubuntu/ubuntu/pools) (this is where the main, multiverse universe and restricted packages are hosted) 


Do I need to add a deb-src line? Do i not need to add /ubuntu/pools because it will automatically search the indexes? 
Any help is appreciated im pretty new to Ubuntu.

Thanks

---

### Post by deadflowr on 2019-04-18
> Do I need to add a deb-src line?
Only if you intend to build from Ubuntu's source packages, which most users don't.

Sources need to always comply with apt standards.
Read more on sources.list here:
[https://wiki.debian.org/SourcesList]("https://wiki.debian.org/SourcesList")

---

### Post by sundanceactual on 2019-04-19
So I added in [http://x.x.x.x/Ubuntu/ubuntu/pools](http://x.x.x.x/Ubuntu/ubuntu/pools) main/ and it will start to try to get an update but then I get a 404 not found.

I get something like 7 or 8 lines of

Ign [http://x.x.x.x/Ubunut.ubuntu/pools](http://x.x.x.x/Ubunut.ubuntu/pools) main/

First I was getting an error because it doesn't have a release file so I changed it to [trusted=yes] in the sources.list now I get the 404 not found. I can navigate to the repo on a web browser just fine. Is there something im missing?

---

