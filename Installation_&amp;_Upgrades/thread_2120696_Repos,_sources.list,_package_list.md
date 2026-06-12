---
title: "Repos, sources.list, package list"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by m666 on 2013-02-27
How can I list all packages from certain repository?
I'd like to check what packages are in partner or extras repos

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

I think there must be some 'apt-something' command to do this :confused:

---

### Post by dino99 on 2013-02-27
the easiest way: use synaptic

---

### Post by schragge on 2013-02-27
+1 to *use synaptic*.
Anything involving command-line would be pretty well... involved, even if using tools like [grep-dctrl(1)](http://manpages.ubuntu.com/manpages/precise/en/man1/grep-dctrl.1.html) or [dpkg-awk(1)](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg-awk.1.html).

E.g. for *partner* this should be something like
```

sed -n 's/^Package: *//p' /var/lib/apt/lists/*partner_binary-*_Packages|sort -u

```

For extras,
```

sed -n 's/^Package: *//p' /var/lib/apt/lists/extras.*main_binary-*_Packages|sort -u

```

The exact syntax depends on what you have in your */etc/apt/sources.list*

---

### Post by m666 on 2013-02-27
It's minimal CLI-install. No synaptic.


@schragge

```
sed -n 's/^Package: *//p' /var/lib/apt/lists/liquorix.net_debian_dists_sid_main_binary-i386_Packages|sort -u
```

Thanks! I don't understand the syntax hahaha but it works.

---

