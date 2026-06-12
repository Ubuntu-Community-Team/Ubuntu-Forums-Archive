---
title: "Packages are a nightmare!"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by Mazehero55 on 2006-08-22
here's what is happening on my system with my packages.

I run game.deb :  dependency game-data.deb not met

So I run game-data.deb : dependency game.deb not met


It's asking me for a package that it's dependent on yet that pasckage is dependent on it itself. So how am I supposed to install this stuf.

and how do I fix  broken cache?

---

### Post by amohanty on 2006-08-23
Do both :)
sudo dpkg -i game.deb game-data.deb

> how do I fix broken cache?

The easiest way is to fire up synaptic (System->Administration->Synaptic...)
Click on the **Custom** button at the bottom left corner, and then select broken in the left pane.
Then completely remove the pkgs listed on the right.


HTH
AM

---

