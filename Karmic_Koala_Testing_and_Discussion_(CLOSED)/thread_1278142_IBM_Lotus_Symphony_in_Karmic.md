---
title: "IBM Lotus Symphony in Karmic"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2009-09-29
Hello all

Has anyone managed to get Symphony installed and running in Karmic? I've tried both the deb from IBM's website (tagged Hardy) and the deb from Ubuntu's Jaunty partner repo. Both installs fail, reporting -

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
```

I expect Symphony will get packaged into the Karmic partner repo eventually. Just wondered if anyone has a quicker route!

Cheers
Roger

---

### Post by blakamin on 2009-09-29
[http://ubuntuforums.org/showthread.php?t=1273828]("http://ubuntuforums.org/showthread.php?t=1273828")

and the [bug]("https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953")

try the CLI version in the bug comments.

---

### Post by rogerdean on 2009-09-29
Thanks!

```
sudo dpkg -i symphony_1.3-1jaunty1_i386.deb
```

...worked perfectly

Cheers
Roger

---

