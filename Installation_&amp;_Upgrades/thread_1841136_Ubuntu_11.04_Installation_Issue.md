---
title: "Ubuntu 11.04 Installation Issue"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by LMNUCOHEN on 2011-09-08
When I run Ubuntu 11.04 from the Desktop CD, the appropriate graphical user interface appears. However if I install Ubuntu 11.04 as a guest OS in a virtual machine, no graphical user interface appears... only a command prompt, text base interface.

My system is a an HP Envy 17 3D and my host OS is Windows 7 Professional. The virtual machine was created by VMware Workstation 7.1.4

Why is there no graphical user interface associated with the virtual machine guest OS?

---

### Post by mörgæs on 2011-09-09
Is this also the case for a Xubuntu installation?

---

### Post by fdrake on 2011-09-09
it depends on how much RAM/Video-card performance you have dedicated to the virtual machine in vmware,


> 
40 GB for hard disk and 1 GB for RAM. Display is Autodetect and accelerate for 3D graphics.

edit:
after your PM it looks like that is not the case. The other thing left is that it does not recognize the graphic card. Instead of "Auto-detected" can you specify the card model? if you don't know use the live cd and type in the terminal:
```

lshw -c Video  

```
annd look for the VGA .

---

