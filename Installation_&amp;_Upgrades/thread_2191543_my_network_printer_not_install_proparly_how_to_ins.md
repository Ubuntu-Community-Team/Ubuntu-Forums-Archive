---
title: "my network printer not install proparly how to instoll"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by akshay_kam on 2013-12-03
dear sir
my network printer not install proparly how to instoll

---

### Post by efflandt on 2013-12-03
You need to provide more information, like manufacturer and model of printer.

Do you know the IP address of the printer? It is best for a network printer to have a static (manually assigned) IP address, in same network as your router, but outside of DHCP assigned (automatic IP) range. If the printer gets an automatic IP, that could change, and then not work.

Under **System Settings** > **Printing** > **+ Add**, it is easiest under **Network** to use "**AppSocket/HP JetDirect**". That is an HP thing, but I have not seen a print server in a network printer that did not support it. All you need to do is insert the IP address of the printer, leave default port 9100. Although, if Ubuntu cannot automatically find a driver for it, you may need to hunt for a suitable PPD file, or possibly select a printer that your printer emulates. For example many business printers can do "postscript" or "HP PCL". Before there was an Ubuntu driver for my Lexmark C543dn color laser, the C534 driver worked.

---

