---
title: "Why &quot;permission denied&quot; for sudo operation?"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by pcpain on 2010-09-30
A few days ago I tried to install a driver for a Brother printer (HL-5040) in terminal mode by issuing "sudo dpkg -i --force-all hl5040lpr-1.1.2-1.i386.deb" on my Ubuntu 9.10 PC.

During the process several error messages were displayed. All of them say "permission denied" to access a directory /etc/init.d/lpd. Consequently, the installation failed and Synaptic package manager does not work any more and becomes broken.

Questions: Why did I get "permission denied" as a su? How can I get around the problem so I can re-install the driver?

---

### Post by Goolie on 2010-09-30
> **pcpain said:**
> A few days ago I tried to install a driver for a Brother printer (HL-5040) in terminal mode by issuing "sudo dpkg -i --force-all hl5040lpr-1.1.2-1.i386.deb" on my Ubuntu 9.10 PC.

During the process several error messages were displayed. All of them say "permission denied" to access a directory /etc/init.d/lpd. Consequently, the installation failed and Synaptic package manager does not work any more and becomes broken.

Questions: Why did I get "permission denied" as a su? How can I get around the problem so I can re-install the driver?


Try finding out if that file is currently in use

---

### Post by kleskjr on 2010-09-30
I have similar issue when try to change my battery parameters.don't know why
but after loging with **sudo -s** it works.

---

### Post by pcpain on 2010-10-01
Thanks to Goolie and Kleskjr. 
I am quite sure that the directory "etc/init.d/lpd" was not in use. The suggestion to  run "sudo -s" did not solve my problem. 

Incidentally I found that the printer Brother 5040 was working although the installation of the driver failed. I am sure that I will find it working only partially later. 

Now the problem is the broken Synaptic Package Manager. Somewhere it says "Software index is broken,"  and keeps saying "The package hl5040lpr needs to be reinstalled, but I can't find an archive for it" each time I tries to run "sudo apt-get -f install" or" sudo apt-get purge synaptic" and other similar commands ."

I need help to straighten Synaptic.

---

