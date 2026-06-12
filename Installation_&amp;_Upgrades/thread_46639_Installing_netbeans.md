---
title: "Installing netbeans"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by FreDV on 2005-07-05
Hi everyone!

First off, i'd like to say Ubuntu rocks. I especially like the Debianesque apt-get, without the difficulty of installing the core (which failed for me several times in the past with Debian). 

Hopefully this question is rather trivial:
I have tried to install netbeans by first downloading the binary for linux: netbeans-4_1-linux.bin

I have not been able to install this. I am aware you are supposed to run this file, but when I try, I get the following error:
'The filename "netbeans-4_1-linux.bin" indicates that this file is of type "unknown". The contents of the file indicate that the file is of type "executable".'

What goes wrong here? Is there any other way of installing this? (but then, why is no alternative offered on the netbeans website?)

Thanks a lot!

Fre

---

### Post by FreDV on 2005-07-05
Solved...
For those who find this with google, what I did was:
1. move the .bin file to my home directory
2. open a terminal
3. type: install -v netbeans-4_1-linux.bin netbeans-4.1

This started the installer and the rest is easy.

Fre

---

