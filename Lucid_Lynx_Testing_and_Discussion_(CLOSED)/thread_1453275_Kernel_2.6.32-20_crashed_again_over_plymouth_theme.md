---
title: "Kernel 2.6.32-20 crashed again over plymouth theme"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-13
i have just reinstall 2.6.32-20 becuase fglrx and compiz is working there and everything was fine the only thing i did that might had caused the problem is to use this command:
sudo update-alternatives --config default.plymouth and choose number 4 and after restart he want go up again i see the purple screen and then it turns black luckily 2.6.33 is not effected by this things.

```
There are 5 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       &#1502;&#1510;&#1489; &#1488;&#1493;&#1496;&#1493;&#1502;&#1496;&#1497;
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        &#1502;&#1510;&#1489; &#1497;&#1491;&#1504;&#1497;
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        &#1502;&#1510;&#1489; &#1497;&#1491;&#1504;&#1497;
* 3            /lib/plymouth/themes/solar/solar.plymouth               10        &#1502;&#1510;&#1489; &#1497;&#1491;&#1504;&#1497;
  4            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        &#1502;&#1510;&#1489; &#1497;&#1491;&#1504;&#1497;
  5            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       &#1502;&#1510;&#1489; &#1497;&#1491;&#1504;&#1497;

&#1500;&#1495;&#1509; &#1488;&#1504;&#1496;&#1512; &#1499;&#1491;&#1497; &#1500;&#1513;&#1502;&#1493;&#1512; &#1488;&#1514; &#1492;&#1489;&#1495;&#1497;&#1512;&#1492; &#1492;&#1504;&#1493;&#1499;&#1495;&#1497;&#1514;
[*], &#1488;&#1493; &#1492;&#1511;&#1513; &#1488;&#1514; &#1492;&#1502;&#1505;&#1508;&#1512; &#1492;&#1502;&#1497;&#1497;&#1510;&#1490; &#1488;&#1514; &#1492;&#1489;&#1495;&#1497;&#1512;&#1492; &#1492;&#1502;&#1489;&#1493;&#1511;&#1513;&#1514;: 

```i'll try to set 0 from 2.6.33 now and see if it would fix the problem.

EDIT:
i set it to 0 and now it's working again for now any way.

---

