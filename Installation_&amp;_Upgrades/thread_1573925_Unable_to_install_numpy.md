---
title: "Unable to install numpy"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-09-13
I am running Ubuntu 10.04 (64-bit) with python 2.6 and have had great difficulties with the installation of numpy and matplotlib (matplotlib needs numpy). 

I have tried several different approaches --- but unsuccessful still.

I have downloaded the following:

* **python-numpy_1.4.1-4_amd64.deb**
* **python-numpy_1.5.0-1ppa1_amd64.deb**
* **numpy-1.5.0.tar.gz**

and,

* **matplotlib_0.99.3-1ubuntu1.debian.tar.gz**
* **matplotlib_0.99.3.orig.tar.gz** 
* **matplotlib-1.0.0.tar.gz**

(I gave up on matplotlib 1.0.0)

How can I install numpy with matplotlib? I have attached a python script to test the installation.

Help would be appreciated, greatly.

---

### Post by virsto on 2010-09-14
Ok,
I now have the latest numpy and matplotlib up and running on my Ubuntu 10.04 64-bit system. Some preliminary testing indicates things are working as they should. I am now summarizing what Eric Firing posted to the matplotlib user group on this, so that others might benefit from his expertise (as I have):
 
**# Thanks to Eric Firing ([EMAIL="efiring@hawaii.edu"]efiring@hawaii.edu[/EMAIL]) who is a member **
**# the matplotlib ****user group for this clever use of Linux commands **
**# to solve my problem :-)**
**#**
**# Lets "clean the slate" before a reinstallation (if you believe older**
**# versions are present)**
```
sudo rm -rf /usr/local/lib/python2.6/dist-packages/matplotlib*
sudo rm -rf /usr/local/lib/python2.6/dist-packages/pylab*
sudo rm -rf /usr/local/lib/python2.6/dist-packages/mpl_toolkits/mplot3d
sudo rm -rf /usr/local/lib/python2.6/dist-packages/mpl_toolkits/axes_grid
sudo rm -rf /usr/local/lib/python2.6/dist-packages/mpl_toolkits/axes_grid1
sudo rm -rf /usr/local/lib/python2.6/dist-packages/mpl_toolkits/axisartist
sudo rm  /usr/local/lib/python2.6/dist-packages/mpl_toolkits/*.py
 

```**# Install all the dependencies (installs an old version of numpy)**
```
sudo apt-get build-dep python-matplotlib 

```**# Now to get rid of the old version of numpy**
```
sudo apt-get remove python-numpy 

```
**# Download the latest numpy tar, untar it, then navigate to**
**# where setup.py for numpy is located and give the following commands**
```
python setup.py build
python setup.py install 

```
**# Repeat the previous for matplotlib (download tar, untar it, etc.)**
```
python setup.py build
python setup.py install

```
and th-th-tha-that-that's all folks!
 
--V

---

### Post by jrb114 on 2011-06-01
Well, early 12 months later, a reply.

Thanks for that, I found it really useful!

J

---

### Post by amorriso on 2012-03-09
Worked 1st time. Much appreciated.

---

