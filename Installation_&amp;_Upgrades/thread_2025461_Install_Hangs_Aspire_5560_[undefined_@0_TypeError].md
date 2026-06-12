---
title: "Install Hangs Aspire 5560 [undefined @0: TypeError:]"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by keyshawn on 2012-07-14
Edit: 
Hours later, a message stating 'the installation has finished' appeared. So, solved for now ! 
here's my updated syslog [http://paste.ubuntu.com/1092108/](http://paste.ubuntu.com/1092108/)

Hi, 

I'm installing ubuntu 12.04  on this laptop
(Acer Aspire 5560-7414) for the first time. 

(I booted the live CD, 'chose try' used the desktop for a bit (firefox) and then proceeded with the install by launching 'install 12.04 LTS' in the unity bar) and the install screen has been at the same note for the past 60 minutes, with its last message: 
```
** Message: console message: undefined @0: TypeError: 'undefined' is not a function
``` and the little rotating hourglass like mouse cursor still appears when the install window is focused. 


Is my install finished ? I'm not sure if this error is even serious, but I would have expected some final confirmation messages confirming a successful install or to reboot [can't remember what happened the last time I installed ubuntu].  

I read through the syslog and found a few graphics related errors, including 
Jul 14 15:34:52 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
The card is reportedly supported in linux: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

My video card is a AMD Radeon 6520G although lspci reports it as: 
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647

Here is my X0rg log: [http://paste.ubuntu.com/1091871/](http://paste.ubuntu.com/1091871/)
Here is my lspci: [http://paste.ubuntu.com/1091860/](http://paste.ubuntu.com/1091860/)

Here is my syslog: [http://paste.ubuntu.com/1091855/](http://paste.ubuntu.com/1091855/)


Oh well, after dozen+ installs of ubuntu, this is my first one with any problems. 

thanks, 
will

---

