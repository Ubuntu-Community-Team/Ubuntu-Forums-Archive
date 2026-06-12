---
title: "php5-common unmet dependencies"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by altbdoor on 2012-03-21
firstly, hello ubuntuforums

i've been a new user to xubuntu for around 3 months, and have been focusing on moving all my web-related work into xubuntu. 

one of the requirements for my web work is to install a web server. i have followed the installing LAMP for ubuntu tutorial here : [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

i have successfully installed apache and php. now i am moving on to install mysql. on step 4 of installing mysql, or more accurately, running the command :

```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
```i encountered an error as displayed below

```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-mysql: Depends: php5-common (= 5.3.2-1ubuntu4.11) but 5.3.2-1ubuntu4.14 is to be installed
```from what i can see, the current version of php5-common i have at the moment is 5.3.2-1ubuntu4.14, but installation of php5-mysql requires php5-common 5.3.2-1ubuntu4.11. besides that, the synaptic package manager shows that i have php5-common 5.3.2-1ubuntu4.14. 

synaptic package manager img : [http://i.imgur.com/9jyZR.png](http://i.imgur.com/9jyZR.png)

anyone have any idea on how to fix this? do i need to rollback the php5-common version? if so, how? i have to admit that i am still learning and have yet to make/install any files yet.

thank you in advance. regards.

**EDIT1**: info on the computer
```
Linux altbdoor-laptop 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686 GNU/Linux

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

```**EDIT2**: went to ubuntu IRC for solutions. people suggested to use original repo and follow instructions from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). yet to perform these actions. will do later.

**EDIT3:** problem solved. changed my repository to the main server. updated the kernel and many other files. continued with the installation and done. thanks for reading.

---

