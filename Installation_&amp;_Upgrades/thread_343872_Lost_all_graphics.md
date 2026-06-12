---
title: "Lost all graphics"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by jayneella on 2007-01-22
I will try and explain my problem as best as i can as im an absoloute beginer so please bare with me.
I installed some updates yesterday from the pop up icon, after doing this i received an error message ""The application Nautilus has quit unexpextedly, You can 
inform the developers to help them fix it or you can restart the 
application right now" I tried restarting the app by clicking ok and just kept getting the same error.
I re-booted the system and since then i have had no graphics just a blank screen.
I get the login promp from ubuntu but then a blank screen.
Also somthing slighty concerning is that i noticed an error on loggin in " Asembling raid array failed" well i have a think pad T42 laptop and my brother advises me i dont have a raid array!
I hope i have given enough info.
Thanks x

---

### Post by renzokuken on 2007-01-22
sounds to me like your update screwed up the grafix drivers/server.

can you get into the CLI on boot up? when you get to the login prompt, try pressing Ctrl+Alt+F1 and see if it takes you to the command line interface. if so, then try the following and see if you can post it here.

```
sudo nano /etc/X11/xorg.conf
```

it may also be worth posting your hardware, processor, grafix cards (or chipset) etc

---

### Post by jayneella on 2007-01-22
> **renzokuken said:**
> sounds to me like your update screwed up the grafix drivers/server.

can you get into the CLI on boot up? when you get to the login prompt, try pressing Ctrl+Alt+F1 and see if it takes you to the command line interface. if so, then try the following and see if you can post it here.

```
sudo nano /etc/X11/xorg.conf
```

it may also be worth posting your hardware, processor, grafix cards (or chipset) etc


Hi there.
Im having a problem doing anything at the moment as im getting the following on turning on the laptop
"Give root password for maintenence or type control -D to continue"
Tried typing control -d but it takes me back to the same command....

---

### Post by jayneella on 2007-01-22
> **jayneella said:**
> Hi there.
Im having a problem doing anything at the moment as im getting the following on turning on the laptop
"Give root password for maintenence or type control -D to continue"
Tried typing control -d but it takes me back to the same command....

Just also tried control alt F1 as suggested and i now have the following
"Uncompressing linux ok, booting the kernel
bogl_init failed: setting screen size:cannot allocate memory Screen init failed"

---

### Post by renzokuken on 2007-01-22
ok, weird, never seen that before.......

did you have any important data on the computer or was it a fresh install? it it was fresh then may be worth installing again. otherwise, sorry, i have no idea and may be worth waiting for someone more "technically inclined" than myself

EDIT: i think it may have something to do with usplash, not sure what though, i'll carry on digging. what laptop you got?

---

### Post by jayneella on 2007-01-22
> **renzokuken said:**
> ok, weird, never seen that before.......

did you have any important data on the computer or was it a fresh install? it it was fresh then may be worth installing again. otherwise, sorry, i have no idea and may be worth waiting for someone more "technically inclined" than myself

My brother has backed up for me so i wont lose anything...i was thinking i should try installing ubuntu again...
But im stuck at the control -D screen again so i cant do a thing! :confused:

---

### Post by jayneella on 2007-01-22
> **renzokuken said:**
> ok, weird, never seen that before.......

did you have any important data on the computer or was it a fresh install? it it was fresh then may be worth installing again. otherwise, sorry, i have no idea and may be worth waiting for someone more "technically inclined" than myself

EDIT: i think it may have something to do with usplash, not sure what though, i'll carry on digging. what laptop you got?

I have a thinkpad T42

---

### Post by JamieC on 2007-01-22
As requested, try entering the root password. What 'maintenance options' are you presented with?

---

### Post by jayneella on 2007-01-22
> **JamieC said:**
> As requested, try entering the root password. What 'maintenance options' are you presented with?

I dont know what the root password is...all it states is 
"give root password for maintenance or type contol -D to continue" that's all i get. i tried control -D and and it takes me back to the same thing again.. weird!

---

### Post by jayneella on 2007-01-22
> **renzokuken said:**
> sounds to me like your update screwed up the grafix drivers/server.

can you get into the CLI on boot up? when you get to the login prompt, try pressing Ctrl+Alt+F1 and see if it takes you to the command line interface. if so, then try the following and see if you can post it here.

```
sudo nano /etc/X11/xorg.conf
```

it may also be worth posting your hardware, processor, grafix cards (or chipset) etc

Hey i managed to get out of it and have got to cli
done sudo nano etc and now appear to have some sort of file open, with options at the bottom ie get help,write out,read file..

---

### Post by renzokuken on 2007-01-22
yup, thats the one, its just a text file (opened in a CLI program called nano). the options at the bottom simply allow you to save, close, exit, etc.

do not change anything in this file yet, just scroll down (arrow keys) until you see the Section "Device". look at what is written next to "driver" and post it here, also may be worth scrolling down further and noting the screen resolutions listed.

what grafix card/chipset does your pc have?

---

### Post by jayneella on 2007-01-22
I dont get the option to scroll down and the arrow keys dont move a thing

---

### Post by renzokuken on 2007-01-22
really? weird......

have you tried Page Up and Page Down..........the arrow keys should work fine

keep holding the down arrow down, the flashing block has to move all the way down the page before it starts scrolling

apparently you can also use Ctrl+Y and Ctrl+V to move up and down pages

---

### Post by jayneella on 2007-01-28
> **renzokuken said:**
> really? weird......

have you tried Page Up and Page Down..........the arrow keys should work fine

keep holding the down arrow down, the flashing block has to move all the way down the page before it starts scrolling

apparently you can also use Ctrl+Y and Ctrl+V to move up and down pages

Hello, Sorry for the delay in responding, i cant see anything at all in this file it seems blank, i have tried all the scroll options and there is nothing there... 
My brother is trying to fix it remotely but not having any joy at all.
Any other ideas i can try?
I have downloaded the ubuntu 6.10 software to a CD incase i need to re-install but wont have a clue how to do this either as im running commands from terminal and im more a windows peep no Linux, this Linux was my bros idea! 

:confused:

---

### Post by nike984 on 2007-01-28
This is a Tip that I've learned from this forum.

login using recovery mode
At the terminal screen, 

```
cd /etc/X11
ls 

```
if there is xorg.conf.*** <==*** may be backup, or number or ~ or anything.
Choose the one that seems to be created when the system has no problem,then

```
sudo cp xorg.conf.*** xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by jayneella on 2007-01-28
> **nike984 said:**
> This is a Tip that I've learned from this forum.

login using recovery mode
At the terminal screen, 

```
cd /etc/X11
ls 

```
if there is xorg.conf.*** <==*** may be backup, or number or ~ or anything.
Choose the one that seems to be created when the system has no problem,then

```
sudo cp xorg.conf.*** xorg.conf
sudo /etc/init.d/gdm restart
```

Hi and thanks for replying so quickly. i tried the first thind you said and it says no such file or directory?

---

### Post by jayneella on 2007-01-28
> **jayneella said:**
> Hi and thanks for replying so quickly. i tried the first thind you said and it says no such file or directory?

Ok just called my brother and he has said i have no back up's at all, he had allready tried that, he does know linux quite well but is in denmark and it is really difficult getting to speak to him.
I have managed to do the forst command i was just typing it in wrong im afraid.

---

