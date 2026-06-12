---
title: "seeking report showing all installed packages"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2008-12-01
How do I get a 'report' that lists all installed packages? I'd prefer a display from one of the apt wrapper GUI's if possible.

I know about dpkg --list, but I'd like to get the
complete description. I've not had much luck with other dpkg options.

---

### Post by Partyboi2 on 2008-12-01
All the packages that are installed are listed in  /var/lib/dpkg/status so try
```
cat /var/lib/dpkg/status |more
```

---

