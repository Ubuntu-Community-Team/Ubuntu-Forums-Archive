---
title: "Refuses to Upgrade"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by Peyton on 2007-11-22
Okay, so, I decided to upgrade today. The upgrader downloaded all the necessary files, but after that, it just quit. Now, when I run Adept, I'm informed that there are over 1,000 updated packages available, but when I try to actually perform the update, I get a lovely error message (attached).

So, what now?

:confused:

---

### Post by taurus on 2007-11-22
Close adept and run these two commands from a terminal to see what happens.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Peyton on 2007-11-22
Ah, saw your post from the other thread. Anyway, here's what happens:

> peyton@Athlon-Mobile:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  digikam: Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.1 is installed
           Depends: libexiv2-0 but it is not installed
           Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is installed
           Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is installed
           Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is installed
           Depends: libjasper1 (>= 1.900.1) but it is not installed
           Depends: libkdcraw1 but it is not installed
           Depends: libkexiv2-1 but it is not installed
           Depends: libsqlite3-0 (>= 3.4.2) but 3.3.13-0ubuntu1 is installed
           Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is installed
           Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is installed
  gwenview: Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.1 is installed
            Depends: libexiv2-0 but it is not installed
            Depends: libstdc++6 (>= 4.2-20070516) but 4.1.2-0ubuntu4 is installed
  kipi-plugins: Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.1 is installed
                Depends: libglib2.0-0 (>= 2.13.5) but 2.12.11-0ubuntu1 is installed
                Depends: libgphoto2-2 (>= 2.3.1) but 2.3.0-0ubuntu4 is installed
                Depends: libgphoto2-port0 (>= 2.3.1) but 2.3.0-0ubuntu4 is installed
                Depends: libgpod2 but it is not installed
                Depends: libkcal2b (>= 4:3.5.7) but 4:3.5.6-0ubuntu6 is installed
                Depends: libkdcraw1 but it is not installed
                Depends: libkexiv2-1 but it is not installed
                Depends: libstdc++6 (>= 4.2-20070516) but 4.1.2-0ubuntu4 is installed
                Depends: libxml2 (>= 2.6.29) but 2.6.27.dfsg-1ubuntu3 is installed
  libice-dev: Depends: libice6 (= 2:1.0.3-3) but 2:1.0.3-1build1 is installed
E: Unmet dependencies. Try using -f.

---

### Post by taurus on 2007-11-22
Try

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Peyton on 2007-11-22
Success! Thank you.

---

