---
title: "Problem during running Live version"
date: 2017-06-05
forum: Installation &amp; Upgrades
---

### Post by elteran on 2017-06-05
Ok, so I've got windows 10 installed and I would like to try if some things important to me are working with ubuntu. 

I've tried to check if LiveCD version is working, but I am having some troubles. ( see screens ). No matter if I tried to install Ubuntu, UbuntuGnome, burning it by Rufus or UNetBootIn, the problem stays as it was. 

The original version does not show the readable logs - I've turned them on by removing 'quite' from boot parameters. But at the moment I have no idea how to start. The screen shows completely frozen terminal. I cannot do anything - only hard reboot.

Please help :)

---

### Post by LastDino on 2017-06-05
```
Ok, **so I've got windows 10 installed** and I would like to try if some things important to me are working with ubuntu.
```

So, its WIn 10 per-installed machine? Bit more info will help

Have you turned off secure boot and fast startup?

---

### Post by elteran on 2017-06-05
No, I made my pc from scratch - thus I've installed Windows 10 by my own. I have all the secure boots, fast startups turn off.

Basically, I've got the following parts:


[LIST]
[*]MSI Z97 GAMING 3, Intel Z97, 4xDDR3, 1x M2, VGA, GbLAN, ATX (Z97 GAMING 3)
[*]MSI GeForce GTX 970 GAMING 4GB DDR5 PCI-E BOX
[*]Samsung SSD 850 EVO 250GB SATAIII, 540/520MBs, IOPS 97K MZ-75E250B/EU
[*]Seagate Barracuda, 3.5, 2TB, SATA/600, 7200RPM, 64MB cache ST2000DM001
[*]Intel CORE i7-4790K 4.0GHz BOX 8MB LGA1150 BX80646I74790K	
[/LIST]

---

### Post by LastDino on 2017-06-05
Have you tried "nomodeset"

USB boot - At the menu press tab or F6 on the first option to edit the boot  options and replaced the 'splash' option with 'nomodeset'.

---

### Post by elteran on 2017-06-05
Little update, I've run LinuxMint successfully. Now, I will try with this nomodeset option.

---

