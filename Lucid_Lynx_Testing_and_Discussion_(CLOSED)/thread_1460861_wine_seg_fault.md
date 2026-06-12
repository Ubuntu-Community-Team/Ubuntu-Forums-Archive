---
title: "wine seg fault"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dslink on 2010-04-23
crashes, no dump file. running latest packages from today in lucid (x64). was a clean install of lucid about a week or two ago, when ever beta2 was released. I had the same version of wine working on karmic x64

dustin@noname:~/Downloads$ wine Continuum040.exe 
Segmentation fault
dustin@noname:~/Downloads$ winecfg 
Segmentation fault

ii  wine                                  1.1.42-0ubuntu2                                 Microsoft Windows Compatibility Layer (dummy
ii  wine1.2                               1.1.42-0ubuntu2                                 Microsoft Windows Compatibility Layer (Binar
ii  wine1.2-gecko                         1.0.0-0ubuntu3                                  Microsoft Windows Compatibility Layer (Web B

---

### Post by dino99 on 2010-04-23
> **dslink said:**
> crashes, no dump file. running latest packages from today in lucid (x64). was a clean install of lucid about a week or two ago, when ever beta2 was released. I had the same version of wine working on karmic x64

dustin@noname:~/Downloads$ wine Continuum040.exe 
Segmentation fault
dustin@noname:~/Downloads$ winecfg 
Segmentation fault

ii  wine                                  1.1.42-0ubuntu2                                 Microsoft Windows Compatibility Layer (dummy
ii  wine1.2                               1.1.42-0ubuntu2                                 Microsoft Windows Compatibility Layer (Binar
ii  wine1.2-gecko                         1.0.0-0ubuntu3                                  Microsoft Windows Compatibility Layer (Web B

so ,few cases: wine installation is corrupted, continnm40.exe is corrupted, ram problem, disk space problem (not enough)

you can save your work under wine then remove .wine and reinstall 1.1.43

---

