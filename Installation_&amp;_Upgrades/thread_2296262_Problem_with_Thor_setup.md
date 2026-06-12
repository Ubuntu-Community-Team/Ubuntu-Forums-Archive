---
title: "Problem with Thor setup"
date: 2015-09-24
forum: Installation &amp; Upgrades
---

### Post by guastellavalerio on 2015-09-24
Hi everyone,
I am trying to install Thor on linux Ubuntu ( version Trusty tahr). I am following the instructions available on the website of the software (thor). Everything seems fine. I managed to add the following entry in /etc/apt/sources.list 
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main

However,  afterwards, before to continue with the install ,for security reasons is required to run the following lines on the terminal

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

I run them in  one line summing them with && 
and the outcome is 

gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
?: keys.gnupg.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

I do not understand what is  happening, the website does not provide any further explanations and i could not find any threads on this.
Please help me

---

### Post by hubutm20 on 2015-09-24
"keys.gnupg.net: Host not found"
try  gpg --keyserver  keyserver.ubuntu.com --recv 886DDD89

---

