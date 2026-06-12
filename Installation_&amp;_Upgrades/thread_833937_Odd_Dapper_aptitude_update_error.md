---
title: "Odd Dapper aptitude update error"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Riverside on 2008-06-19
Extract from sudo aptitude update output today:

```
Get:8 http://gb.archive.ubuntu.com dapper-updates/main Packages [356kB]
99% [8 Packages gzip 0] [Logging in]
gzip: stdin: not in gzip format
Err http://gb.archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
```

Is anyone else seeing this?

---

### Post by PmDematagoda on 2008-06-19
Do:-
```
sudo apt-get install --reinstall gzip
```
and see if that fixes it.

---

### Post by Riverside on 2008-06-20
> **PmDematagoda said:**
> Do:-
```
sudo apt-get install --reinstall gzip
```
and see if that fixes it.It doesn't appear to have been a gzip issue per se.  The error message reported concerned one specific section of the update data only, the remainder of the update data was downloaded and processed normally.

---

