---
title: "installation error"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by aashu4 on 2012-02-14
Hi, I am trying to install tinyOS 2.1.1 on Ubuntu 10.10 and facing this error. Any help would be appreciated

$ sudo apt-get install tinyos-2.1.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
[B]
The following packages have unmet dependencies:
 tinyos-2.1.1 : Depends: tinyos-required-all but it is not going to be installed or
                         tinyos-required-msp430 but it is not going to be installed or
                         tinyos-required-avr but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/B]

---

### Post by tamkt on 2012-02-14
You try
sudo apt-get install tinyos-*

---

### Post by aashu4 on 2012-02-14
Tried that. The following error is shown

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 deputy-tinyos : Depends: nesc but it is not installable
 msp430-optional-tinyos : Depends: msp430-tinyos but it is not installable
 tinyos-optional-all : Depends: msp430-tinyos-optional but it is not installable
                       Depends: avr-tinyos-optional but it is not installable
 tinyos-required-avr : Depends: nesc but it is not installable
 tinyos-required-msp430 : Depends: msp430-tinyos but it is not installable
                          Depends: nesc but it is not installable
 tinyos-tools : Depends: nesc but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by tamkt on 2012-02-14
You try link
[http://alkautsarpens.wordpress.com/2008/04/30/install-tinyos-2x-on-ubuntu/](http://alkautsarpens.wordpress.com/2008/04/30/install-tinyos-2x-on-ubuntu/)

Or
[http://blog.aguskurniawan.net/post/Deploying-TinyOS-on-Ubuntu-1010.aspx](http://blog.aguskurniawan.net/post/Deploying-TinyOS-on-Ubuntu-1010.aspx)

Source
[http://tinyos.stanford.edu/tinyos/dists/ubuntu/](http://tinyos.stanford.edu/tinyos/dists/ubuntu/)

---

