---
title: "PPPoE Settings !"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by zerosan on 2005-05-09
Please help me to set up my internet connection using Point to Point Protocol over Ethernet with Ubuntu 5.04.
I've set up my Internet connection with Slackware using adsl-setup script, but under Ubuntu there no adsl-setup or this is why I'm with non administrative account.
Sorry I'm lame.Please help me. Thank you! :)

---

### Post by az on 2005-05-09
Unless you do not have X installed, use the graphical networking tool.  And no, there is no root account.  The user has scalable administrator priviledges.  You need to entoer your password to gain priviledges.

---

### Post by zerosan on 2005-05-09
Can I use adsl-setup script from rp-pppoe Roaring Pinguin to set up my Internet Connection

---

### Post by cyberdude on 2005-05-09
in terminal type sudo pppoeconf
enter your ubuntu account login password  when prompted
pppoeconf will start, enter info as prompted and your net setup should be ok.

in my case i picked yes at every yes/no prompt and everything works fine

---

