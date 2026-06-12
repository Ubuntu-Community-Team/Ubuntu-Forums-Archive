---
title: "Dell vostro 1310 display problem on ubuntu 12.04"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by RooSH23 on 2012-05-03
After upgrading to ubuntu 12.04 i keep experiencing display problems and crashes.
connecting an external screen make it even worse and fail to load at all.
upon each startup i get the following error message:

[IMG]https://lh5.googleusercontent.com/-isv44cN7xsI/T6JZGK2aHxI/AAAAAAAAAs4/I71LoZNOd3g/s512/Screenshot%2520from%25202012-05-03%252012%253A54%253A23.png[/IMG]

[IMG]https://lh4.googleusercontent.com/-fZ6KUb1zk6A/T6JZHwfaC_I/AAAAAAAAAtA/M4gbK5y04lg/s640/Screenshot%2520from%25202012-05-03%252012%253A54%253A43.png[/IMG]

---

### Post by kc1di on 2012-05-03
sorry your having problems. 

your Vistro has an Nvidia video card.  and there is a problem with the propitiatory Driver at this point.  If you have installed Nvidia Current or other Nvidia Driver , you should remove it for now. and use the opensource driver.  That will cure some of the crashes. 
It's been reported and is being worked on. 


[http://www.nvnews.net/vbulletin/showthread.php?t=178460]("http://www.nvnews.net/vbulletin/showthread.php?t=178460")

---

### Post by RooSH23 on 2012-05-03
I don't have nvidia graphic card.
my graphic card is onboard:

```
sudo lshw -C video
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f80fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff

```

---

