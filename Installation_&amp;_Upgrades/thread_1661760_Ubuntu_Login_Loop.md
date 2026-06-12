---
title: "Ubuntu Login Loop"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by stolenwhisper on 2011-01-07
Hey guys, been trying on this problem for a little over 2 weeks now.

I can sucessfully install ubuntu from the cd I burned, I also media checked the cd. Anyway after installing I am prompted with the login screen where I can select the account I created and then after typing the correct password I am thrown back to the login screen.

Things I can do....

Login by using any of the tty terminals f1, f2 etc...
Login using fail safe ubuntu desktop. (seems to work just fine)
Login using the repair console. (last option on the desktop selection.)

Things I can't do....

Login using the regular ubuntu desktop.

Things i've tried

apt-get update
apt-get upgrade
removed ubuntu-desktop and reinstalled
tried using several suggestions from the IRC channel. Things like killing the x windows and restarting etc...


I am not sure why this computer seems to be having so many issues with the ubuntu desktop. Any suggestions on how to fix this would be great.


Version of ubuntu is 10.10
Computer is running a 1 ghrtz processor with less then 512mb of ram.
40.0GB hdd.

I also have limited experience using linux.

---

### Post by Rubi1200 on 2011-01-07
Hi and welcome to the forums :-)

What graphics card do you have installed and could you be a bit more specific about the exact amount of RAM?

Thanks.

---

### Post by stolenwhisper on 2011-01-09
I think 384mb of ram. I have a 256 stick and a 128 stick. I'm not sure on the graphics card, its an old computer with a built in video device.

New problems.... installer hangs and then crashes when it gets to installing system. Works fine before and during copying files. I'm thinking it has something to do with the video device.

Any work arounds? Also, i don't seem to have another blank cd or dvd laying around, is there a way to just install the CLI for ubuntu from the ubuntu desktop cd?

---

### Post by stolenwhisper on 2011-01-09
Ok, i managed to find a work around to this issue and it seems to be stable and working 100%.

What I did

Wiped HDD from the desktop install
Downloaded and burned a copy of ubuntu server 10.10
Installed Ubuntu Server 10.10
sudo su root
apt-get update
apt-get install ubuntu-desktop
reboot

after reboot it booted into the ubuntu GNOME desktop and allowed me to login.

I have no idea what the issue was with the first cd, but either way she's working now and thanks for your help guys.

---

