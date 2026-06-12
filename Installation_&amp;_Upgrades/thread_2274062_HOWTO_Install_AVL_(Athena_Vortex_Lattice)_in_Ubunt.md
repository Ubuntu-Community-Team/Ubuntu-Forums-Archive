---
title: "HOWTO: Install AVL (Athena Vortex Lattice) in Ubuntu"
date: 2015-04-17
forum: Installation &amp; Upgrades
---

### Post by scott96 on 2015-04-17
I searched for too long to find the solution to this so I thought I would make a post so someone else might find it in the future.  There is an old post going over this [http://ubuntuforums.org/showthread.php?t=1182359](http://ubuntuforums.org/showthread.php?t=1182359) but it no longer works.  I was uanble to get the current version (3.35) to build but 3.32 works fine.  Hopefully this saves someone a headache.  And if anyone can get 3.35 built from source let me know.

```
sudo apt-get install build-essential gfortran
wget http://web.mit.edu/drela/Public/web/avl/avl3.32.tgz
tar -xvf avl3.32.tgz
cd Avl/plotlib
cp config.make.gfortran config.make
make
cd ../eispack
gedit Makefile

```


Change ```
FC = ifort
``` to ```
FC = gfortran
```
Comment out ```
DP = -r8
```
Save the Makefile
```
make
cd ../bin
gedit Makefile_gfortran
```

At the top change BINDIR to 
```
BINDIR=/usr/bin/
```
Save the Makefile
```
sudo make -f Makefile_gfortran
```


You can now run AVL from terminal with ```
avl
```

---

