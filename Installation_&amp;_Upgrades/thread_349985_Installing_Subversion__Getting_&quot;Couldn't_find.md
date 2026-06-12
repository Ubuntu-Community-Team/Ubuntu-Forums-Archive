---
title: "Installing Subversion:  Getting &quot;Couldn't find package subversion&quot;"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by mattc58 on 2007-01-31
Hello Friends,

I've got a new Ubuntu 6.10 Server instance running at a VPS hosting provider and I'm trying to install Subversion with no luck.

I'm typing "sudo apt-get install subversion" and it's coming back with:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package subversion

I've tried a few other packages (subversion_tools, postgresql) and I've gotten the same thing.

Any ideas here?  The machine has proper net connectivity and has updating itself through apt-get before so I'm a bit stumped.

Thanks,

Matt

---

### Post by mattc58 on 2007-01-31
And never mind!  I did a apt-get update followed by the apt-get install subversion and we're good to go.

---

### Post by avalez on 2008-03-14
And for me it was also necessary first to uncomment all repositories in /etc/apt/sources.list, because they were commented out by installer, because of no internet connection during installation.

---

