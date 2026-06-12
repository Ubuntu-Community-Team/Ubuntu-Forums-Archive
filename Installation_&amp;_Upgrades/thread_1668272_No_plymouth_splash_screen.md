---
title: "No plymouth splash screen?"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by drazgo on 2011-01-16
Hi everyone, 

I recently bought a new laptop with an ATI Mobility Radeon 5470HD graphics card in it and installed ubuntu. Everything works just fine, but at the startup, no plymouth splash screen comes up, just a black screen with a white dash...

Does anybody know how to fix this so i can get some eyecandy? :)

Thanks in advance!

---

### Post by dino99 on 2011-01-16
check that "splash" is loaded by the boot line

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth

---

### Post by drazgo on 2011-01-16
> **dino99 said:**
> check that "splash" is loaded by the boot line

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth

Just tried, still not working :? The plymouth splash on shutdown works though... Any other ideas?

---

### Post by drazgo on 2011-01-17
Somebody at askubuntu.com provided me the answer! For people who have the same issue, just follow this tutorial: 

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

---

### Post by garvinrick4 on 2011-01-17
#Need to get video drivers working before mountall hits:
Fix below from launchpad some time ago: Works:
```
sudo -i 
```
  	 	 	 	 	```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 


 
```

---

