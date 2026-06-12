---
title: "Download-only option for Ubuntu 6.10?"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by elreteipos on 2007-04-18
Is there a way to download all the packages needed for Ubuntu 6.10, but perform the actual upgrade later?

---

### Post by Jeremy23 on 2007-04-19
Yep, if you use the command-line. First, edit your sources.list file:

```
$ gksu gedit /etc/apt/sources.list
```

Do a search-and-replace, and change all occurances of your current distro version (e.g. "dapper") to the one you will be upgrading to (e.g. "edgy"). Hit Save, and quit.

Then,

```
$ sudo apt-get update
```

If you're connected to the 'net, that should work without a problem. Next step:

```
$ sudo apt-get -d dist-upgrade
```

This will download all required packages.

When you're offline, run:

```
$ sudo apt-get dist-upgrade
```

(or just remember to take the "-d" out of the command)

I hope that helps.

---

### Post by ekravche on 2007-04-19
[COLOR="Red"]**Actually it's recommended that you don't do that!**[/COLOR] Read [http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599) for more details of how to upgrade.

> **Jeremy23 said:**
> Yep, if you use the command-line. First, edit your sources.list file:

```
$ gksu gedit /etc/apt/sources.list
```

Do a search-and-replace, and change all occurances of your current distro version (e.g. "dapper") to the one you will be upgrading to (e.g. "edgy"). Hit Save, and quit.

Then,

```
$ sudo apt-get update
```

If you're connected to the 'net, that should work without a problem. Next step:

```
$ sudo apt-get -d dist-upgrade
```

This will download all required packages.

When you're offline, run:

```
$ sudo apt-get dist-upgrade
```

(or just remember to take the "-d" out of the command)

I hope that helps.

---

### Post by Jeremy23 on 2007-04-19
From the post:

> Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

How is it hacky, if that's the way Debian has done that for years?

---

