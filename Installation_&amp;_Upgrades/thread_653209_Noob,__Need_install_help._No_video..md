---
title: "Noob,  Need install help. No video."
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by mrchaos101 on 2007-12-29
Did the isntall. I see Ubuntu logo and progress bar.  Few min later monitor is off with amber light.

I read another post and I pressed ctrl+alt+f1

I am at a command prompt of some sort

ubuntu@ubuntu:~$

says something about there is no warranty etc.

Graphics card is nVIDIA Geforce FX 7300 GS

This is a new system build:
AMD 64 x2 CPU
MSI  k9n6gm  with nForce 410 Chipset
Maxtor 100GB Sata HDD
Liteon IDE DVD/CDRW drive
512mb DDR2

I downloaded the 7.10 OS that said for AMD and Intel 64bit.

---

### Post by taurus on 2007-12-29
At that prompt, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to the GUI login screen and restart X with <Ctrl><Alt>Backspace.

Or you can reboot if you wish.

```
sudo shutdown -r now
```

---

### Post by mrchaos101 on 2007-12-29
Any chance on this topic you all can tell me what this stuff is so I can learn.

example:

if it was dos and I need to do these commands
cd \
md temp
cd temp
copy c:\folder\.*

cd  meanc change director \ means root so cd \ is chaning you back to the root director
md temp  md means make directory temp is the name of the new directory  so we made a dir named temp
cd temp  cd is change direcorty temp is the dir we are going into
copy c:\folder.*  means we are going to copy all files that are in a direcotry named folder to the temp folder we are currently in.

Any way... I have no clue what these commands that are being listed mean or do.  I want to learn this as I go.... if you have the time.

---

### Post by taurus on 2007-12-29
> **mrchaos101 said:**
> Any chance on this topic you all can tell me what this stuff is so I can learn.

example:

if it was dos and I need to do these commands
cd \
md temp
cd temp
copy c:\folder\.*

cd  meanc change director \ means root so cd \ is chaning you back to the root director
md temp  md means make directory temp is the name of the new directory  so we made a dir named temp
cd temp  cd is change direcorty temp is the dir we are going into
copy c:\folder.*  means we are going to copy all files that are in a direcotry named folder to the temp folder we are currently in.

Any way... I have no clue what these commands that are being listed mean or do.  I want to learn this as I go.... if you have the time.

Problem is Unix/Linux uses /, not \.  So if you want to move to root directory, you have to run

```
cd /
sudo mkdir temp  <-- to create a temp directory
cd temp
sudo cp /diretory_name/* .
```
The reason you have to include sudo in front of those commands because you don't have write permissions outside of your $HOME directory.  So if you want to write outside of your $HOME directory, you have to be root and sudo command would let you do that.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pumalite on 2007-12-29
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by mrchaos101 on 2007-12-29
ah ok got ya.

On this 
sudo dpkg-reconfigure -phigh xserver-xorg


sudo is taking "god mode" for the command

pkg-reconfigure -phigh xserver-xorg   what is this command and the switches doing?

Result on seemed to just pull up a menu to allow me to change the screen res.  I changed it to low 800x600.

Now it seems to be ok. But I would like to know what I did and why.

---

