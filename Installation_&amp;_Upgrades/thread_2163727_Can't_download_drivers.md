---
title: "Can't download drivers?"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by Nate Hofmann on 2013-07-19
When ever I try to download driver using Additonal Drivers,  the installation fails an additional wndow opens saying "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log". Does anyone know what this means and how to fix it? Thanks!

---

### Post by Claus7 on 2013-07-19
Hello,

you might have to install this driver by yourself. Providing more information on what you want to install will provide answers suitable to your needs. Also, have you seen the file in question in order to realise what the problem might be?

Regards!

---

### Post by Cheesehead on 2013-07-19
> **Nate Hofmann said:**
> When ever I try to download driver using Additonal Drivers,  the installation fails an additional wndow opens saying "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log". Does anyone know what this means and how to fix it? Thanks!

The system could not install the driver.
There is a detailed log of the failure at /var/log/jockey.log
Open that file, and copy-and-paste the contents here.
Then we can tell you more.

---

### Post by Nate Hofmann on 2013-08-01
I have no clue how to open the" /var/log/jockey.log" file. Please help?

---

### Post by dino99 on 2013-08-01
open a terminal (from the menu) and glance at the details of :

> cat /var/log/jockey.log

---

