---
title: "Install something with a git clone?"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by cmpunk on 2008-07-19
I need to install this microdia webcam driver and here are the directions:
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia
make
sudo insmod ./microdia.ko

And then:
sudo install -d /lib/modules/`uname -r`/misc
sudo install microdia.ko /lib/modules/`uname -r`/misc
sudo depmod -a

When I tried "git clone http://repo.or.cz/r/microdia.git" it said command git not found.
So then after that, i install git-core. So then I ran "git clone http://repo.or.cz/r/microdia.git" again, but it said:

/usr/bin/git-clone: 310: curl: not found
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?

Can someone help me?

---

### Post by Partyboi2 on 2008-07-20
try
```
sudo apt-get install git-core gitk git-gui git-doc curl
```

---

### Post by cmpunk on 2008-07-21
It worked, thanks

---

