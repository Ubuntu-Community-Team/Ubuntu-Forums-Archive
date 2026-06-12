---
title: "Ubuntu 17.04 : Ubuntu Cannot install fonts-lato package ( needed by ruby )"
date: 2017-04-28
forum: Installation &amp; Upgrades
---

### Post by olikaf on 2017-04-28
All is in the title...
I tried to install ruby, but I have an infinite loop on the fonts-lato package.
Same issue if I try to install fonts-lato alone.



```
sudo apt-get install fonts-lato
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fonts-lato
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2693 kB of archives.
After this operation, 12.0 MB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]
Get:1 http://fr.archive.ubuntu.com/ubuntu zesty/main amd64 fonts-lato all 2.0-1 [2693 kB]

```

---

### Post by Xian on 2017-04-28
My first thought would be to try a different mirror ... 

If you tried that ...  possible to install the package directly?

```
$ wget [http://fr.archive.ubuntu.com/ubuntu/pool/main/f/fonts-lato/fonts-lato_2.0-1_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/f/fonts-lato/fonts-lato_2.0-1_all.deb)

$ sudo dpkg -i /path/to/file.deb
$ sudo apt-get install -f
```

---

