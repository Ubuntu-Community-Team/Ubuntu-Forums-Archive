---
title: "Problem installing libapache2-mod-php5"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by ishu161 on 2012-01-21
So I was installing LAMP (I installed everything separately). Problem is, I keep getting stuck at this message while installing libapache2-mod-php5:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mod-php5 : Depends: php5-common (= 5.3.5-1ubuntu7) but 5.3.5-1ubuntu7.4 is to be installed
E: Broken packagesI found some solutions via Google, like apt-get update, and using the -f option. Nothing has worked so far. I'd appreciate any help. :)

I'm using Natty.

---

### Post by raja.genupula on 2012-01-22
open your synaptic manager and at the bottom read message . then try to fix that broken packages from there .

or

in terminal 

sudo apt-get install -f

give me that output here 

thank you.

---

### Post by ishu161 on 2012-01-23
Hi! Sorry for the late reply.

I don't get any message as I open the Synaptic Package Manager. 

Sudo apt-get install -f gives this output:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  git-man liberror-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks!

---

### Post by raja.genupula on 2012-01-23
ok now try again to install that required package .

let us know what you got .

---

### Post by raja.genupula on 2012-01-23
look for that required dependencies packages from ubuntu packages and install them

sudo dpkg -i name.deb

---

### Post by ishu161 on 2012-01-23
Hi
So I guess the problem was that the dependency php-common was the one conflicting. I removed it from synaptic, and tried again, and there was no problem! :D

Thanks for helping me out!

---

