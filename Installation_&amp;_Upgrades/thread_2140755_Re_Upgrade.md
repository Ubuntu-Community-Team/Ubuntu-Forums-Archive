---
title: "Re Upgrade"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by mickee384 on 2013-04-30
Maybe a silly question. Is it possible to re run the upgrade to ubuntu 13.04? Like to fix broken system files? Or just fresh install and restore my data? :oops:

---

### Post by ibjsb4 on 2013-04-30
No you can't re-run updates, but what you can do  is try to configure all unconfigured packages.

```
sudo dpkg --configure -a
```

[http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html)

Or try to fix broken packages.

```
sudo apt-get -f install
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Or try to resolve package conflicts

```
sudo apt-get dist-upgrade
```

The man pages are built into your system.  Examples:

```
man dpkg
```

```
man apt-get
```

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by mickee384 on 2013-04-30
Thanks! I will try this and report back. And thanks for the man page part as well.

---

### Post by mickee384 on 2013-04-30
The reason I ask, is I inadvertently upgraded gnome to 3.8 from 3.6. Apparently ubuntu 13.04 is configured to work with the older gnome, so really looking for a way to downgrade gnome 3.8 to 3.6

---

### Post by mickee384 on 2013-05-04
so, in the end I tried booting to the dvd and choosing the re-install ubuntu option. It failed. (too much damage?) in any case I went ahead and started over. Fresh and at 13.04

---

