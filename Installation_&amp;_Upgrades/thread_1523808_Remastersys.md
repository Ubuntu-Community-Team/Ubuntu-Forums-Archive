---
title: "Remastersys"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by da_buddar on 2010-07-04
When attempting to install REMASTERSYS i get he following error message:

Error: Dependency is not satisfiable: dialog

what do i need to do to solve this?

Please bare in mind i've had ubuntu for a day and know nothing about computers beyond simple stuff

Cheers 
James

PS i'm using the latest ubuntu at 64bit

---

### Post by sxmaxchine on 2010-07-04
the dependencies mean that you need to install those programs in order for remastersys to work. try googling the name of the dependent item and install them all then you can install remastersys

---

### Post by da_buddar on 2010-07-04
I don't understand what a dependency is and how it effects the installation. 

Am i looking for dependencies of DIALOG or REMASTERSYS or the installer or ubuntu and what format is a dependency and how do you hook it up?

I've had a look in the synaptic package manager for files under dialog but turn a blank when the time come to chose which one.

---

### Post by ronnielsen1 on 2010-07-04
It should install without problems. Where did you get the remastersys you're trying to install? 
You also don't mention what version of Ubuntu you're running.

This is for Ubuntu 10.04

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

From terminal

[COLOR=Red]sudo gedit /etc/apt/sources.list[/COLOR]

Add the following to souces.list  For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up

[COLOR=Red]#  Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

[COLOR=Black]Save file and close[/COLOR]

sudo apt-get update

sudo apt-get install remastersys
[/COLOR]

---

### Post by tomynho on 2010-07-05
> **da_buddar said:**
> When attempting to install REMASTERSYS i get he following error message:

Error: Dependency is not satisfiable: dialog

what do i need to do to solve this?

Please bare in mind i've had ubuntu for a day and know nothing about computers beyond simple stuff

Cheers 
James

PS i'm using the latest ubuntu at 64bit

I have the same problem, except for the fact, that for me the dependency which is not satisfiable is ubiquity.
See this for more details:
[http://ubuntuforums.org/showthread.php?t=1523975](http://ubuntuforums.org/showthread.php?t=1523975)

---

