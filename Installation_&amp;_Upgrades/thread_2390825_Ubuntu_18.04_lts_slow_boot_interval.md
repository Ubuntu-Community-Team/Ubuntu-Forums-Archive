---
title: "Ubuntu 18.04 lts slow boot interval"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by arnav16 on 2018-05-03
I had got some errors earlier i have solved it now but i got another problem then after. The OS boots very slow; it takes more than 2 minutes to show the login screen. The black screen appears after the ubuntu loading screen upto 2 to 3 minutes and only the login screen appears. Please, help on this topic...It's not the solution to wait every 4-5 minutes to use the Ubuntu. Please help me...:(:(:(

---

### Post by Claus7 on 2018-05-03
Hello,

in order to shed more light to your issue, try these commands:
systemd-analyze time
systemd-analyze blame
systemd-analyze critical-chain

from there you will have a clearer picture of what is wrong so as to take the necessary steps needed.

Regards!

---

