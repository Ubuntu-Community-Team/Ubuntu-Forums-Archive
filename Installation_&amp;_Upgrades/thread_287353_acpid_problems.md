---
title: "acpid problems"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by astronouth7303 on 2006-10-28
I just upgraded to edgy on my server, and I had the idea of having acpid use upstart. Now acpid is broken (or maybe it was before, I'm not sure).

"sudo /etc/init.d/acpid start" shows nothing, and no acpid process appears.

If I run acpid from bash, it says it can't find "/proc/acpid".

I believe that the kernel is missing the right modules. Is there a good way to check this?

How do I fix the problem here?

---

