---
title: "Installation of NVDIA drivers"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Aragon12345 on 2008-08-18
What i did was i entered alt ctrl f2 and then typed:
```
/etc/init.d/gdm stop
apt -get install build-essential
sh NVDIAdriver........
StartX this didn't work so i just typed X and it seemed to half start
```

The problem that i have now is that it will not boot. It just gets to Running Local scripts and flashs then comes back to Running local scripts and flashs again. This occurs a few times then it just looks like its frozen.

I can access the termninal using recovery mode which i tried to turn on X server from with no avail.

Any help would be apreciated!

---

### Post by cdtech on 2008-08-18
First, while your in the recovery mode type:
```
sudo dpkg-reconfigure xserver-xorg
```
This will reset your xserver (xorg.conf).

Then boot into normal GUI mode. After you log in go to "Synaptic Package Manager" and search for nvidia. Select "envyng-gtk and envyng-core". Then open a terminal and type:
```
sudo envyng-gtk
```
This will install your video drivers for you.

Hope this helps........

---

### Post by nikobor on 2008-08-19
I had the same problem once. What I did was to install enving.
sudo apt-get install envyng-gtk
Then simply, using root:
sudo envyng --t
in order to use the text mode. Then you choose option one- install nvidia driver in text mode. It all worked for me without need to reset the xserver. It's all done in recovery mode.

---

### Post by cdtech on 2008-08-19
> **nikobor said:**
> I had the same problem once. What I did was to install enving.
sudo apt-get install envyng-gtk
Then simply, using root:
sudo envyng --t
in order to use the text mode. Then you choose option one- install nvidia driver in text mode. It all worked for me without need to reset the xserver. It's all done in recovery mode.

Nice....:)

---

