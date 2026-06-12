---
title: "apt-get vs update-manager"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by kellemes on 2008-03-05
Can anyone explain to me..
I'm on Debian and apt-get tells me the following..
```
The following packages have been kept back:
  deluge-torrent
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```

But.. the update manager shows me there are updates, namely deluge-torrent.

Why is apt-get keeping this package back and update-manager isn't?

---

### Post by PmDematagoda on 2008-03-05
In order to actually "update" using apt-get you need to execute:-
```
sudo apt-get upgrade
```
in update-manager, this is done pretty much automatically.

---

### Post by jimv on 2008-03-05
If I had to guess, I'd say it's because you installed that package manually.  I installed a package manually, and apt-get doesn't update it, but Update Manager does.

---

### Post by hyper_ch on 2008-03-05
if it was hold back, try apt-get dist-upgrade

---

### Post by kellemes on 2008-03-05
> **PmDematagoda said:**
> In order to actually "update" using apt-get you need to execute:-
```
sudo apt-get upgrade
```
in update-manager, this is done pretty much automatically.

That's what I did obviously ;-)
A couple of packages were upgraded but deluge was kept back after doing...
```

sudo apt-get update
sudo apt-get upgrade

```

2 minutes later update-manager told me there is an update for deluge..
And again trying apt-get.. deluge **still** was kept back.
update-manager simply upgraded deluge.

@jimv: it was not installed manually, it's from an official repository.

@hypper_ch: maybe you're right.. but does this mean update-manager is constantly doing a dist-upgrade?

---

### Post by hyper_ch on 2008-03-05
> **hyper_ch said:**
> if it was hold back, try apt-get dist-upgrade <--

---

### Post by PmDematagoda on 2008-03-05
Not entirely sure about this, but did you try:-
```
sudo apt-get upgrade deluge-torrent
```

---

### Post by jimv on 2008-03-05
You can always

sudo apt-get remove --purge deluge-torrent

and then

sudo apt-get install deluge-torrent

I can't imagine that not fixing it.

---

