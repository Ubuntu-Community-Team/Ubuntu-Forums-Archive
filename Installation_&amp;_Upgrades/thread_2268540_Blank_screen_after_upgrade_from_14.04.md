---
title: "Blank screen after upgrade from 14.04"
date: 2015-03-09
forum: Installation &amp; Upgrades
---

### Post by Matt_Barcus on 2015-03-09
Hello,

I am somewhat new to ubuntu. I had 14.04 installed on my machine and updated software through the software center. After rebooting the machine I was prompted that low graphics mode is required. Selecting the option did nothing. I then booted to terminal using alt + ctrl + F1 and followed instructions to install GDM as my graphics manager (instructions here: [http://simpledeveloper.com/system-running-in-low-graphics-mode/](http://simpledeveloper.com/system-running-in-low-graphics-mode/)). That seemed like a solutions for a few people, but now when I reboot, instead of seeing the low graphics prompt, all I get is a blank screen. I am not sure what to do. Alt + ctrl + f1 no longer appears to work. Please help. Thanks. I should mention that i also have windows 8.1 installed on the computer and select OS at start up. Specs of computer: sapphire r9 280 graphics card, i7 5820, asrock x99 extreme4 mobo.

---

### Post by Matt_Barcus on 2015-03-09
I seemed to have fixed this problem. The fglrx driver was previously installed and was causing issues after the update. I was able to get back to the terminal and change graphics manager back to original. From there, it began to work to boot in low graphics mode. The catalyst center had problems opening so I just uninstalled fglrx and rebooted. Everything then worked fine.

---

