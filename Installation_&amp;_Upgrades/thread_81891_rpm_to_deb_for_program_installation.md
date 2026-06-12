---
title: "rpm to deb for program installation"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by bluefuse on 2005-10-25
how can I change a rpm file to a deb file so I can install an application?

---

### Post by Leif on 2005-10-25
sudo alien foo.rpm
sudo dpkg -i foo.deb

---

### Post by bluefuse on 2005-10-25
when you say sudo alien foo.rpm do you mean sudo packagename.rpm
                                                                           sudo dpkg -i packagename.deb

and how can I keep a copy once the conversion is done so I can host it on my file server?

---

### Post by Leif on 2005-10-25
sorry, yes, foo means whatever your package name is. so in your words :

sudo alien packagename.rpm
sudo dpkg -i packagename.deb

and the deb file you created will still be there after you install it.

---

### Post by az on 2005-10-25
...and if it does not work after you successfully install it, it is because it was an rpm....  You can always go and get the source code and build the app yourself.

---

### Post by blu.gecko on 2005-10-25
[QUOTE=azz]...and if it does not work after you successfully install it, it is because it was an rpm....  You can always go and get the source code and build the app yourself.[/QUOTE]

and how do you exactly do that?:o

---

### Post by Leif on 2005-10-25
[QUOTE=blu.gecko]and how do you exactly do that?:o[/QUOTE]

usually, something like this :

1. tar xzvf packagename.tar.gz
2. cd to folder just extracted
3. ./configure
4. make
5. sudo make install

you will need gcc to do this (sudo apt-get install build-essential).

---

### Post by munkymonkjr on 2005-10-25
you can do it in one step. 

alien -i package.rpm ;)

---

