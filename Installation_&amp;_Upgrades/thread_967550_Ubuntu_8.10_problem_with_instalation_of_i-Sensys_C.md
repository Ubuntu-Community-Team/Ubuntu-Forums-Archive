---
title: "Ubuntu 8.10 problem with instalation of i-Sensys Canon LBP2900 Laser Printer"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by epitsst on 2008-11-02
Hi, 

I have a problem with instalation of Canon LBP 2900 laser printer. I have downloaded new driver from Canon site:

[http://software.canon-europe.com/products/0010419.asp](http://software.canon-europe.com/products/0010419.asp)
Canon CAPT Printer Driver for Linux (1.60). 

I have followed instructions in manual. In manual, for deb distributions, there is comand cupsys restart, but there is no cupsys, no such comand, only cups?

Did anyone instaled some Canon Laser printer? Can anyone help with this problem?

---

### Post by Bibabenjo on 2008-11-08
Hi epitsst,

I installed my canon lbp2900 a few weeks ago, using [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900") instruction!
Im using hardy and the printer works well.

If you get the problem solved, please tell me if you can print with duplex (both sides of the paper)! Unfortunately I couldnt get it working.

Greetz
BiBa

---

### Post by epitsst on 2008-11-11
> **Bibabenjo said:**
> Hi epitsst,

I installed my canon lbp2900 a few weeks ago, using [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900") instruction!
Im using hardy and the printer works well.

If you get the problem solved, please tell me if you can print with duplex (both sides of the paper)! Unfortunately I couldnt get it working.

Greetz
BiBa

I have also installed my printer with that instructions with some differences. There is no cupsys, only cups command in ubuntu 8.10, so there is no command cupsys restart, but cups restart works in the same way. Also, there are new Canon drivers with deb distribution, so I didn't use alien. But with all this, I am trying to print, and sometimes I can print test page without problems, but sometimes it takes forever to print, especially open office word document, and usually I get info that the print job is taking to long and I have to quit printing. But if I launch launch_captstatusui using terminal then I get window with message "Do you want to use this format of paper" or some thing like that, and when I press the OK button printing starts?? I still don't now how to solve this problem. If I find the way I'll let you now. Thanks for reply.

---

### Post by stephenr80 on 2009-04-29
> **epitsst said:**
> I have also installed my printer with that instructions with some differences. There is no cupsys, only cups command in ubuntu 8.10, so there is no command cupsys restart, but cups restart works in the same way. Also, there are new Canon drivers with deb distribution, so I didn't use alien. But with all this, I am trying to print, and sometimes I can print test page without problems, but sometimes it takes forever to print, especially open office word document, and usually I get info that the print job is taking to long and I have to quit printing. But if I launch launch_captstatusui using terminal then I get window with message "Do you want to use this format of paper" or some thing like that, and when I press the OK button printing starts?? I still don't now how to solve this problem. If I find the way I'll let you now. Thanks for reply.

for me the problem is that the system finds new printers when i turn the printer on and off instead of understanding that it is alwyas the same one, please help! I need somebody help! lalalala HEEEEEEEeEEELP

---

