---
title: "hoary hangs during installation"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by rpm on 2005-04-27
after asking to dl the complete language pack for italian 

I say NO 

the installer dislplays "configuring apt"

and

Testing network repository...

I think is trying to dl something from ubuntu repos sites but I'm at work on a WAN behind a firewall and you can only connect to the internet trough the proxy server.

What can I do?

Is better at the beginning of the install process to unplug the network cable, so that the LAN is not felt active at all ?

thx in advance

rpm

---

### Post by Sniffer on 2005-04-27
I have the same prob, but after waiting a bit the installer give the connection as failed and continue...

Tough

You still can disable your ethernet connections in your bios and then install hoary...and if needed active them before....


My 2 cents
Sniff.

---

### Post by rpm on 2005-04-28
thx

It works after some minutes 

rpm

---

### Post by jonny_boy27 on 2005-05-23
i also have this problem. but i have left it hanging for nearly 30mins with no change! could you maybe explain the fix u suggested by disabling ethernet controllers in BIOS in more detail?

also is there no way of setting teh proxy settings in the installer so that the APT config works?

---

### Post by Sniffer on 2005-05-24
[QUOTE=jonny_boy27]i also have this problem. but i have left it hanging for nearly 30mins with no change! could you maybe explain the fix u suggested by disabling ethernet controllers in BIOS in more detail?

also is there no way of setting teh proxy settings in the installer so that the APT config works?[/QUOTE]


**1st** check if your Ubuntu CD is ok, then by pressing del or F10 when booting (it depends from machine to machine wich button to press, but it says on the boot screen, something like F10 to setup or bios) you have access to your bios, then in hardware options just disable your onboard/PCI lan controllers.


In relation to the proxy settings , never tried, never needed..so i can't be much of help in that situation.

Sniff.

---

