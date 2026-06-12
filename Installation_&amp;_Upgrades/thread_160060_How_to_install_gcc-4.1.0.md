---
title: "How to install gcc-4.1.0"
date: 2006-04-14
forum: Installation &amp; Upgrades
---

### Post by Rudie Britz on 2006-04-14
Hi

I want to upgrade the gcc-4.1.0 to install MPlayer
#

1.Extract the archive with

tar -xvzf gcc-core-XXX.tar.gz

#

2.GCC is not built inside the source directory itself like most programs, but needs a build directory outside the source directory. Thus you need to create this directory via

mkdir gcc-build

#

3.Then you can proceed to configure gcc in the build directory, but you need the configure from the source directory:

cd gcc-build
../gcc-3.XXX/configure

#

4.Compile GCC by issuing this command in the build directory:

[COLOR="Red"]make[/COLOR] bootstrap

#

5.Now you can install GCC (as root) by typing

[COLOR="Red"]make install[/COLOR]

The "MAKE" command do not work on this linux.I want to install it.I unzip it and finnish the firts tree steps.But where the make command came from?  so how can i install it .I want to install MPlayer

---

### Post by localzuk on 2006-04-14
Why do you *need* an external compiler? Why not install the gcc4 available from the repositories?

To do this, simply install the 'build-essential' package via synaptic, adept, aptitude or apt-get.

---

