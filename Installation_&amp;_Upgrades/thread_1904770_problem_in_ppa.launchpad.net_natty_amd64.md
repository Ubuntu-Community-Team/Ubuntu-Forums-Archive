---
title: "problem in ppa.launchpad.net natty amd64"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by bn3232 on 2012-01-05
when I run apt-get update I face following errors. How can I fixthem?


W: Failed to fetch [http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages](http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/natty/main/amd64/binary-amd64/Packages](http://ppa.launchpad.net/dists/natty/main/amd64/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/natty/main/Packages/binary-amd64/Packages](http://ppa.launchpad.net/dists/natty/main/Packages/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dlecan/openjdkclear/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/dlecan/openjdkclear/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dlecan/openjdkclear/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/dlecan/openjdkclear/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntugnometeam/gnome3/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntugnometeam/gnome3/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntugnometeam/gnome3/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntugnometeam/gnome3/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

---

### Post by oldos2er on 2012-01-05
Run ```
gksu software-properties-gtk
``` and under the 'Other Software' tab, uncheck the boxes next to the repositories you don't want. When you're done, run ```
sudo apt-get update
```

---

### Post by spacecheck on 2012-01-05
Or you can click your way through the no longer functional paths until you reach a new functional path for what you need, then edit your /etc/apt/sources.list to reflect the corrected pathways for the ppa software sources you want, if any.

---

