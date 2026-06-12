---
title: "E: xcwcp: subprocess post-installation script  problem"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by kyme on 2008-01-21
everytime i update and install. i get an error msg 

  E: xcwcp: subprocess post-installation script returned error exit status 10

  its been a week now i have tweaking this, but still wont work.. Im a newbie of ubuntu linux..
  Hope you can help me!! im loosing hope :-(
  looks like im not deserving to use ubuntu :-(

---

### Post by Partyboi2 on 2008-01-21
try uninstalling the package then reinstalling it
```
sudo apt-get remove xcwcp
``````
sudo apt-get install xcwcp
```

---

### Post by ei2gsb on 2008-02-19
Remove 2.3-6 first ** sudo apt-get remove xcwcp**

Then try this older version for now 2.3-3  from [http://packages.debian.org/etch/i386/xcwcp/download](http://packages.debian.org/etch/i386/xcwcp/download)

it looks like something is referring to libqt3c102-mt whatever that is, instead of llibqt3-mt

---

