---
title: "&quot;No Video Adapter Found&quot;"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by jake1337 on 2008-06-03
Hey, i have a working CD of 7.1 which i was going to use to dual boot with vista, and then update it when on... to the latest 8.3 or whatever.

So i put the disk in, ask the bio's to boot from disk. It loads up, asks me the main options, i select install or run ubuntu now. It shows a loading bar, after about 15-20 seconds the loading bar breaks up, and the graphics split.

I then, opens a box saying that "ubuntu could not find any video adapters" and that i should keep it at low settings, i click yes, continue. 

I then stops installing and goes on what looks like a command line.  With 4 lines of "loaded this... loaded that"

Any ideas? I am going to double check and dl the newer version of ubuntu over night to see if it makes a difference, but i've got a feeling its not!

---PC-SPECS---
Nvidia 8800GT 1024mb 
2gb ram // Pentium D 3.0ghz Dcore
Asus motherboard // PCI-EXPRESS 2.0


*NOTE* I've used this same disk on another system to install linux and it worked FINE.

---

### Post by PmDematagoda on 2008-06-03
Try installing the Nvidia driver manually by:-
1) Remove the nvidia-glx-new package with:-
```
sudo apt-get install nvidia-glx-new
```

2) Download the Nvidia driver installer:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run
```

3) Install the required prerequisites with:-
```
sudo apt-get install build-essential
```

4) Stop the X-Server with:-
```
sudo /etc/init.d/gdm stop
```
if the X-Server isn't completely killed, then execute:-
```
sudo killall Xorg
```

5) Execute the installer with:-
```
sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run
```

6) After install, restart the X-Server with:-
```
sudo /etc/init.d/gdm start
```

See if that fixes the problem.

---

### Post by jake1337 on 2008-06-03
How can i type it in if Ubuntu isn't even installed on my pc?

---

### Post by PmDematagoda on 2008-06-03
> **jake1337 said:**
> How can i type it in if Ubuntu isn't even installed on my pc?

Oops, I didn't see that. Sorry.

You can try and install Ubuntu using the Alternate CD which can be found [here]("http://releases.ubuntu.com/8.04/").

---

