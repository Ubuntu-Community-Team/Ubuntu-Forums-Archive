---
title: "Can updating break my LAMP server?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by apantev on 2010-03-12
I set up a LAMP server using tasksel and it works great, but I'm not sure about much of the specifics of it. It just works and I have not had a need to find out much about it. So I was wondering if installing updates through the update manager could possible break my LAMP server and if so what types of updates should I look for that could break it?

---

### Post by Mighty_Joe on 2010-03-12
There is no limit to the amount of screwing up a computer can do.  Even if you do nothing, it can break.  
A good administrator will have backups, a disaster recover plan and, if possible, redundant servers for running tests (this is why virtualization has become very popular).

---

### Post by tgalati4 on 2010-03-12
Server updates are usually security-related, so it's a good idea to stay current.  Breakage can happen, but it's rare.

If a kernel update breaks, you can always boot an older kernel in grub.  If an apache2 update breaks, then that's a regression.  Send in your log files  and file a bug to fix it.

---

