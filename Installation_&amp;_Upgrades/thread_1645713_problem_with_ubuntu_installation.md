---
title: "problem with ubuntu installation"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by ubunt12 on 2010-12-14
hi, i recently bought an acer aspire 5742z and ive tried to install ubuntu over windows 7 64 bit on my drive to make ubuntu 32bit my os like i did with my desktop with no problems.    The installation completes without any problems and then reboots but then when it reboots, instead of loading the ubuntu desktop it tells you to login to a terminal then its just a big terminal to execute commands.

Please can someone help me,
Thanks.

---

### Post by amsterdamharu on 2010-12-14
Since you don't have a gui I guess you need a pen and paper, after you log in to the terminal can you type the following commands?
```
sudo service gdm stop
startx
```Write down any output you get there and have a look in the Xorg.0.log (or any other Xorg logs) remember when typing a command you can press tab twice to see what logs are there.
[COLOR=Red]Note that the X in Xorg... is a capital X[/COLOR]
So when you type nano /var/log/Xor(press tab twice) you'll see a list of available logs.
```
nano /var/log/Xorg.0.log
```Check out any line beginning with (EE) or (WW)

I'm not sure if xforcevesa still helps but you can give that a try:
When booting press shift to see the boot menu -> select Ubuntu and check around for an option to edit this entry -> add xforcevesa in the end and give it a go.
This might give you a low graphics desktop but you still need to install the Intel drivers for the card in your laptop.

Since you're running the latest kernel you might just need a driver version that is not in the Ubuntu repository to make it work. Add a repository that has more current (and unstable) drivers:
[https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

---

### Post by ubunt12 on 2010-12-14
thanks ill try it now

---

### Post by ubunt12 on 2010-12-14
first command:
unknown instance
and second command startx left a blank screen, i had to press power button to turn it off

---

### Post by ubunt12 on 2010-12-14
i dont understand, when i boot from usb it works fine until i install it and reboot from HDD

---

### Post by amsterdamharu on 2010-12-14
Ok try the command on tty1:
press control + alt + F1
Log in and type the commands:[FONT=monospace]
[/FONT]```
sudo service gdm stop
startx
```If you have a blanc screen press control + alt + F1 again.

> when i boot from usb it works fine
Probably because the install tries a better video mode and fails.

---

### Post by ubunt12 on 2010-12-15
nope still doing the same thing, the screen goes blank

---

### Post by amsterdamharu on 2010-12-15
Ok, you can try to log in and have a look in the Xorg.0.log  (or any other Xorg logs) remember when typing a command you can press  tab twice to see what logs are there.
So when you type nano /var/log/Xor(press tab twice) you'll see a list of available logs.
[COLOR=Red]Note that the X in Xorg... is a capital X[/COLOR]
```
nano /var/log/Xorg.0.log
```Check out any line beginning with (EE) or (WW)

I'm not sure if xforcevesa still helps but you can give that a try:
When booting press shift to see the boot menu -> select Ubuntu and  check around for an option to edit this entry -> add xforcevesa in  the end and give it a go.
This might give you a low graphics desktop but you still need to install the Intel drivers for the card in your laptop.
For example (on mint) I see the line
```
linux /boot/vmlinuz-2.6.24-27-generic root=UUID=c728500b-6aed-4aa2-972f-eb6d8723c2a1 ro quiet splash
```
and add xforcevesa
```
linux /boot/vmlinuz-2.6.24-27-generic root=UUID=c728500b-6aed-4aa2-972f-eb6d8723c2a1 ro quiet splash xforcevesa
```


Since you're running the latest kernel you might just need a driver  version that is not in the Ubuntu repository to make it work. Add a  repository that has more current (and unstable) drivers:
[https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
You need an internet connection and it might take a while to update your system. Reboot and see what happens

---

### Post by ubunt12 on 2010-12-15
Thanks for the help but ive solved it, i held shift before ubuntu bootup then ran restore mode or whatever its called then theres a few options one of which is to fix broken dpkgs.

---

