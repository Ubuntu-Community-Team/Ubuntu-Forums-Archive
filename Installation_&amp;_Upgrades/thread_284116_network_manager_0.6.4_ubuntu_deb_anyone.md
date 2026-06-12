---
title: "network manager 0.6.4 ubuntu deb anyone?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by RikoW on 2006-10-25
Dear all,

does anybody have a deb package for Dapper of the lastest release of the network-manager (0.6.4)?

I tried to compile from source, but it would complain that the wireless-tool are not installed or not functional. As far as I could tell, they are installed with the proper version, but most likely, the header files are missing. Unfortunately, there is no src or dev package in the repos (at least none I could find).

I have the problem, that network-manager doesn't show me the wireless networks, which are WEP encrypted, or at least not all of them. At work, I see the open guest network, but not the wep encrypted internal one. I can connect to it ok, but have to put all the info (ESSID, key) every time again.
I was hoping, that the last version has a fix for that, since I saw a patch somewhere for the 0.6.2 version addressing exactly that problem.

Thanks and cheers,

                    Riko

---

### Post by lognok on 2006-11-10
Hi RikoW, remember to install 'libiw-dev' and a bunch of other dependencies (I think about 10) that it will ask for during the ./configure process. I configured and compiled it on Edgy and it's working, but not quite the way I want it to, I cannot connect to some networks, which the default network manager in Edgy easily connects to (strange).
Hope you have better luck.

---

