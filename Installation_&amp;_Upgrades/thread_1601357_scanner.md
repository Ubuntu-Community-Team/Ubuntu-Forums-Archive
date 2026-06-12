---
title: "scanner"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Anil babu on 2010-10-20
My Canon 646DU flat bed scanner worked in Ubuntu 10.04LTS .
Follow the steps in Ubuntu Help Center.
Click on ubuntu help center
click on printing faxing scanning
click on scanning
scroll down to 3.4 Manually installing 
click on link to install   :  libsane-extras
Press Alt+F2, type 
    gksudo gedit /etc/sane.d/dll.conf into the box and 
    click Run to open the SANE driver file for editing.
    Enable the right driver for your scanner by removing the “#” 
    from in front of the name of the driver. You may need to search the web to 
    find out which driver is the right one.
the key step is to suffix the model no: of your scanner after the name of scanner eg. canon646DU
save
and open the application  to scan in XSane image scanner
all the best

---

