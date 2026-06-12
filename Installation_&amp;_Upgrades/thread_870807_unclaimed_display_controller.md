---
title: "unclaimed display controller"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by CTown on 2008-07-26
Hi,

I am very new at Ubuntu and have installed Ubuntu Hardy on an Asus Nova P20 

[http://www.asus.com.au/products.aspx?l1=20&l2=115&l3=0&l4=0&model=2199&modelmenu=1](http://www.asus.com.au/products.aspx?l1=20&l2=115&l3=0&l4=0&model=2199&modelmenu=1)


The problem I am having is when I do a lshw -C display I get:
 ```

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82946GZ/GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
```

What does UNCLAIMED mean? My wireless network adapter said the same thing before the driver was installed. Does this mean the driver for the display is not installed correctly or at all?

All my google searches say that this display chipset should be automatically installed?

Could someone please point me in the right direction with this?

---

### Post by Pumalite on 2008-07-26
It means the kernel did not recognize it and no module is mounted. Try to open uo backports and do:
sudo aptitude update
sudo aptitude dist-upgrade
Reboot
If that doen't do it; try:
sudo apt-get install linux-backports-modules-generic

---

### Post by CTown on 2008-07-27
Thanks for your reply. I followed your instructions but it is still reporting as unclaimed.

Any other ideas?

---

### Post by Pumalite on 2008-07-27
Try a different kernel.(version)

---

### Post by javacookies on 2011-09-13
my display also indicate UNCLAIMED....i still can't understand what it means...i've searched in the net already...some says the driver isn;t installed some says other things
BTW, in my onitor settings, I can't change the refresh rate.It says 0hz though I don't believe it but i'm still bothered because evertime I open a game or VLC,the display flicks . Thnaks for any help I can get here :)

---

