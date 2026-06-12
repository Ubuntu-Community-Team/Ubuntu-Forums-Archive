---
title: "upgradation of wine"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by lenypl on 2011-09-15
how can i upgrade wine ?now iam using 1.2.2. some applications doesnt work with it like rynga voip.

---

### Post by khelben1979 on 2011-09-15
[Rynga - WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22800").

Wine 1.2.x = stable releases.
Wine 1.3.x = unstable releases.

I guess you could downloaded the latest unstable release and compile from source code, but it is not certain that it works better. You'll find the source code [here]("http://prdownloads.sourceforge.net/wine/wine-1.3.28.tar.bz2").
To compile you go through:

(system libraries checking)
```
./configure
```
(compiles the source code)
```
make
```
(compiles the source code to system binary path)
```
sudo make install
```

In my opinion, I don't think it's worth it for this specific application and you should try with some other application instead, but the choice is free. Also it's recommended to uninstall the old version of Wine before proceeding.

---

### Post by raja.genupula on 2011-09-15
use stable versions to avoid problems . you can choose alternative to wine in this case , they are also good . 

my choice is PlayOnLinux
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

