---
title: "qgis download and install"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by Newmanthomsonk on 2013-02-03
Sir 

        I need to download and install qgis on my ubuntu 10.4 pls help

---

### Post by Cheesemill on 2013-02-03
Have you read the instructions?
[http://hub.qgis.org/projects/quantum-gis/wiki/Download#26-Ubuntu](http://hub.qgis.org/projects/quantum-gis/wiki/Download#26-Ubuntu)

For the stable version...
```
echo "deb     http://qgis.org/debian lucid main" | sudo tee -a /etc/apt/sources.list
gpg --keyserver keyserver.ubuntu.com --recv 997D3880
gpg --export --armor 997D3880 | sudo apt-key add -
sudo apt-get update
sudo apt-get install qgis
```

For the latest version...
```
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install qgis
```

---

