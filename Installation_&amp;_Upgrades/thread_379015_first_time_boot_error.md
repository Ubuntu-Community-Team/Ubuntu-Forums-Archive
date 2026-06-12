---
title: "first time boot error"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by zzfive on 2007-03-08
i successfully installed ubuntu on my hp pavilion laptop and windows boots fine but when i boot ubuntu it goes past the loading splash screen and then the monitor cuts off and just has a bunch of grey lines and nothing happens any one have any idea of what might be happening and how to fix it. any help is greatly appreciated

---

### Post by watson540 on 2007-03-08
what is most likely happening is xorg is trying to use a video driver that your system doesnt like. you need to boot into 'single user' or 'safe mode'.. it's the option under the normal boot option in grub. that will get you to a console, from there you can edit your xorg.conf or install the video driver you need. hope this helps. if you need more assistance you need to post back what kind of video card you have and then post the contentts of your xorg.conf file :)

---

### Post by zzfive on 2007-03-08
i have recovery mode, so i booted into that and it froze on checking something across 2 cpus

---

### Post by watson540 on 2007-03-08
try booting into recovery only this time highlight the option and press e, then press down then press e again. remove the words quiet and splash and add vga=791 . then press enter and hit b

---

### Post by zzfive on 2007-03-08
ok that fixes it now is there any way to make it so i dont have to do that every time? thanks for the quick responces btw

---

### Post by watson540 on 2007-03-08
Yes you can and you are very welcome. Im just glad it WORKS for you! :)

What you need to do is this: open a terminal in x, type 'sudo gedit /boot/grub/menu.1st'
scroll about 3/4's of the way down, and you will see your kernel boot options just like you see them through grub when you boot. its obviously the grub config file :) , heh. so find the line for your kernel, the one that has the words splash and quiet on it and just add 'vga=791' to the end of all that junk! :) save it and you're done. if you dont want splash then remove the word splash, if you like splash but wanna know whats going on still then remove the word quiet. if you want it to act dumb then leave quiet and splash there , heh. i use the splash screen but i keep the quiet option off so i can see what happened if it locks up

---

### Post by zzfive on 2007-03-08
=] thanks a million now i get to try and get wireless working but i found a few guides on it so hopefully i can get it goin

---

### Post by watson540 on 2007-03-08
im so happy it worked for you as well, its totally by accident i found out how to stop the hardlocks, all that command does that i gave you is increase the console resolution to 1024x768. wierd huh?
post back if you have wireless problems, i have a broadcom 4311 chipset

---

### Post by zzfive on 2007-03-08
me too and i have backed up the drivers but i cant seem to get any of the tutorials to work if you have any quick tips i would greatly appreciate it because lets face it whats the fun of a linux computer that cant get online

---

### Post by watson540 on 2007-03-08
i hear ya. ok if you have the broadcom 4311 then do this. first edit the file /etc/modprobe.d/blacklist with a text editor . at the bottom type in blacklist bcm43xx

then go get the LATEST ndiswrapper. make sure you have build-essential and kernel headers. go to the folder where you downloaded the file inside of a terminal
tar -zxvf ndiswrapper.tar.gz
cd ndiswrapper*
sudo make
sudo make install
do a search on your windows drives for a file called bcmwl5.inf 
then type ndiswrapper -i /path/to/bcmwl5.inf
should see stuff on the screen then, it will be installed. then type modprobe ndiswrapper ..if it all works then type ndiswrapper -m to add it to your startup options so it starts when you boot. they have a built in driver for these cards but i havent gotten it to work yet so i use ndiswrapper hope this helps

---

### Post by zzfive on 2007-03-08
i get a permission error when executing modprobe ndiswrapper i must be running the wrong terminal or in the wrong mode but im new to ubuntu

---

### Post by watson540 on 2007-03-08
no im sorry you need to do this.
sudo modprobe ndiswrapper
i forgot to tell you to use the command 'sudo' sudo tells linux you want to run it as a super user.

---

### Post by zzfive on 2007-03-08
i tried that and i just get a fatal error. any idea?

---

### Post by watson540 on 2007-03-08
i need to know the error, usually a fatal error means that the module isnt there which would mean you didnt get ndiswrapper correctyl installed. i just remembered though. there is a program called automatix that will install ndiswrapper for you! go download that. good luck

a few other apps out there will install it for you too googke it :)

---

### Post by zzfive on 2007-03-08
Error inserting ndiswrapper: (path) invalid arguement


any ideas?

---

