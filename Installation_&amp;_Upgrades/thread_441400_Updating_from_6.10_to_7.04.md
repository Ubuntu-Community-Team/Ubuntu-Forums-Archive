---
title: "Updating from 6.10 to 7.04 ?"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by BorgCymru on 2007-05-12
Manamged to get 6.10 installed but now would like to upgrade to 7/04.

is it possable at all ? 

Thanks

---

### Post by jpietari on 2007-05-12
The instructions to do this are at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).

Make sure you read tje warnings before you upgrade.

---

### Post by cryogen on 2007-05-12
> **BorgCymru said:**
> Manamged to get 6.10 installed but now would like to upgrade to 7/04.

is it possable at all ? 

Thanks

If you don't like the terminal, use the Update Manager.  It's the easiest to figure out.

If you'd rather use the terminal (which is my preferred way), run:

```
sudo nano /etc/apt/sources.list
```

and change every instance of 'edgy' to 'feisty' (make sure you get them all!)

Then run the command below.  It works every time for me:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

And answer Y (yes) to the prompt.

Note, this can be a very long process depending on your connection speed.  It takes about three hours on my connection.

---

