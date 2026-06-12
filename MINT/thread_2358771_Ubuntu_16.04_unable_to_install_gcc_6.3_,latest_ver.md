---
title: "Ubuntu 16.04 unable to install gcc 6.3 ,latest version"
date: 2017-04-17
forum: MINT
---

### Post by deepakdeshp on 2017-04-17
[COLOR=#333333][FONT=Verdana][FONT=inherit][FONT=&amp]Hello,
vmware is prompting me to install gcc6.2 otherwise vmware will not start. I followed [https://gist.github.com/application2000/73fd6f4bf1be6600a2cf9f56315a2d91#file-how-to-install-latest-gcc-on-ubuntu-lts-txt-L25](https://gist.github.com/application2000/73fd6f4bf1be6600a2cf9f56315a2d91#file-how-to-install-latest-gcc-on-ubuntu-lts-txt-L25)
The error I got is
[FONT=inherit][B]
: > [SELECT ALL]("https://forums.linuxmint.com/viewtopic.php?f=47&t=243919#")[/B]> 
   Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++-6 : Depends: gcc-6-base (= 6.2.0-3ubuntu11~16.04) but 6.2.1-7ubuntu1~16.04.york0 is to be installed
         Depends: libstdc++-6-dev (= 6.2.0-3ubuntu11~16.04) but it is not going to be installed
 gcc-6 : Depends: cpp-6 (= 6.2.0-3ubuntu11~16.04) but it is not going to be installed
         Depends: gcc-6-base (= 6.2.0-3ubuntu11~16.04) but 6.2.1-7ubuntu1~16.04.york0 is to be installed
         Depends: libgcc-6-dev (= 6.2.0-3ubuntu11~16.04) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
uma@mint-18-uma ~ $ sudo apt install gcc-6-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-6-base is already the newest version (6.2.1-7ubuntu1~16.04.york0).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
uma@mint-18-uma ~ $ sudo apt install cpp-6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cpp-6 : Depends: gcc-6-base (= 6.2.0-3ubuntu11~16.04) but 6.2.1-7ubuntu1~16.04.york0 is to be installed
E: Unable to correct problems, you have held broken packages.
uma@mint-18-uma ~ $ sudo apt install gcc-6-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-6-base is already the newest version (6.2.1-7ubuntu1~16.04.york0).
0 upgraded, 0 newly installed, 0 to remove and 0 [/FONT]> 
Thanks for any pointers...
Deepak[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by howefield on 2017-04-17
Thread moved to the "*MINT*" forum and font reset to default.

---

### Post by deepakdeshp on 2017-04-24
Any pointer please?

---

### Post by mc4man on 2017-04-25
You linked, (and used I guess),  a guide  that uses the toolchain ppa. But you've also added & used another ppa for gcc-6.x 
Better to use just one ppa for this. I'd remove all the ....york0 packages, then try again from the toolchain ppa only

---

