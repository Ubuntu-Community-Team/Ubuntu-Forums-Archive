---
title: "Install Xerox C9065 Printer"
date: 2023-01-20
forum: Installation &amp; Upgrades
---

### Post by lee121212 on 2023-01-20
Hello Everyone

I am using Ubunutu Server 22.10, CUPS and SAMBA

[B]Question
[/B]I have a Xerox Primelink C9065 when I go to the "Xerox Downloads" page there is no Linux driver

There is a driver in Xerox Primelink C9065 in CUPS however it does not allow advanced features like Stapling, Hole Punching and Folding

How can I enable the advanced functions, in Windows it is easy because there is a check box that says "Advanced Function"

---

### Post by ActionParsnip on 2023-01-20
[https://download.support.xerox.com/pub/docs/PLC9065_PLC9070/userdocs/any-os/en_GB/PrimeLink_C9065_C9070_sag_en-us.pdf](https://download.support.xerox.com/pub/docs/PLC9065_PLC9070/userdocs/any-os/en_GB/PrimeLink_C9065_C9070_sag_en-us.pdf)

Shows there may be a driver

---

### Post by ActionParsnip on 2023-01-20
[https://www.support.xerox.com/en-us/product/primelink-c9065-c9070/downloads?platform=linux&product=&category=&language=en&attributeId=](https://www.support.xerox.com/en-us/product/primelink-c9065-c9070/downloads?platform=linux&product=&category=&language=en&attributeId=)

Grab the 64bit deb

---

### Post by ActionParsnip on 2023-01-20
[https://download.support.xerox.com/pub/drivers/CQ8580/drivers/linux/pt_BR/XeroxOfficev5Pkg-Linuxx86_64-5.20.661.4684.deb](https://download.support.xerox.com/pub/drivers/CQ8580/drivers/linux/pt_BR/XeroxOfficev5Pkg-Linuxx86_64-5.20.661.4684.deb)

Nice when a direct download is available :)

---

### Post by lee121212 on 2023-01-20
I must be blind, thanks for that

Curious to know that if I install driver this on the Ubuntu Server and share with SAMBA the Windows 10 Clients will be able to connect.

However they will need the Xerox Global Printer Driver correct for Windows

---

### Post by ActionParsnip on 2023-01-20
Don't see why not. CUPS can also share the printer for you too

---

### Post by lee121212 on 2023-01-20
I am using CUPS at the moment which works for basic functions but as soon as I want advanced functionality such as Stapling, Hole Punching and Folding the CUPS driver does not work.

However now I have the driver hopefully this will unlock advanced features

---

### Post by ActionParsnip on 2023-01-20
Not sure about that. I despise printers but hopefully you'll get sorted.

---

### Post by lee121212 on 2023-01-24
I have tried to install the printer using the Debian file using the following commands 

[COLOR=#333333][FONT=Calibri]sudo dpkg --force-all -i <deb package>

[/FONT][/COLOR]However where do the files goto or extract too because it Unpacks but nothing else happens and I do not see the printer in the Printer section

---

