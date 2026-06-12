---
title: "Kickstart with PXE Netboot: url directive not working"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Peturrr on 2011-01-21
I have setup a PXE netboot server for installing Ubuntu. I use a kickstart file to automate the install of the networked machines.

Everything works fine, except for the url directive in the kickstart file that directs to my apt-cacher server:
```
url --url http://localcacheserver:3142/ubuntu
```

This should work, but the localcacheserver never gets hit, instead the installer just directly connects to the ubuntu servers. 

I was wondering, is using netboot/kickstart combination the cause of not being able to use a url directive?

---

