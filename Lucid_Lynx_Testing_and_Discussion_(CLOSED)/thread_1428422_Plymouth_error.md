---
title: "Plymouth error?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Madspyman on 2010-03-12
Got this error when trying to boot my Lucid partition.

> mountall: error while loading shared libraries: libplybootclient.so.2: cannot open shared file: no such file exists

init: mountall main process (281) terminated with status (127)

It happened after running update manager (which had a plymouth upgrade) and restarting.

I'm guessing libplybootclient has something to do with plymouth, and things were working great before the update.

---

### Post by Vanishing on 2010-03-12
> **Madspyman said:**
> Got this error when trying to boot my Lucid partition.



I'm guessing libplybootclient has something to do with plymouth, and things were working great before the update.

like i posted and somebody else posted earlier..do not upgrade plymouth yet..

---

### Post by benrboone on 2010-03-14
I had the same problem,  the following post help me solve it.
[http://it.toolbox.com/blogs/securitymonkey/ubuntu-psa-fixing-mountall-failure-at-boot-on-ubuntu-lucid-alpha-37440#commentsform](http://it.toolbox.com/blogs/securitymonkey/ubuntu-psa-fixing-mountall-failure-at-boot-on-ubuntu-lucid-alpha-37440#commentsform)
If you are running 64 bit then note the change in the comments for the amd64 bit package.  Good luck

---

### Post by teh603 on 2010-03-14
Yeah, doing a clean reinstall then removing plymouth BEFORE installing updates is generally what works. Mountall kills the -13 version, and -14 seems to drop me into a confusing text shell.

---

