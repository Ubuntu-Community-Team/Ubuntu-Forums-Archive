---
title: "Installed crashed"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by Scarface on 2006-07-03
Well i did the install but at 97% it crashed. It had an error code but restarted before i had time to save it all...I had WInXP pro on it but did not have any multiloader program to dual boot both winxp and linux..I was told it would work..I'm a noob so what was i suppose to think.... Now when i boot my pc it says invalid system disks....i wish i knew what's going on....any1 help

---

### Post by Jagot on 2006-07-03
Put in your Windows disk and get into the recovery console and when you get to the prompt type:

```
fixmbr
```

Alternatively, you could download a FreeDOS bootdisk from [http://www.freedos.org/](http://www.freedos.org/) and get to the command prompt there and type:

```
fdisk /mbr
```

---

