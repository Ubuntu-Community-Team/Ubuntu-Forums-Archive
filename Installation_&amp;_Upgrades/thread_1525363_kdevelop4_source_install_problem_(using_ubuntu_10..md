---
title: "kdevelop4 source install problem (using ubuntu 10.4)"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by mintyhippo on 2010-07-06
Hello i am trying to install kdevelop4 IDE in ubuntu 10.4 from source. I was able to get the kdevplatform installed from source, but not kdevelop. I am able to create the make files for kdevelop but when i try the acual install i get the following error:

```
/home/username/src/kdevelop/app/main.cpp: In function ‘int main(int, char**)’:
/home/username/src/kdevelop/app/main.cpp:136: error: ‘defaultSessionId’ is not a member of ‘KDevelop::SessionController’
/home/username/src/kdevelop/app/main.cpp:144: error: ‘defaultSessionId’ is not a member of ‘KDevelop::SessionController’
```the steps i took so far for installation were:
        
```
$ mkdir -p $HOME/src/kdevplatform/build
$ cd $HOME/src/kdevplatform/build
$ cmake .. -DCMAKE_INSTALL_PREFIX=/usr/kde/4
$ sudo make install
``````
$ mkdir -p $HOME/src/kdevelop/build
$ cd $HOME/src/kdevelop/build
$ sudo cmake -DCMAKE_PREFIX_PATH=/usr/kde/4 -DCMAKE_INSTALL_PREFIX=/usr/kde/4 ../
$ make
$ sudo make install
```This is becoming extremely frustrating, especially considering i had spent all day installing the dependancies, which are now just cluttering my system. 
-any help is greatly appreciated, thank you.

---

