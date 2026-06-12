---
title: "Unable to add a local printer driver when using a Remote Printer"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by John_Lawton on 2014-07-31
I have a small office with a Linux server which has a USB printer installed and a new workstation with a fresh install of Kubuntu 14.04. 
The workstation detects the raw printer on my Linux server, calling it a 'Remote Printer'. This server printer is configured using Samba as a Windows printer with a RAW driver.  My Windows clients work fine using their local printer driver for this printer (Dell  1320c). 

I have installed a Linux printer driver on my workstation which works if I plug the printer in as a local USB printer.  The problem is that the workstation Settings, Printer GUI tool, [COLOR=#ff0000]Configure[/COLOR] button won't allow a printer driver to be added when using the Remote Printer on the server -  the [COLOR=#ff0000]Driver[/COLOR] selection is greyed out. 

(BTW, I've tried the local CUPS server which doesn't help either, sending me off to the Linux server CUPS server, aargh!).

This hadn't been a problem on my previous workstation using an earlier version of Kubuntu. The SSD on that machine unfortunately became u/s (don't ask) so I can't access any configuration files from that now.

How to fix please, this is driving me nuts!!

---

### Post by John_Lawton on 2014-08-04
Anyone? I'm currently unable to print and would really appreciate some help with this problem.

---

### Post by dangle42 on 2014-08-04
My first thought is that you will have to install it off a script. I had to use a .run file to install my hp drivers. I did a quick Google search. Did you try this? 
[http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu](http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu)

---

### Post by John_Lawton on 2014-08-05
Yes, I have installed a driver, and it works if I plug the printer into the USB port. However I cannot select this driver when using the same printer connected to the Linux server, 'chef'. See the attached where the Driver selection box is greyed out.

[IMG]http://lawton.me.uk/images/snapshot6.png[/IMG]

---

### Post by mikejjp on 2014-11-29
I have a greyed-out printer "USB #2 with status readback for Canon IJ ..."

---

