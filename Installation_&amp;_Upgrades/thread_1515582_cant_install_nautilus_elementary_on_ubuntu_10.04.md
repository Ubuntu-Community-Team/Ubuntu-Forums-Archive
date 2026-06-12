---
title: "cant install nautilus elementary on ubuntu 10.04"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by macstar on 2010-06-22
im following this guide:

[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)

but having no success:

adding the ppa in terminal works as does it in synaptics package manager.
when i do update in terminal it seems to update A LOT of things and it takes quite long.

when looking in synaptics package manager for nautilus-elementary it finds nothing!

can someone say me why that is and how to install?


all i could think about is that it could have to do with the fact that i upgraded the kernel to 2.6.34. but can it really be the reason?

---

### Post by stlsaint on 2010-06-22
That command you used did not install anything. You cant upgrade anything that you dont have installed in the first place. You need to find out the package name of that application and install it.

for example:
```
sudo apt-get install nautilus-elementary
```

then you can upgrade via:
```
sudo apt-get upgrade
```

---

### Post by macstar on 2010-06-22
> **stlsaint said:**
> That command you used did not install anything. You cant upgrade anything that you dont have installed in the first place. You need to find out the package name of that application and install it.

for example:
```
sudo apt-get install nautilus-elementary
```then you can upgrade via:
```
sudo apt-get upgrade
```

apt-get- install nautiulus-elementary says that it couldnt find the package...

when i enter:
```

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
```

it gives the message:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 91DB0C47720C152FF466E7BA61E091672E206FF0


then tires to get the key  2E206FF0 from hkp Server keyserver.ubuntu.com 

and its: wait wait wait wait ... nothing happens. it seems to be stuck and i cancel with strg+c. :(

---

### Post by macstar on 2010-06-23
can anyone help? why doesnt the package manager find nautilus-elementary despite me having added all neccessary sources?

---

### Post by macstar on 2010-06-23
in the meantime, i have fixed it by myself. i had to compile it on my own. no idea, why, but at least its working now :)

```

sudo apt-get install bzr
sudo apt-get build-dep nautilus
bzr branch lp:nautilus-elementary
cd nautilus-elementary/
./configure --prefix=/usr && make
sudo make install

```

---

### Post by macstar on 2010-06-23
looks like ive done a big mistake. after killing nautilus all was working fine, i rebooted later now i cant see the desktop anymore!!! it stucks to a black screen, i can see and move the mouse cursor, but thats it about.

CAN ANYONE HELP? how can i uninstall this nautilus-elementary **** (yes, its obviously **** if it destroys the system) and get back to the normal nautilus again which was working just fine.

---

### Post by macstar on 2010-06-24
anyone? its really important!

---

### Post by tg3793 on 2011-06-09
Woah! ... I was just getting ready to install Nautilus Elementary (in Ubuntu 10.04) when I saw this thread. Did you ever get this fixed? It would be a good idea if I knew how you fixed it (before I tried this).

---

