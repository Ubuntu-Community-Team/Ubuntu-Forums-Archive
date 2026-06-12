---
title: "easier way of installing downloaded .deb packages to offline computer"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2011-04-27
Hi.

I don't have an internet connection at home so I had a little trouble getting packages for my ubuntu. Though I have a working connection at my work the dependency issues make it difficult for a seamless installation. Anyway, I managed to get my hands on an ubuntu with a updated synaptic package manager and generated package download scripts using File > Generate package download script in synaptic's menu bar.

I took the scripts to my online pc at work where i managed to download all the packages including their dependencies. The next thing to do was to open synaptic and use File > Add downloaded packages, where i would select the directory location of the packages and synaptic was supposed to take care of installing the packages. 

The problem is, synaptic doesn't seem to 'recognize' them; the packages are dimmed or non-selectable. The only option I have left is to install the packages and dependencies one by one, which I'm sure you'd appreciate the problem I face here. I made a download for over 30 packages, and including the dependencies I now have over 500 packages and dependencies to install, not to mention the dependency order installation I have to identify and keep. :frown:

Can someone help me out here? My system is a windows 7-Maverick dual boot.

Thanks in advance.

---

### Post by oldos2er on 2011-04-27
Take a look at [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by EthioJOB on 2011-04-28
I did, but there is a new version that came out for ubuntu 10.10 and onwards because these versions of the OS won't allow executables to run. Turns out the procedure is a little bit more complicated and there's a catch to it as well (you'll need Python and PythonGTK+ or something like that on the online computer, something which I have no control over). So as you can see, using generated scritps from synaptic is my only option.

---

### Post by EthioJOB on 2011-04-29
Bump

---

### Post by linuxone on 2011-04-29
Hi,

> **EthioJOB said:**
> I did, but there is a new version that came out for ubuntu 10.10 and onwards because these versions of the OS won't allow executables to run. Turns out the procedure is a little bit more complicated and there's a catch to it as well (you'll need Python and PythonGTK+ or something like that on the online computer, something which I have no control over). So as you can see, using generated scritps from synaptic is my only option.

if you want upgrade your offline system to Natty 11.04 use the CD installation method as described into the [Ubuntu Wiki](https://help.ubuntu.com/community/NattyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD).

Thomas

---

### Post by EthioJOB on 2011-04-30
Well upgrading is something that I will consider for the future. Right now what's bothering me most is my inability to install applications just because I'm offline.

---

### Post by dino99 on 2011-04-30
howto:

- create a special folder where you put all the .deb downloaded for future installation
- then you are ready for installation:
  a) cd to_that_deb_folder
  b) sudo dpkg -i the_deb_package (or sudo dpkg -i * to install them all)

---

### Post by EthioJOB on 2011-05-04
dino99,

I tried you're suggestion and with a little tinkering from the help command, it worked. I copied the folders with the .deb packages to my desktop and entered the command

sudo dpkg -i -R /("folder's location")

-i   is good for installing only one package
-R will include to the whole folder; i.e., it will execute the command to all the .deb packages found in that folder. Only requirement I found was that the folder with the said packages *have* to be copied on the computer.

Anyway, thanks.

---

