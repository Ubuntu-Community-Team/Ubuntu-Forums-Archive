---
title: "Xserver will not start"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2010-05-11
Hi after update I restarted Now I can not login gnome. I tried this  sud o   d p k g - r e c o n f i g u r e   x s e r v e r - x o r g did not work gsm will not start then I did this   sudo apt-get remove -- purge xserver-xorg then
 sudo apt-get install xserver-xorg then   sudo dpkg-reconfigure xserver-xorg still not working

---

### Post by nothingspecial on 2010-05-11
Does ```
sudo service gdm start
```

give any errors?

---

### Post by stuart221 on 2010-05-11
Massage gdm start/running process 4512

---

### Post by nothingspecial on 2010-05-11
Then if you press Ctrl-Alt_F7

---

### Post by stuart221 on 2010-05-11
No error message just loads some programs

---

### Post by nothingspecial on 2010-05-11
What programs?

Help me out.

---

### Post by stuart221 on 2010-05-11
Sorry programs boinc core client clamav daemon clams

---

### Post by nothingspecial on 2010-05-11
Do you know your graphics card?

```

lspci -v
```

Just post the grahic card bit unless you don`t know what it is :)

---

### Post by stuart221 on 2010-05-12
Nvidia geforce 7300

---

