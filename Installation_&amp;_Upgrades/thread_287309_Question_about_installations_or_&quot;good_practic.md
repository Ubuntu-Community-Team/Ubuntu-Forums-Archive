---
title: "Question about installations or &quot;good practices&quot; tips"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by javierfh on 2006-10-28
hello,

today i just installed Edgy and so far seems more stable for me than dapper. Probably i had some application in dapper that was messing things and now when doing clean instalation things are much better.

But, i have noticed, that in my home directory there are lots of hidden folders from applications. It might be that i was installing them in the wrong place, but then for future, where do you install new applications as for example google earth or jalbum or other that you download and are not controlled by synaptics. Is there some particular/preferred folder where to install?Or what would be good practice installing applications?

My question it is because i was expecting to have only personal data in /home partition, so was hoping to do a clean installation, but then i have noticed that in /home still had some applications.

Thanks in advance,

Javi

---

### Post by lloyd_b on 2006-10-28
When you talk about "hidden" folders, are you referring to folders with a period at the beginning of the name?  If so, you probably don't have any choice about them.  Almost all applications that need to store user-specific information use such files in the user's home directory.

That's one reason that some people recommend having "/home" on a separate filesystem - so if the home directories grow out of control it won't overflow the root filesystem.

The applications themselves (the executables) are normally stored elsewhere - typically "/usr/bin" or "/usr/local/bin".

It's generally a good policy to periodically check your home directory for such files/directories, and delete any for applications that you've removed from the system.  Other than that, there's not much you can do about them, as if you delete them, the next time you run the associated application, it will usually just recreate it.

Also be aware that some of those entries (".Xauthority" and friends, for example) are necessary for the operation of X-windows and the desktop!  Don't delete anything unless you know for certain what it was for.

Lloyd B.

---

