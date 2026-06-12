---
title: "How to remove real VNC enterprise in Ubunto 9.1"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by raywcleung on 2010-01-05
I installed Real VNC enterprise software in Ubunto 9.1 by mistake, but there is no control panel like Windows to uninstall it, please help to advise how to remove it and I want to install real vnc free version. Thanks.:KS

---

### Post by jonest1 on 2010-01-05
Can you please explain in as much detail as possible the installation steps you used to install the software?  Did you download it from somewhere?  What was the filename on the package?  Or did you install it through the software center?

---

### Post by raywcleung on 2010-01-06
I think I double clicked the .deb package and it install automatically in Ubuntu 9.1 but my another Netbook remix version Ubunto has a software installation prompt and console for me to choose, I don't have knowledge on sudo command, it is download from realvnc.com and you choose enterprise linux version, it will install automatically on double click the firefox download from the firefox download tab.

[http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi)


**VNC Enterprise Edition for Linux (x86)**
Installable packages including viewer, XFree86 module, stand-alone server and x0vncserver
Version 4.5  (requires [a license key]("http://www.realvnc.com/cgi-bin/purchase.cgi?product=enterprise4%2FXvnc&productTypes=LICENSE"))

---

### Post by jonest1 on 2010-01-06
I don't have my Ubuntu installation in front of me, but I can walk you through.  If you have questions, I may be able to assist further in a few hours.

Go to System -> Administration -> Synaptic Package manager and open it.  

There should be a search button at the top, click on it.

Type vnc into the search window and ensure the drop-down Look-in list is set to Name.  Click OK.  It should find a few items in the search results window.  Right-click on the vnc-e or whatever aplication from the search results and choose remove or uninstall.  

Then click the apply button from the top toolbar and it should uninstall.

There are multiple methods for installing and uninstalling software, but synaptic may be the best for this situation.

Let me know if this worked out for you.

---

