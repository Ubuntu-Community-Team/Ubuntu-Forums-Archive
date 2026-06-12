---
title: "Latest Karmic Alpha"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dobbie03 on 2009-09-16
How do I upgrade to the latest Alpha without having to download a live cd?

---

### Post by marshmallow1304 on 2009-09-16
According to [this page]("http://www.ubuntu.com/testing/karmic/alpha5") at the Ubuntu website:
> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by QIII on 2009-09-16
My two cents, if anyone is still listening...

While I have had success updating in the past, I would do backups and install Karmic fresh this time around.

Karmic uses GRUB2, which doesn't use things like menu.lst.  Updating rather than installing fresh can leave you in a "legacy" situation with GRUB and menu.lst and some potential problems.

I'm not sure what the ultimate plans are, but I don't think there is going to be a method to "fix" this right away.

---

### Post by Dobbie03 on 2009-09-16
Well has anyone had any major issues in regards to updating?

---

### Post by Eestlane on 2009-09-16
Oh yes, but these should be solved by this moment. I mean the whole packages stuff going on last days.


EDIT: The best time to upgrade would be when Alpha 6 is out! So, tomorrow something.

---

### Post by QIII on 2009-09-16
Do remember that Karmic is still and Alpha and has not even reached the Beta stage ...

It is not recommended as a production environment yet.

---

### Post by slakkie on 2009-09-16
> **QIII said:**
> My two cents, if anyone is still listening...

While I have had success updating in the past, I would do backups and install Karmic fresh this time around.

Karmic uses GRUB2, which doesn't use things like menu.lst.  Updating rather than installing fresh can leave you in a "legacy" situation with GRUB and menu.lst and some potential problems.

I'm not sure what the ultimate plans are, but I don't think there is going to be a method to "fix" this right away.

You can easily switch from grub to grub2. No rocket science. That alone is not a reason not to upgrade. But for now, I would not recommend anyone upgrading to Karmic due to the serious b0rkage which presented itself yesterday.

---

### Post by Geoff918 on 2009-09-16
I have upgraded two systems to the testing version. No problems, no guarantees yours will go as well, however. Such is the way of pre-release versions. It's certainly getting more stable day-by-day. If you want to wait for official release, it's set for October 27th if memory serves.

---

### Post by Dobbie03 on 2009-09-16
I am of two minds, I really want to update yet I am worried about it messing up my system.  

When the Official Release is out can we update via a live update?

---

### Post by Eestlane on 2009-09-16
yes

---

### Post by Paqman on 2009-09-16
If downloading a 700MB LiveCD is a problem, then you might want to reconsider running the development branch. You should be prepared to install a LOT of updates. If it's a bandwidth issue, they're going to kill you.

---

### Post by Dobbie03 on 2009-09-16
Bandwidth isn't an issue, so I just update from the cd?

---

### Post by QIII on 2009-09-16
Against my recommendation vis-a-vis a fresh install of Karmic this time around...

If you want to use the update manager GUI and select upgrade from there

```
gksudo update-manager -d
```


If you just want to use the terminal...

```
 sudo apt-get update && sudo apt-get upgrade
```

```
 sudo apt-get dist-upgrade
```

```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by slakkie on 2009-09-17
> **QIII said:**
> Against my recommendation vis-a-vis a fresh install of Karmic this time around...

If you want to use the update manager GUI and select upgrade from there

```
gksudo update-manager -d
```


If you just want to use the terminal...

```
 sudo apt-get update && sudo apt-get upgrade
```

```
 sudo apt-get dist-upgrade
```

```
 sudo apt-get update && sudo apt-get upgrade
```


Which can be simplified to:

```

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade

```

---

### Post by Dobbie03 on 2009-09-19
Thanks guys but I think I will wait until the official release is availible.

---

