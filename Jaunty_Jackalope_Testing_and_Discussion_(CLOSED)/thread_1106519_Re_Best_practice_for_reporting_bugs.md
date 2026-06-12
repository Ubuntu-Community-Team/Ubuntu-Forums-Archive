---
title: "Re: Best practice for reporting bugs"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-03-25
Is using [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) to get -dbgsym packages fully equivalent (in terms of getting a useful stack trace) to recompile a package like

```
DEB_BUILD_OPTIONS="nostrip noopt" fakeroot apt-get -b source <package>
```

?

---

