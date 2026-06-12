---
title: "update-manager -d doesnt work"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by pjalegria on 2010-03-20
Hi 

I want to upgrade to Lucid Beta 1 but when i try to do "update-manager -d" i have disk space error on /var/cache... can someone help me?

Thanks

---

### Post by wojox on 2010-03-20
Try this in the terminal, clean up:

```
sudo apt-get clean && sudo apt-get autoclean
```

Make sure your up to date:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Then run:

```
sudo update-manager -d
```

---

### Post by pjalegria on 2010-03-20
I have already have made that with no sucess

---

