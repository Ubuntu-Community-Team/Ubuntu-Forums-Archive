---
title: "Upgrade to current release from ver6.10 Edgy"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by esquif on 2008-07-02
My Kubuntu version is quite outdated (6.10 Edgy). Seemingly "apt-get update" no longer works. Below are some of the messages I get:

> 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy/free Translation-en_US
...
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy/free Packages
  404 Not Found [IP: 213.186.45.139 80]
Hit [http://archive.linutop.eu](http://archive.linutop.eu) edgy Release
Hit [http://archive.linutop.eu](http://archive.linutop.eu) edgy-updates Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy/non-free Packages
  404 Not Found [IP: 213.186.45.139 80]
Ign [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports Release
Hit [http://archive.linutop.eu](http://archive.linutop.eu) edgy-security Release
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release
...Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/main Packages
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/restricted Packages
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/main Sources
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/restricted Sources
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/universe Packages
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/multiverse Packages
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/universe Sources
  404 Not Found
Err [http://archive.linutop.eu](http://archive.linutop.eu) edgy-backports/multiverse Sources
  404 Not Found
...


It looks like the repository is no longer there. Does anyone have any idea how I can upgrade to the current release without installing it from scratch? Thanks a lot.

---

### Post by Pumalite on 2008-07-02
You have to go step by step: 6.10>7.04>7.10>8.04
Try a different Server because I'm not sure the support for 6.10 has ended. If you cannot do it the official way, you might want to try this:

sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by Thirtysixway on 2008-07-02
They look available through firefox... odd.  Can you access the web from your box?  Also try dist-upgrade (but you would need to make sure all updates are installed first)

Maybe this has to do with the fact that 6.10 isn't supported anymore.

---

### Post by esquif on 2008-07-02
Unfortunately still doesn't work. :\ The errors are the same. Also I forgot to mention the last couple of lines of errors:

> W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I get updates from another server? I'm very new at linux so I'd appreciate any help. Thanks a bunch!

---

### Post by Pumalite on 2008-07-02
The error message means you have another instance of apt-get open; maybe Synaptic
As for the Server:
System>Administration>Software Sources>Change the Server to Main. But the prior poster might be righ and there is no support for 6.10
In that case, try the command lines I gave you. Make sure you remove all third parties form your sources.list and that your OS is fully updated before you attemp it.

---

