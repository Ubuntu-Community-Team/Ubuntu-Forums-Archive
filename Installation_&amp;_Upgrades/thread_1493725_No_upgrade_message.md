---
title: "No upgrade message"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by jaime2d2 on 2010-05-26
Hi all.

I'm trying to upgrade from 9.10 to 10.04 LTS

I've followed [http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29)

Everything is updated.

But, i don't receive the message "New Ubuntu release..."

Any idea? Will I have to download the entire DVD?

Thank you very much.

---

### Post by masux594 on 2010-05-26
check in the System>Admin>Sources.. third tab, in the bottom of it.. There's a combo.. What do you have on it?

Sysc, A

---

### Post by jaime2d2 on 2010-05-26
It says "Ediciones normales" in spanish, normal o regular editions would be the translation.

---

### Post by masux594 on 2010-05-26
try to choose the "LTS" one, then close it and then open the update manager.. [COLOR=#000000]It seems strange  because it should already work[/COLOR]..

Sysc, A

---

### Post by jaime2d2 on 2010-05-26
I've changed it to LTS but the result is the same.

---

### Post by masux594 on 2010-05-26
Try to type this command 
```
sudo update-manager --dist-upgrade
```Does it tells ypu something?

Sysc, A

---

### Post by jaime2d2 on 2010-05-26
It says everything is updated.

Never mind, i'll try with de CD.

Thank you for your interest

---

### Post by jaime2d2 on 2010-05-26
I tried:

```
sudo update-manager --dist-upgrade
```and it worked.

---

