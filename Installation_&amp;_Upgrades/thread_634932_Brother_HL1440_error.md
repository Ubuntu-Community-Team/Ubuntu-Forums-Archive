---
title: "Brother HL1440 error"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by chrisyuan01 on 2007-12-08
hey everyone.  I recently followed some instructions on this forum to install my Brother printer driver, and it worked... for a while.  The last time I restarted, the printer won't show up, and when I open up Synaptic Package Manager, it will not open.  The message that comes up is: hl1440 must be re-installed, but I cannot find the archive.  It does the same thing when I open up terminal and type: sudo apt-get install ABC, ABC being anything.  Please help!!:(

---

### Post by chrisyuan01 on 2007-12-08
can anyone please help?

---

### Post by chrisyuan01 on 2007-12-08
Nobody?

---

### Post by chrisyuan01 on 2007-12-09
Wow, everyone else gets their questions answered, but not me?:(

---

### Post by froy02 on 2007-12-10
download the lpr and cups drivers for your printer from this site: [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

there should be 2 drivers 1 lpr and 1 cups driver.

use the gdebi package installer by right clicking on the hl-1440 lpr driver and install it FIRST.  then install the cups wrapper next.

open firefox and type "http://localhost:631" and configure your printer.

make sure you download the deb files for debian.

---

### Post by chrisyuan01 on 2007-12-10
yes, that is what I do, except when I install my LPR driver, then when I try and instal CUPS, it says that it needs to re-install LPR except it is corrupted, and to try again.  Also, it says it has a Cache Error

---

