---
title: "Can't go past 800x600 in Ubuntu or Xubuntu."
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Rock on 2008-06-08
Here are the specs of the computer I'm installing Ubuntu/Xubuntu on. 

Unknown Motherboard
Intel P4 2GHz
NVIDIA Geforce 7600GS 256MB
256MB PC133 RAM
40GB Western Digital Hard Drive
Acer AL1714

I've gotten this video card to use 1280x1024 on my AMD Athlon 64 3000+ and my 3 computers share the same keyboard, mouse, and monitor through the KVM switch (AMD Athlon 64 X2 5200+ 2.7GHz and NVIDIA Geforce 8600 GT, AMD Athlon 64 3000+ 2GHz and NVIDIA Geforce FX5500, and Intel P4 2GHz and NVIDIA Geforce 7600GS). The P4 has the better video card because the Athlon 64 3000+ is a web server with text only if anyone is wondering. I'm wondering why it won't go past 800x600 on this computer with 8.04 but it did on the Athlon 64 3000+ with 7.04.

---

### Post by Pumalite on 2008-06-08
Enable Hardware Drivers
System>Administration>Hardware Drivers

---

### Post by housam on 2008-06-08
try this : System > Preferences > Screen Resolution
If you didn't find your settings , try the following :
```
sudo nano /etc/usplash.conf
```
you will got something like that

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.


add the required resolution
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="Red"]1024[/COLOR]


then reboot and type :
```
sudo dpkg-reconfigure usplash
```



then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by Rock on 2008-06-08
> **Pumalite said:**
> Enable Hardware Drivers
System>Administration>Hardware Drivers

Tried that, does nothing.

[QUOTE=housam;5142936]try this : System > Preferences > Screen Resolution
If you didn't find your settings , try the following :
```
sudo nano /etc/usplash.conf
```
you will got something like that



add the required resolution


then reboot and type :
```
sudo dpkg-reconfigure usplash
```

I'll try that again after I re-install Ubuntu.

---

### Post by Rock on 2008-06-09
Ok, I ended up solving the problem by replacing the power supply. I had a 300W power supply in this computer and it wasn't enough power for the video card. Because of that, the computer watered down the video card limiting it to 800x600 and I gave it a 400W power supply and the problem was solved.

---

### Post by Nimefurahi on 2008-06-10
Now Rock, that's incredible! Who would have thought that the video card itself would throttle down to a less power-consumptive resolution. Good trouble shooting on your part. Bravo!

And Housam, thank you brother. The reason I tuned into this thread in the first place was because I had changed the  xres and yres parameters in my usplash.conf  and saw no results afterward. I has forgotten the refresh call: 
dpkg-reconfigure usplash 
You reminded me of that. Thanks.

Nimefurahi

---

