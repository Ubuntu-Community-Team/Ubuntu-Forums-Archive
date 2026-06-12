---
title: "Need restricted xtras package for ubuntu 12.10"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by ANiK3T on 2012-11-30
I need it urgently pls some one upload it or give me an official download link for it
n ya pls give me a step by step procedure to install it

---

### Post by dino99 on 2012-11-30
extra packages are found by activated  "restricted" repo

you can check it with software sources menu (system settings: use dash to find it)

or edit the sources list:

sudo gedit /etc/apt/sources.list

you might have these lines inside:
(no needs to make dupes indeed)

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal partner 
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal partner 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal  main universe restricted multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main universe restricted multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main universe restricted multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-proposed main multiverse restricted universe  
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) quantal main  
deb-src [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) quantal main  
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free 

save that file when the upgrade is done, then run:

sudo apt-get update
sudo apt-get install -f

---

### Post by howefield on 2012-11-30
[http://packages.ubuntu.com/quantal/ubuntu-restricted-extras](http://packages.ubuntu.com/quantal/ubuntu-restricted-extras)

---

### Post by grahammechanical on 2012-11-30
They are also in the Ubuntu Software Centre. Just search for Restricted Extras and the Centre will give you a choice of installing the Extras for Xubuntu, Kubuntu and Ubuntu. You just click Install.

Remember, this download may bring in Microsoft core fonts. You will be asked to accept the licence agreement. Scroll down the page to find the Accept button.

Regards.

---

