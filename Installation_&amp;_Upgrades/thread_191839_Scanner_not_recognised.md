---
title: "Scanner not recognised"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by erbedo on 2006-06-08
Hi all. After the upgrade from breezy to dapper my scanner stop working. When i open xsane it sats that i've no devices installed, but on breezy all worked fine.. Any idea?

---

### Post by Ivan Matveich on 2006-06-08
Try these commands:

```

sudo apt-get install sane-utils
scanimage -L

```

Does it list any scanners?

If it does not, run

```

dmesg > log.txt

```

and attach the log.txt to your reply.

---

### Post by erbedo on 2006-06-08
[QUOTE=Ivan Matveich]Try these commands:

```

sudo apt-get install sane-utils
scanimage -L

```

Does it list any scanners?

If it does not, run

```

dmesg > log.txt

```

and attach the log.txt to your reply.[/QUOTE]

No scanners identified  :(

---

### Post by Ivan Matveich on 2006-06-08
Bummer.

You should file a bug at

[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

for package "xsane". Be sure to attach the output from

```

dmesg
sudo lshw
sudo lsusb -v

```

and tell them what kind of scanner you have.

---

