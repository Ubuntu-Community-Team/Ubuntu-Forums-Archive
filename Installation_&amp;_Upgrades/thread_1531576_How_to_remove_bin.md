---
title: "How to remove bin ?"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by birkopf on 2010-07-15
I installed program from sources (billreminder) but it installed with an error. I want to uninstall it. I don't have catalog with make file so I cannot do 'make uninstall'

- How to fully uninstall program build from sources ? Nothing about uninstalling in manual :(

---

### Post by TheStroj on 2010-07-15
Program will probably be installed in /usr/local so search the files there and manualy delete them :)

---

### Post by Paddy Landau on 2010-07-15
Are you talking about [gnulinuxbrasil's billreminder]("http://billreminder.gnulinuxbrasil.org/")? Was there a specific reason for installing from source and not using the .deb file? (If you use the .deb file in future, you'll be able to uninstall quickly and easily using Synaptic. Wherever possible, always use the .deb file so that Synaptic can track dependencies and help you to install and uninstall.)

To uninstall manually, you'll need to know where all the files are placed. Uninstalling is simply a matter of deleting those files and, where applicable, directories. If you did not use root (i.e. sudo), then presumably you installed it all somewhere in your home directory.

---

### Post by birkopf on 2010-07-15
> **Paddy Landau said:**
>  Was there a specific reason for installing from source and not using the .deb file? 


I was using source because deb was only for i386 architecture. I have 64 bit processor. I found it in usr/local/bin. 

Just wanted to be sure that "jut removing" will not break any dependencies. 
Thanks for help guys!

:D

---

### Post by mcduck on 2010-07-15
In the future,  recommend always using Checkinstall when you need to install something from source. Instead of installing the application directly it turns it into a .deb package and installs that. So your application gets recognized by the package management and you can simply uninstall it like any other package.

To use checkinstall you simply replace the "make install command with it, so instead of doing the usual "./configure && make && sudo make install" you'd run "./configure && make && sudo checkinstall". Of course you need to install the checkinstall aackage from repositories first. :)

---

### Post by birkopf on 2010-07-15
> **mcduck said:**
> In the future,  recommend always using Checkinstall when you need to install something from source.

Excellent!
Thank you for this tip !

;)

---

### Post by stanleykaaya on 2011-07-07
just access the directory where you had the .bin file installed and, right click the uninstall icon,click open and all will be done.

---

### Post by philinux on 2011-07-07
Thread is marked as solved and old. Closed.

---

