---
title: "The unconventional alpine install (PINE mail client)"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Poyntz on 2008-11-14
This wasn't solved on another thread so I thought I'd help some people out.
Here's a simple tutorial to install alpine if apt won't let you install alpine because it thinks **libssl** and **libldap** don't exist.

First you should make sure you've got some recommended/necessary files:
```
sudo apt-get install libkrb53 libldap-2.4-2 libncurses5 libpam0g aspell

```

Now you'll probably need to download libssl0.9.7:
```
wget http://ftp.au.debian.org/debian/pool/main/o/openssl097/libssl0.9.7_0.9.7k-3.1etch1_i386.deb
```
(*Not sure why it's not satisfied with libssl0.9.8, but for me having the library alone didn't achieve anything*)

Install the package
```
sudo dpkg -i libssl0.9.7_0.9.7k-3.1etch1_i386.deb
```

Install exim4
```
sudo apt-get install exim4 && sudo apt-get -f install
```
If your ubuntu OS acted anything like mine exim4 won't install because ubuntu doesn't want to recognise libldap. Doing **sudo apt-get -f install** should fix this. 

Finally install alpine
```
sudo apt-get install alpine
```
(If you get some message saying there was a failed dependency try **sudo apt-get -f install** again)

Hope this helps. If it doesn't please explain **your** problem

---

