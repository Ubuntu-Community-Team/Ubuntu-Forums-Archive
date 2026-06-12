---
title: "google-earth error message."
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by WicketKeeper on 2013-01-12
Hi All
I have finally upgraded from 12.04 to 12.10.
Everything seems fine except I cannot update or add packages.
I get the same error message.
It reads...

E: Type 'You' is not known on line 2 in source list /etc/apt/sources.list.d/google-earth.list
E: The list of sources could not be read.

I removed google earth about 8 months ago!
Please folks, how do I make this go away as I really do not feel like doing a fresh install of 12.04.

Thanks Everyone

Keeper

---

### Post by howefield on 2013-01-12
Open a terminal and type the following command

```
sudo rm /etc/apt/sources.list.d/google-earth.list
```

Then

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by WicketKeeper on 2013-01-12
Oh Thank soooo much, it seems to be working finally
Thank You

---

### Post by howefield on 2013-01-12
You are soooo welcome :-)

---

### Post by WicketKeeper on 2013-01-12
Howefield; terminal has finished doing its thing.
It is working perfectly at last.
Just wanted to say Thank You again.
:D):P
Bye

---

