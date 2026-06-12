---
title: "I need to reverse to previous kernel How do I get the linux headers?"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by gertvs on 2007-11-05
I upgraded from Feisty to Gutsy, and thus upgraded to the 2.6.22-14-generic kernel, which causes a failure in my eth0 device. When I boot into 2.6.20-16-generic the problems are gone.
I have no problem with using this kernel, but I need Virtual Box and it wants to rebuild for this kernel.
So I tried to install the linux headers, but cannot find them anywhere for this kernel.
Any suggestions what to do?

---

### Post by Pumalite on 2007-11-05
Someone correct me if I'm wrong, but I think they are not available in the usual repos for Feisty.
Did you run:
sudo apt-get install linux-headers-`uname -r`

---

### Post by gertvs on 2007-11-05
If I run:
sudo apt-get install linux-headers-`uname -r`

I get:

me@mycomputer~$ sudo apt-get install linux-headers-2.6.20-16-generic
[sudo] password for me
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.20-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.20-16-generic has no installation candidate
gert@host:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.20-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.20-16-generic has no installation candidate

I also tried to add the Feisty repositories but to no avail.

---

### Post by az on 2007-11-05
linux-headers-2.6.20-16-generic is in the feisty-security repository.

---

### Post by mikewhatever on 2007-11-05
They can be downloaded as a separate package [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=feisty&release=all)

---

### Post by gertvs on 2007-11-05
Thanks az,
That wasn't very obvious, but you saved my day.

---

### Post by gertvs on 2007-11-05
Thanks to you too Mike, az's hint already solved my problem. I wasn't aware of this package search feature. I'll bear it mind for the next problem ;-)
Thanks

---

