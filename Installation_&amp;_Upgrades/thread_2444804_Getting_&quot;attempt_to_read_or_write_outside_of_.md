---
title: "Getting &quot;attempt to read or write outside of disk 'hd0'&quot; after install."
date: 2020-06-04
forum: Installation &amp; Upgrades
---

### Post by n9vmo on 2020-06-04
After installing 20.04 (and any other previous version both desktop and server) I keep getting the error message [U]attempt to read or write outside of disk "hd0" Entering rescue mode...
[/U]

I have done a lot of reading on this and have tried all of the given  solutions and none of them have worked.  I have even loaded the Ubuntu  LiveCd and run the Boot Rescue program and I still get the stated error.

  
The machine is a Dell R710 with a H700 Raid Controller with six 3TB  HDDs in a Raid 50 configuration and I'm using all but ~500MB.

  
I also know that this is an Ubuntu install issue as I can load  Windows 10 and have absolutely no errors. 

What am I missing???

---

### Post by n9vmo on 2020-06-05
Figured out my issue.

Machine was not set to UEFI but was in BIOS.

Changed setting and all is working now.

---

