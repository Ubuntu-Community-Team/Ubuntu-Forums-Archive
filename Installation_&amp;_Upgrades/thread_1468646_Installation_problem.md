---
title: "Installation problem"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by yani21 on 2010-05-01
Hi guys. I have problem with installing programs. When i try to install something it gives me error that installation could have failed because of an error in the corresponding software package or it was cancelled 
in an unfriendly way. I am new in ubuntu and can't fix that please help.

---

### Post by P4man on 2010-05-01
unfriendly? Maybe you havent been nice to ubuntu and its mad at you :)

its probably the repository being overloaded right now. Try a different mirror from system > administration > software sources > download from
let it reload the sources when it asks you to.

if that doesnt help, open a terminal from applications > accessories and type

```
sudo apt-get update
```

(enter you password)

copy paste the output here.

---

