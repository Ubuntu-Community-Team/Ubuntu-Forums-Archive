---
title: "Installation Error : Showing Disk"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by devanson on 2010-05-18
Recently I downloaded and installed Ubuntu 10.04, but during my installation it shows some Hard Disc Dirty, clean it, like that. The same happened when I installed in my friends laptop.

Solution please....

---

### Post by duke.tim on 2011-10-04
If windows is still installed on the harddisk, you need to start windows up and run chkdsk. I would advise you to run the last option.

read only mode within windows
(if you are using vista or 7 you need to run the command line,CMD, as administrator [right click -> Run As Administrator])
```
chkdsk
```

Basic fix
```
chkdsk /f 
```

*to repair bad sectors add the /r option

```
chkdsk /f /r 
```

______________________________________________________

If you are in linux run the fsck utility
check out the link below

[http://www.snow.nl/dist/xhtmlc/ch03s02.html](http://www.snow.nl/dist/xhtmlc/ch03s02.html)

---

