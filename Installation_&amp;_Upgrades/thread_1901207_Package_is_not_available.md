---
title: "Package is not available"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by n.jayakumar.24 on 2011-12-28
Hi,
Am completely new to linux OS. As a part of some development work I was asked to  install some packages along with java6-jre. In vain, I was able to install java6-jre to my Ubuntu. I was supposed to install below packages or asked to run below command :) after java installation.

root@ubuntu:~# sudo apt-get install gdebi build-essential dialog nfs-kernel-server libgtk2.0 libxml2 libasound2 libwbxml2.0 portmap realpath fakeroot qemu-kvm binutils-multiarch debhelper  libsdl-gfx1.2-4


But am getting following errors. 

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgtk2.0-0' for regex 'libgtk2.0'
Note, selecting 'libgtk2.0-cil' for regex 'libgtk2.0'
Note, selecting 'libgtk2.0-bin' for regex 'libgtk2.0'
Note, selecting 'libgtk2.0-common' for regex 'libgtk2.0'
Package dialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package gdebi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gdebi' has no installation candidate
E: Unable to locate package build-essential
E: Package 'dialog' has no installation candidate
E: Unable to locate package nfs-kernel-server
E: Unable to locate package libwbxml2.0
E: Couldn't find any package by regex 'libwbxml2.0'
E: Unable to locate package portmap
E: Unable to locate package realpath
E: Unable to locate package fakeroot
E: Unable to locate package qemu-kvm
E: Unable to locate package binutils-multiarch
E: Package 'debhelper' has no installation candidate
E: Unable to locate package libsdl-gfx1.2-4
E: Couldn't find any package by regex 'libsdl-gfx1.2-4'[/HTML]

Thats lot more error for me to search in net to solve it. Thought, I shall get some assistants in this forum to resolve this issue easily.

Note: Am using ubuntu running with VMware player. And java -version return java version "1.6.0_24", which confirms java installation was successful.

Thanks in advance,
Jayakumar.

---

### Post by 2F4U on 2011-12-28
I looked up most of the packages in you list and I am able to find them. What Ubuntu version are you using?

---

### Post by n.jayakumar.24 on 2011-12-28
Am using ubuntu 11.10
Thanks,
Jayakumar.

---

### Post by n.jayakumar.24 on 2011-12-29
Its of no meaning the issue has been solved. :popcorn:. I just installed Synaptic package manager which is not by default comes with 11.10 Ubuntu (In previous versions tool comes along with the Ubuntu) and I went back to terminal, to my surprise the same sudo commands worked without any flaw :p.

---

