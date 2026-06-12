---
title: "GeForce 6150 driver on ubuntu 9.10 HELP PLZ !"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by ihy2000 on 2010-01-12
Hi,

I've just installed ubuntu 9.10 on my desktop, my graphic card seems to run unstable some times and i cant run compiz.

My card is GeForce 6150, How can i install a driver for it so that i can fix the problem and run compiz ?

Thanks,

---

### Post by cta16 on 2010-01-12
Try [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
After installation, it should be pretty self explanatory after you run it. Make sure you are connected to the internet.

---

### Post by ihy2000 on 2010-01-12
Thanks, It worked :)

---

### Post by presence1960 on 2010-01-12
> **cta16 said:**
> Try [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
After installation, it should be pretty self explanatory after you run it. Make sure you are connected to the internet.

For future reference EnvyNG is now in the repositories. You can install EnvyNG by running in terminal:

```
sudo apt-get install envyng-core
sudo apt-get envyng-qt
sudo apt-get install envyng-gtk
```

Once installed you can open EnvyNG by running in terminal ```
envyng -t
```

---

