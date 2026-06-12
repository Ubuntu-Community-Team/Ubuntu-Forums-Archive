---
title: "broken packages : linux images not found"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by dbcityl on 2013-01-13
installing &removing programs through software center always fail, lately.

I'm new to using a terminal, but have been reading a lot of posts lately, in order to fix this

i was able to update my 11.10 version through 
```
 sudo apt-get clean  
```and```
sudo apt-get update && sudo apt-get dist-upgrade   
```(in fact I followed the instructions on this thread:
 [http://ubuntuforums.org/showthread.php?t=2043023&highlight=configuring+linux+generic](http://ubuntuforums.org/showthread.php?t=2043023&highlight=configuring+linux+generic) )

Now I get error reports on: 
 linux-image-3.0.0-28-generic 
  linux-image-3.0.0-29-generic 


based on this info &

> Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-
image-3.0.0-28-generic.postrm line 328. i tried:
```
cd /var/lib/dpkg/info
``` ```
sudo rm linux-image-3.0.0-28-generic linux-image-generic linux-generic
```but now it says it can't remove ‘linux-image-3.0.0-28-generic’, because it does not exist.


Now that don't make sense to me.

If it does to you, can you help me with this?

(i've kept a log of all i've been doing, if you want to know, though some of it is in dutch.)

---

