---
title: "Upgrade - Packages kept back .."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Naatan on 2010-03-31
Hi, I upgraded from Ubuntu 9.10 to 10.04 back when it was in alpha 3. My 9.10 was a completely clean installation (I did it this way since the Lucid CD didn't want to boot for me).

I also have an install at work which was a clean install.

So far the clean install works far better than the upgrade, sad to say that I have never been able to dist-upgrade without any problems.. always a hassle.

Anyway, on to me problem, when I try to upgrade 2 packages are being held back.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libgtk2.0-bin update-manager
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

I tried clearing my cache but that didn't work.. anyone know what I can do ?

Thanks

---

### Post by descendent87 on 2010-03-31
Just wait, being held back due to dependency problems. It'll sort itself out eventually

---

### Post by Arand on 2010-03-31
Short answer: **Wait.**

Long:
Most likely a case of required dependencies not being published to the repository mirror, the held back packages will probably be installable once their dependencies are in place. This is not a problem, and waiting is normally the best mitigator.
(c.f. [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434) -- same cause, but describing update-manager instead)

- Arand

---

### Post by Naatan on 2010-03-31
ok thanks guys, I always thought the partial upgrade meant that the upgrade was split in 2 to prevent incompatibilities .. good to know what it really stands for.

---

### Post by cariboo on 2010-03-31
This problem comes up all the time, and you are wrong in your assumption about a partial upgrades. Have a look [here]("http:///ubuntuforums.org/showthread.php?t=1343434") for more info on partial upgrades.

---

### Post by Naatan on 2010-03-31
Thanks cariboo, I got it when Arand linked it .. ;)

---

