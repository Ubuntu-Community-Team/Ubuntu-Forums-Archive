---
title: "upgrade to edgy issues"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by mr love and justice on 2006-11-06
I updated to 6.10 last night and am currently having difficulty resolving a few issues. I first noticed that my wireless internet card was no longer working. My windows driver was intact so I suspected that perhaps ndiswrapper had been deleted. When I tried to check that out with synaptics, I received the following error.

Error: Opening the cache (E: Malformed line 31 in source list /etc/apt/sources.list (dist parse), E: The list of sources could not be read.)

Line 31 reads as follows:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

Any ideas?

MLaJ

---

### Post by babooka on 2006-11-06
> **mr love and justice said:**
> I updated to 6.10 last night and am currently having difficulty resolving a few issues. I first noticed that my wireless internet card was no longer working. My windows driver was intact so I suspected that perhaps ndiswrapper had been deleted. When I tried to check that out with synaptics, I received the following error.

Error: Opening the cache (E: Malformed line 31 in source list /etc/apt/sources.list (dist parse), E: The list of sources could not be read.)

Line 31 reads as follows:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

Any ideas?

MLaJ

should be something like:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

---

### Post by mcglnx on 2006-12-19
Strange I had the same issue ticking the 'sources' part as well,...
A bug?

---

