---
title: "Install Lamp server"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by leeba on 2007-02-08
I did an install for Ubuntu 6.10 on a Intel x86, dual processor, PII 450 with 512 MB RAM and two 40 GB SCSI hard drives. When going through the install cd, I  selected the first option "install to the hard disk" ...but..  I need to install a LAMP server. Did I mess up by doing the install to the hard disk? Is the install LAMP server another option I can now go back and do from the install cd i created or should i have done that instead of the Install to the Hard Disk? Thanks in advance... ~Lee

---

### Post by divague on 2007-02-09
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc](https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc)

---

### Post by az on 2007-02-09
What cd did you use?

The LAMP stack is just a bunch of packages.  You do not need to reinstall anything to install those packages.  Just run

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by bandie on 2007-02-09
Once the server software has been installed you should get an option to install a DNS and / or LAMP you must select the option using the spacebar, don't just press enter assuming LAMP is already selected.

---

### Post by leeba on 2007-02-09
I used the [http://www.ubuntu.com/products/GetUb...irect=download](http://www.ubuntu.com/products/GetUb...irect=download) 

i ran this in the terminal and it said couldnt find package apache2.. when i did the install i did not choose the LAMP server ..just out of now knowing better at the time.

---

### Post by leeba on 2007-02-09
bandie.. i already did what you said not to do.. any solutions at this point?

---

### Post by az on 2007-02-09
Once you boot into your Ubuntu system, you need to be connected to the internet to install stuff from the repositories.

---

