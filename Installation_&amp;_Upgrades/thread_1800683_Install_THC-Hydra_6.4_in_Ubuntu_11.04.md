---
title: "Install THC-Hydra 6.4 in Ubuntu 11.04"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by etherspin on 2011-07-09
Many people seem to have trouble either installing hydra with SSL  support, or getting xhydra working.  I just installed it on Ubuntu 11.04  and I want to share with others.  I gathered most of the installation  procedure from this site: [http://edwincastillo.com/archives/242](http://edwincastillo.com/archives/242). 

Open a terminal.

Prepare for the installation-->

```

sudo apt-get install libssh-dev
sudo apt-get install libgtk2.0-dev
wget -c http://thc.org/thc-hydra/releases/[COLOR=#000000]hydra-6.4-src.tar.gz
wget -c http://www.libssh.org/files/[/COLOR]0.5/libssh-0.5.0.tar.gz

```To be safe we install libssh (hydra has not like the libssh-dev  package that comes with Ubuntu in previous releases)-->

```

tar -xvzf libssh-0.5.0.tar.gz
cd libssh-0.5.0
mkdir build
cd build

```If you don't have cmake-->

```

sudo apt-get install cmake

```Then-->

```

cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=debug ..
make
sudo make install
cd ../..

```Now to extract and install hydra-->

```

tar -xvzf [COLOR=#000000]hydra-6.4-src.tar.gz
cd hydra-6.4-src
./configure
make
sudo make install
[/COLOR]
```[COLOR=#000000]

[/COLOR]Now to install xhydra (though it should be installed with the previous commands)-->

```

cd hydra-gtk
./configure
make
sudo make install

```[COLOR=#000000] 
Start xhydra by opening terminal and-->

```

xhydra

```I hope this helps!
[/COLOR]

---

### Post by Script Warlock on 2011-07-10
> c-make -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=debug ..

is it a little typo? 
cmake instead of c-make

> cd hydra-6.4-src.tar.gz after extracting
cd hydra-6.4-src

to use xhydra
cd hydra-gtk

and needs libgtk2.0-dev

---

### Post by etherspin on 2011-07-10
Thank you!  I have made the suggested changes!

---

### Post by mazzalee on 2013-02-24
> **etherspin said:**
> Many people seem to have trouble either installing hydra with SSL  support, or getting xhydra working.  I just installed it on Ubuntu 11.04  and I want to share with others.  I gathered most of the installation  procedure from this site: [http://edwincastillo.com/archives/242](http://edwincastillo.com/archives/242). 

Open a terminal.

Prepare for the installation-->

```

sudo apt-get install libssh-dev
sudo apt-get install libgtk2.0-dev
wget -c http://thc.org/thc-hydra/releases/[COLOR=#000000]hydra-6.4-src.tar.gz
wget -c http://www.libssh.org/files/[/COLOR]0.5/libssh-0.5.0.tar.gz

```To be safe we install libssh (hydra has not like the libssh-dev  package that comes with Ubuntu in previous releases)-->

```

tar -xvzf libssh-0.5.0.tar.gz
cd libssh-0.5.0
mkdir build
cd build

```If you don't have cmake-->

```

sudo apt-get install cmake

```Then-->

```

cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=debug ..
make
sudo make install
cd ../..

```Now to extract and install hydra-->

```

tar -xvzf [COLOR=#000000]hydra-6.4-src.tar.gz
cd hydra-6.4-src
./configure
make
sudo make install
[/COLOR]
```[COLOR=#000000]

[/COLOR]Now to install xhydra (though it should be installed with the previous commands)-->

```

cd hydra-gtk
./configure
make
sudo make install

```[COLOR=#000000] 
Start xhydra by opening terminal and-->

```

xhydra

```I hope this helps!
[/COLOR]
CMake Error: The source directory "/home" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

whats wrong ?!?
what can i do ?

thanks.

---

### Post by oldos2er on 2013-02-24
Please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

