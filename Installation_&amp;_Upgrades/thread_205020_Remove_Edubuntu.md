---
title: "Remove Edubuntu"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-27
Hi,
Just for curiosity of my son, I installed edubuntu on ubuntu through synaptic manager. I completely remove edubuntu as I don't feel like. However, still while restart the system it shows the system of edubuntu. How can I get rid of edubuntu screen coming up while starting the computer?
thanks

---

### Post by aysiu on 2006-06-27
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by vasimakhtar on 2006-06-27
Thanks. But it gives the following message.

"There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
"

I want to remove the edubuntu screen coming up while starting the computer and get rid of it, instead i want ubuntu screen.

thanks

---

### Post by aysiu on 2006-06-27
Try this? ```
sudo aptitude update
sudo aptitude install usplash
sudo aptitude remove edubuntu-artwork-usplash
```

---

