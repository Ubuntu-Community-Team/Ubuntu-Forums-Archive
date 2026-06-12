---
title: "Kernel panic Error"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by firewind2 on 2017-01-05
I updated something I think and now I have " end Kernel panic - not syncing: VFS: Unable to mount roof fs on unknown-block(0,0) ".
I did something has been written on forums but it didn't solve my problem.
Wish you guys help me...

---

### Post by oldos2er on 2017-01-05
Which Ubuntu version are you running? Are you able to boot into a different kernel at the grub menu?

> I did something has been written on forums Which was...? Please give as many details as possible.

---

### Post by firewind2 on 2017-01-05
> **oldos2er said:**
> Which Ubuntu version are you running? Are you able to boot into a different kernel at the grub menu?

 Which was...? Please give as many details as possible.

I don't really remember but it must be v15. And I'm not be able to boot into a different kernel, even with recovery mode. I tried this "[https://ubuntuforums.org/showthread.php?t=1751574](https://ubuntuforums.org/showthread.php?t=1751574)" way but failed at last code.

---

### Post by howefield on 2017-01-05
> **firewind2 said:**
> I don't really remember but it must be v15.

Open a terminal and use the command..

```
cat /etc/*-release
```

to find out which version of Ubuntu you are using and paste the output back here. (for future reference as it seems you cannot right now)

Both 15.* versions are beyond end of life in any case and should be replaced with a supported version.

---

### Post by firewind2 on 2017-01-06
> **howefield said:**
> Open a terminal and use the command..

 ```
cat /etc/*-release
```

 to find out which version of Ubuntu you are using and paste the output back here. (for future reference as it seems you cannot right now)

 Both 15.* versions are beyond end of life in any case and should be replaced with a supported version.

It didn't work.

---

