---
title: "aptdaemon error while installing Oracle 10g"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by aniljaiswal on 2011-03-24
> 
An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.I recently tried to install Oracle xpress edition 10g by downloading the ".deb" file of around 200 mb. When the installation was about to complete, the "Ubuntu Software Center" gave an error like shown in the picture.

Help me as soon as possible.

Thanks & regards.

---

### Post by mvchad on 2011-04-05
Hi,

I had this problem on 10.10 and it turned out that I hadn't configured enough swap for Oracle XE's needs. 

Found this out by manually running dpkg -i *.deb and the resultant output highlighted this fact.

Not sure of the exact requirements, but I just ensured there was at least a gig of swap and it worked a treat.

Hope this helps.

---

