---
title: "quantumGis 0.9.1 - installing from source"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by GOwin on 2008-02-04
'm trying to follow the documentations posted for [compiling QGis 0.8 from source](https://help.ubuntu.com/community/BuildingQuantumGisPoint8FromSource) but using QGis 0.9 instead. However, I keep on failing during compile.

    ./build.sh ${HOME}/apps debug

Issuing this command failed me and when I looked into the qgis directory  I made, there's actually no build.sh in there. I went to the qgis wiki and found a build.sh which I copied to create my own build.sh as follows

    #!/bin/bash
    #
    # A simple script to build QGIS
    #       Tim Sutton 2005
    #
    if [ ! $1 ]
    then
    echo "Usage: ${0} install_prefix"
    echo "e.g."
    echo "${0} \$HOME/apps/"
     exit 1
    fi
    export QTDIR=/usr/local/Trolltech/Qt-4.1.0/
    export PATH=$QTDIR/bin:$PATH
    export LD_LIBRARY_PATH=$QTDIR/lib
    ./autogen.sh --enable-debug --prefix=${1} --with-qtdir=$QTDIR --with-grass=/usr/lib/grass && make && make install


Now, it complains that "./build.sh: line 16: ./autogen.sh: No such file or directory." Obviously, I'm out of my depth here. Am farely new into Linux GIS and I'm trying to see which desktop GIS can I use.   I also checked out your 0.7 instructions but I can't see anything applicable for me. I also read the README and INSTALL and tried to install to follow the instructions there but Ubuntu doesn't have "ccmake"

Could someone please tell me what I'm doing wrong here?

---

### Post by zvacet on 2008-02-05
It looks like your scrip is not executable so 

```
chmod +x** scriptname**
```

For second,yes Ubuntu have ccmake but in synaptic you will find it as** cmake**.

---

### Post by GOwin on 2008-02-05
actually, the "autogen.sh" is missing while build.sh is already executable.

I'm not sure how "autogen.sh" is generated.

---

### Post by Partyboi2 on 2008-02-06
If you want to try install the deb package you could try installing qgis 0.9.0 from [here]("http://www.perrygeo.net/wordpress/?cat=10")
if you don't mind one small step back from 9.1
or if you are still feeling adventurous still you could try the deveolpmental 9.2
If you are wanting the 9.2 you will need to install the current one (qgis 0.8.0) in the gusty repo's then add
[URL="deb:%20http://ppa.launchpad.net/timlinux/ubuntu%20gutsy%20main"]```
deb http://ppa.launchpad.net/timlinux/ubuntu gutsy main
```[/URL]
to your sources.list and then upgrade via apt-get

---

