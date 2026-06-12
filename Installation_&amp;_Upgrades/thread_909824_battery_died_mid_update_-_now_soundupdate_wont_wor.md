---
title: "battery died mid update - now sound/update wont work"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by makewayhomer on 2008-09-03
I was installing an Ubuntu update this week (from the red arrow at the top toolbar) and my battery died. I have since tried to reinstall the updates, but I get an error message. the message is:

[IMG]http://img395.imageshack.us/img395/7052/errorpp9.jpg[/IMG]

I have no idea what this means or what to do - I'm a complete linux newb.

also, my sound is no longer working. the error message I get is 

"no volume control gstreamer plugins and/or devices found". 

could this be related to the above problem? any help?

---

### Post by Pumalite on 2008-09-03
Run:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
Post the outputs.

---

### Post by makewayhomer on 2008-09-04
> **Pumalite said:**
> Run:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
Post the outputs.

I ran all those, tx. this is the final output

Setting up libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) ...

Setting up libsoup2.4-1 (2.4.1-1ubuntu1) ...

Setting up libtiff4 (3.8.2-7ubuntu3.1) ...

Setting up libxml2-utils (2.6.31.dfsg-2ubuntu1.1) ...
Setting up linux-headers-2.6.24-19 (2.6.24-19.41) ...
Setting up linux-headers-2.6.24-19-generic (2.6.24-19.41) ...

Setting up python-libxml2 (2.6.31.dfsg-2ubuntu1.1) ...

Setting up update-notifier-common (0.70.9) ...
Setting up update-notifier (0.70.9) ...

Setting up yelp (2.22.1-0ubuntu2.8.04.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by makewayhomer on 2008-09-04
> **makewayhomer said:**
> I ran all those, tx. this is the final output

Setting up libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) ...

Setting up libsoup2.4-1 (2.4.1-1ubuntu1) ...

Setting up libtiff4 (3.8.2-7ubuntu3.1) ...

Setting up libxml2-utils (2.6.31.dfsg-2ubuntu1.1) ...
Setting up linux-headers-2.6.24-19 (2.6.24-19.41) ...
Setting up linux-headers-2.6.24-19-generic (2.6.24-19.41) ...

Setting up python-libxml2 (2.6.31.dfsg-2ubuntu1.1) ...

Setting up update-notifier-common (0.70.9) ...
Setting up update-notifier (0.70.9) ...

Setting up yelp (2.22.1-0ubuntu2.8.04.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
 I rebooted and noew the resolution is all messed up. I am only using a tiny screen in the middle of the monitor. I have a 12 inch monitor and about 2.5 inches on all sides is not being used. I can however, mouse around to get to the entire desktop.
ugh

---

### Post by Pumalite on 2008-09-04
Get into Recovery Mode and use 'xfix'

---

### Post by makewayhomer on 2008-09-04
> **Pumalite said:**
> Get into Recovery Mode and use 'xfix'

thanks. I think when I boot up I can choose Recovery Mode...but how do I use xfix?

---

### Post by Pumalite on 2008-09-04
When you boot in Recovery Mode; you get a Menu. xfix is the last in the list.

---

