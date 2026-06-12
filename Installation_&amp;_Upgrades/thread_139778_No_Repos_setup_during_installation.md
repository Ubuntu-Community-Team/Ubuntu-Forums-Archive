---
title: "No Repos setup during installation"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Maverick88 on 2006-03-04
I just installed Breezy Badger using the "expert mode".   Since I am using encrypted wireless networking, the install script was not able to setup networking during installation.  

I finally got wireless networking up and running.  But I can't update Breezy!  

I noticed that ONLY one repo was setup -- CDROM.

How do I add ON-LINE repos?  What are the URL's?

Rob

---

### Post by Maverick88 on 2006-03-04
I manually modified /etc/apt/sources.list and uncommented the main repos and the major updates repos.  I did a sudo apt-get update and all is good now.

Rob

---

