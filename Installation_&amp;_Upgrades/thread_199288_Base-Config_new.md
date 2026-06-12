---
title: "Base-Config new???"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by lightboltz on 2006-06-18
Hi,

I am trying to do a debootstrap installation of Dapper. The problem is the the base-config no longer exists.

A saw a post from a developer the other day saying that Locales do the same thing now. But how??

Can somene please explain me how to do the same base-config did.

Thanks

---

### Post by Caiwyn on 2006-06-20
I am having the exact same problem.  The instructions for installing Ubuntu from debootstrap are here:

[http://doc.ubuntu.com/ubuntu/install/i386/apds03.html](http://doc.ubuntu.com/ubuntu/install/i386/apds03.html)

They still instruct the user to run "base-config new" in order to set locale, create the first user, and select apt sources.  However, the base-config command is not installed by debootstrap.

Can someone clarify why this is?

---

### Post by Caiwyn on 2006-06-21
I take it no one knows how to finish the install now?  base-config is deprecated, it would be nice to find instructions on how to finish that part of an install with Dapper.

---

### Post by octoberdan on 2007-05-07
I'm also looking for some way to automate the configuration at the end. Anyone know?

The Feisty manual install doc may come in handy though if you don't mind configuring by hand:
[http://elibrary.fultus.com/technical/index.jsp?topic=/com.fultus.ubuntu.guides/guides/7_04/install-guide-386/apds04.html](http://elibrary.fultus.com/technical/index.jsp?topic=/com.fultus.ubuntu.guides/guides/7_04/install-guide-386/apds04.html)

Note: What I'm trying now is:
```

apt-get install language-pack-en
apt-get install ubuntu-standard

```

---

