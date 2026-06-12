---
title: "Nautilus has lost its icons?"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by jacrider on 2011-11-15
I am just completing an installation of 11.10 AMD64.

I have been using Nautilus (Home Folder) from the launcher and have always had the colored, animated icons.  

All of a sudden after a reboot, all the icons are generic white boxes.  

Not fatal, but I can't see which folders are shared, synced with UbuntuOne, etc.

Any ideas?

---

### Post by dino99 on 2011-11-15
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a (can take a while, be patient)
gnome-panel --replace

---

### Post by jacrider on 2011-11-15
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a (can take a while, be patient)
gnome-panel --replace

Thanks for the suggestion, but it didn't work.  I am using Unity, so gnome-panel isn't running.

Any other ideas?  Can I re-install nautilus?

---

### Post by raja.genupula on 2011-11-15
> **jacrider said:**
> Thanks for the suggestion, but it didn't work.  I am using Unity, so gnome-panel isn't running.

Any other ideas?  Can I re-install nautilus?

i am not sure that reinstalling nautilus will the solve issue .But giving a try is not at all a bad thing

```
sudo apt-get install --reinstall nautilus
```

---

### Post by jacrider on 2011-11-17
That's right ... re-installation didn't work.

Anyone have any other ideas?

Thanks.

---

### Post by raja.genupula on 2011-11-17
Final thing i can give is 
```
sudo apt-get install --resinstall ubuntu-desktop
``` 

all the best .

---

### Post by vinnief on 2011-11-17
same problem here, and none of the above restored the icons. :confused:

---

### Post by Frogs Hair on 2011-11-17
See the section on Nautilus crashing .[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

