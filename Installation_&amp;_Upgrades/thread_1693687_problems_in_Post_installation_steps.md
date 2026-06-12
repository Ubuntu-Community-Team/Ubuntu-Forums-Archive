---
title: "problems in Post installation steps"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Rakesh055 on 2011-02-23
Please can any one help me in the following steps.


uecadmin@server1:~$sudo /etc/init.d/networking restartat this step i cannot connect to the system.

whether should i connect to internet here. please help how can i connect to internet.

---

### Post by Bucky Ball on 2011-02-23
Welcome. 

Firstly, plug in an ethernet cable and get online that way. You will be offered updates. Accept them. Then look in:

System>Administration>Additional Drivers

Is there a wireless driver there? You need to get your wireless card happening before you can get online wirelessly and to do that you need to get online with a cable generally.

Seeing as you are in a terminal, type or paste in:

```
sudo lshw -C network
```

You should be able to identify your wireless card there if the correct firmware is loaded. ;)

---

### Post by Rakesh055 on 2011-02-25
Thanks for the reply,

I will try out with the mentioned steps.

can i know how to get GUI version for the server edition

---

### Post by Bucky Ball on 2011-02-26
You load the server edition and then install a DE (desktop environment) if you want one; Gnome, Xfce would be quicker. The less apps you need to run your server the better for speed. ;)

---

### Post by Rakesh055 on 2011-02-28
In the first reply which you gave i found my wireless device but it is disabled. how to enable that one.

---

### Post by Bucky Ball on 2011-02-28
Plug in an ethernet cable, get updates, then System>Administration>Additional Drivers and enable the card. ;)

Hope that works.

---

### Post by Rakesh055 on 2011-02-28
thank you for the reply,

but my problem is i have to connect to the internet to get update. but the ethernet and wifi drivers are disabled. i could not connect to internet.

can you help me how to update other than from internet. i tried with intenet through LAN but it was saying O%downloading due to some problems. i dont know why.

---

