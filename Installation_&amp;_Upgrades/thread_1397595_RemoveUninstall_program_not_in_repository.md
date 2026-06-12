---
title: "Remove/Uninstall program not in repository"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by sportsdude81 on 2010-02-03
After the upgrade from jaunty to karmic I have a couple of programs that don't even run and are not in the repository.  I was wondering if there was a quick way to uninstall/remove these w/o going to each folder and deleting everything. Specifically ConvertIT.  It is no longer in the Medibuntu repository. Thanks in advance.

---

### Post by gmargo on 2010-02-03
What have you tried?  One or more of these should work:
```

aptitude purge ConvertIT
apt-get --purge remove ConvertIT
dpkg --purge ConvertIT

```

---

### Post by sportsdude81 on 2010-02-04
Thanks.  Wasn't sure if purge tag was the right way to go about it.  Just FYI apt-get doesn't work it just says package not found.  
```
sudo dpkg --purge ConvertIT
```
worked for me.  Thanks again

---

