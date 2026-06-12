---
title: "Missing Desktop View in Ubuntu 18.10 after installing Nvidia driver"
date: 2018-11-15
forum: Installation &amp; Upgrades
---

### Post by persiano2 on 2018-11-15
Hello friends. I  recently installed Ubuntu 18.10, but when I install  the Nvidia graphics  driver through the terminal, after completing the  installation and  restart, I encounter this error message, does anyone  know what is and  should be done. ? 
in another forum somebody said that  use Alt+Ctrl+F1, I did but it doesn't work.

[IMG]https://i.imgur.com/sq1gEaU.jpg[/IMG]

---

### Post by ajgreeny on 2018-11-15
Which nvidia card have you got and which driver did you install and how did you install it, in detail please?
Telling us you installed it through the terminal does not give us enough information.

---

### Post by persiano2 on 2018-11-15
> **ajgreeny said:**
> Which nvidia card have you got and which driver did you install and how did you install it, in detail please?
Telling us you installed it through the terminal does not give us enough information.

Hi,Thanks man! My Graphic card is gt720m for laptop MSI CX61 8gig Ram & CPU Corei5 and Integrated 4600 HD Intel Graphic card, I installed Ubuntu in First Primary Partition and ext4 format.
My way was this :
$ sudo add-apt-repository ppa:graphics-drivers/ppa

$ ubuntu-drivers devices

and the version of driver identified for me was 340.107 so:

$ sudo ubuntu-drivers autoinstall

$ sudo apt install nvidia-340

and the driver installed completely

I reinstalled ubuntu and this problem occurred again.

---

### Post by kc1di on 2018-11-15
if you reinstalled ubuntu you will need to reinstall the driver also.

---

### Post by persiano2 on 2018-11-15
> **kc1di said:**
> if you reinstalled ubuntu you will need to reinstall the driver also.

I did, but these errors were the result again. The Ubuntu startup page comes up, but instead of the desktop display, these appear.

---

### Post by 23dornot23d on 2018-11-15
Seems the same problem keeps happening with Nvidia - optimus cards ........
[https://www.geforce.com/hardware/notebook-gpus/geforce-gt-720m/specifications](https://www.geforce.com/hardware/notebook-gpus/geforce-gt-720m/specifications)

have a look see if **/etc/X11/xorg.conf **is there please ......

sudo mv /etc/X11/xorg.conf     /etc/X11/xorg.conf-last-used

if it is move it and then install bumblebee

sudo apt install bumblebee
sudo apt install lightdm

See if you get a change ......... its worked a couple of times already.

Mine is a gt540m .... did the above and worked ...... and a previous post we went through quite a lot before doing the above.
[https://ubuntuforums.org/showthread.php?t=2404813&page=7](https://ubuntuforums.org/showthread.php?t=2404813&page=7)

---

### Post by persiano2 on 2018-11-15
> **23dornot23d said:**
> Seems the same problem keeps happening with Nvidia - optimus cards ........
[https://www.geforce.com/hardware/notebook-gpus/geforce-gt-720m/specifications](https://www.geforce.com/hardware/notebook-gpus/geforce-gt-720m/specifications)

have a look see if **/etc/X11/xorg.conf **is there please ......

sudo mv /etc/X11/xorg.conf     /etc/X11/xorg.conf-last-used

if it is move it and then install bumblebee

sudo apt install bumblebee
sudo apt install lightdm

See if you get a change ......... its worked a couple of times already.

Mine is a gt540m .... did the above and worked ...... and a previous post we went through quite a lot before doing the above.
[https://ubuntuforums.org/showthread.php?t=2404813&page=7](https://ubuntuforums.org/showthread.php?t=2404813&page=7)

I can't type anything ,That's just a black blank screen, where should I use these commands? sorry I'm new in Linux

---

### Post by 23dornot23d on 2018-11-15
When you boot up

Choose the second option

[B]Advanced menu
[/B]
Then choose the second option again **recovery mode** ( it loads with a basic setup ) from there you will be able to do the commands shown.

---

### Post by persiano2 on 2018-11-15
Thanks my friend, I Installed Linux Mint already,and that's really awesome, without any problem my nvidia driver installed, and after restart everything is Perfect, and I really prefer Mint 19 to Ubuntu 18.10. 

[IMG]https://i.imgur.com/CJphCU3.png[/IMG]

---

### Post by 23dornot23d on 2018-11-15
Wow ..... as long as you have a working system - that is all that matters ....... :D

Best of Luck ..... looks good.

---

### Post by persiano2 on 2018-11-15
> **23dornot23d said:**
> Wow ..... as long as you have a working system - that is all that matters ....... :D

Best of Luck ..... looks good.

Thanks my friend, :grin:

---

### Post by lowgman on 2018-12-27
[COLOR=#1D2129][FONT=Helvetica]nVidia driver-340 is working without bumblebee and mint distro, enter commands in this way:

sudo apt install gnome-session-flashback[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]sudo apt install lightdm[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]sudo apt install nvidia-340

Can anybody create auto-patch for this fix?
[/FONT][/COLOR]
[IMG]https://i.imgur.com/Nk5nWx4.png[/IMG]

---

