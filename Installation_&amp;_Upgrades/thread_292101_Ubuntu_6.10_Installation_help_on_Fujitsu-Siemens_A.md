---
title: "Ubuntu 6.10 Installation help on Fujitsu-Siemens Amilo M 1437G"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by mobiuz on 2006-11-03
During one of the initial screens in the installation where the Ubuntu logo shows with a progress bar below the startup freezes and the computer hangs.

I've read about problems with Ubuntu hotplug together with Fujitsu's Intel soundchip (snd_hda_intel). There's a guide on how to get around this on Ubuntu 5.10 [here]("http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g/"), but things doesn't seem to work the same way with Ubuntu 6.10. The boot syntax is totally different and I don't know how to change them accordingly.

I'm totally new to Ubuntu but would really like to try it, so if someone could give me some directions and maybe help me with disabling these drivers, or whatever needs to be done, i would appreciate it.

---

### Post by Affenkopf on 2006-11-03
I've got exactly the same problem with a Fujitsu-Siemens Scaleo P, help would be appreciated.

---

### Post by hawk88 on 2006-11-13
hi hush_k

i've the same laptop as you and i will describe how I installed Ubuntu.

download the **alternate** cd of ubuntu here
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease")

boot from the cd an follow the instructions on the screen

After the installation boot your system, gdm will return an error because X wont start. This is because the video drivers are not properly installed. to slove this problem type this in the terminal. ( if necessary press Alt + F2 for terminal ).

```

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --ovt=Xv

```

after this you can start the x server with

```

startx

```

the video drivers are now installed, however direct rendering will probably not work. to fix this follow the instructions on the atiwiki [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

method 2 worked for me. :)

I hope this is help full to you

regards 

Hawk

---

