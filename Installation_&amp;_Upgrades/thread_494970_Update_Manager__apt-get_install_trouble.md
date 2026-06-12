---
title: "Update Manager / apt-get install trouble"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Zeke46 on 2007-07-07
I am trying to install a Brother MFC440CN printer on Ubuntu 7.04.

When I go to [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) to try and download the correct driver, the window that opens stops and tells me that I must close all other Update Managers before I continue.  I have restarted twice and retried but it continues doing this.

Also, while following instructions on how to install the printer ([http://www.depannone.com/Printer.html](http://www.depannone.com/Printer.html)), i tried the command $ sudo apt-get install csh...
this is what the screen looks like:

$ sudo apt-get install csh
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

not sure what to do now... any suggestions?

-thanks.

---

### Post by Vajra Vrtti on 2007-07-07
I had no problem to download the drivers. Here they are:

---

### Post by Martje_001 on 2007-07-07
If you boot in recovery mode and then do 'sudo apt-get install csh', what does it do then?

---

