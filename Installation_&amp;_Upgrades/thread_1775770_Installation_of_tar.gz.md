---
title: "Installation of tar.gz"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by pottsiex5 on 2011-06-05
Hi,
I want to install a program from this website [http://www.thc.org/thc-hydra/](http://www.thc.org/thc-hydra/) and i download the option "
[hydra-6.3-src.tar.gz]("http://freeworld.thc.org/releases/hydra-6.3-src.tar.gz")"

i tried following the instructions on this page: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

but when i get to the ./configure step it says "bash: ./configure: No such file or directory"

can anyone explain how to install this please?
thankyou

---

### Post by squaregoldfish on 2011-06-05
The tar.gz file is an archive containing lots of files (similar to a zip file). You have to extract the files before you can use it.

```
tar xzf <filename>
```

This will create a directory next to the tar.gz file. Enter that directory, and you should find the configure script so you can continue following the instructions.

HTH,
Steve.

---

### Post by pottsiex5 on 2011-06-05
Thanks, that worked, but now i have another question. when i get to the "make install" step i get an error:

strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
cp: cannot create regular file `/usr/local/bin/hydra': Permission denied
cp: cannot create regular file `/usr/local/bin/pw-inspector': Permission denied
make: *** [install] Error 1

how do i get it so that it doesnt deny me permission?
thanks

---

### Post by squaregoldfish on 2011-06-05
You need to have root (administrator) access to install software to the main portions of the operating system. The sudo command will give you temporary access to run a command as root, so you can run

```
sudo make install
```

to get the permission you need.

Note that you'll be asked for your password when you do this.

Steve.

---

### Post by pottsiex5 on 2011-06-05
Hey,
This worked but now i get an error saying that a directory doesnt exist:

strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra || echo OK > /dev/null
cp -f hydra.1 xhydra.1 pw-inspector.1 /usr/local/man/man1
cp: target `/usr/local/man/man1' is not a directory
make: *** [install] Error 1

should i create that directory? and if so what is the command?

Pottsie

---

### Post by squaregoldfish on 2011-06-05
The make install command will create all the directories it needs.

---

### Post by pottsiex5 on 2011-06-05
but thats the thing, running "sudo make install" gives that error:

pottsie@joel-potts:/usr/local/src/hydra-6.3-src$ sudo make install
[sudo] password for pottsie: 
strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra || echo OK > /dev/null
cp -f hydra.1 xhydra.1 pw-inspector.1 /usr/local/man/man1
cp: target `/usr/local/man/man1' is not a directory
make: *** [install] Error 1

---

### Post by pottsiex5 on 2011-06-05
Should i use the chown command to be able to create the folder?

---

### Post by squaregoldfish on 2011-06-05
Post the result of:

```
ls -l /usr/local/man
```

---

### Post by etherspin on 2011-07-09
Many people seem to have trouble either installing hydra with SSL   support, or getting xhydra working.  I just installed it on Ubuntu 11.04   and I want to share with others.  I gathered most of the installation   procedure from this site: [http://edwincastillo.com/archives/242](http://edwincastillo.com/archives/242). 

Open a terminal.

Prepare for the installation-->

```

sudo apt-get install libssh-dev
sudo apt-get install libgtk2.0-dev
wget -c http://thc.org/thc-hydra/releases/[COLOR=#000000]hydra-6.4-src.tar.gz
wget -c http://www.libssh.org/files/[/COLOR]0.5/libssh-0.5.0.tar.gz

```To be safe we install libssh (hydra has not like the libssh-dev   package that comes with Ubuntu in previous releases)-->

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

