---
title: "nvidia driver"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by pedrom169 on 2008-01-12
tried installing an nvidia driver on my computer
the file is NVIDIA-Linux-x86-169.07-pkg1.run
someone told me to type in cd (untill i get to directory)
the sudo sd NVIDIA-Linux-x86-169.07-pkg1.run
it said i cannot open file


if im doing something wrong
can someone tell me what i have to type in the terminal

the file is stored on desktop
thanks

Peter

---

### Post by PmDematagoda on 2008-01-12
Move to the Desktop using:-
```
cd ~/Desktop
```
Then list the files using:-
```
ls
```
After that, use the list and replace "filename" with the Nvidia installer filename:-
```
sudo sh filename
```

That should start the installer.

---

### Post by Partyboi2 on 2008-01-12
Go to a terminal Ctrl+Alt+F1-F6
back up xorg
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```stop gdm
```
 sudo /etc/init.d/gdm stop
```change to desktop directory```
cd Desktop
``` install driver```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```start gdm again```
sudo /etc/init.d/gdm start
```

---

### Post by pedrom169 on 2008-01-12
> **Partyboi2 said:**
> Go to a terminal Ctrl+Alt+F1-F6
back up xorg
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```stop gdm
```
 sudo /etc/init.d/gdm stop
```change to desktop directory```
cd Desktop
``` install driver```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```start gdm again```
sudo /etc/init.d/gdm start
```

i did what you told me
when i got to 
```
 sudo /etc/init.d/gdm stop
```
it went to a black screen and carried on typing what was on the list
and it didnt do nothing

thanks
Peter

---

### Post by PmDematagoda on 2008-01-12
When you reach the black screen, press Ctrl+Alt+F1 to get a different terminal, that should allow you to enter the commands.

---

### Post by pedrom169 on 2008-01-12
thank you for reponse
but when i press ctrl + alt + f1 when on block screen i get the terminal. type my user name and password but i cant change directory to desktop.

i do both cd desktop and

cd ~/desktop

both dont work.

thanks
Peter

(p.s. yes i am new at ubuntu ;p)

---

### Post by Pumalite on 2008-01-12
Make sure you have build-essential:
sudo apt-get install build-essential
From a normal running system, pres Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxx.run

Accept license

Let driver compile the module into your kernel

Let driver reconfigure your xorg.conf file

sudo /etc/init.d/gdm start

---

### Post by pedrom169 on 2008-01-12
just to ask what is the path to desktop.
just if i get it wrong :)

thanks
Peter

---

### Post by Pumalite on 2008-01-12
Move it from your Desktop to your /home/username.
sudo sh /home/username/NVIDIA-Linuxxxxxx.run

---

### Post by Shazaam on 2008-01-12
Also for future reference when you want to cd to your desktop make sure you capitalize the d in desktop=

cd ~/Desktop

---

### Post by pedrom169 on 2008-01-13
thank you guys it is installed and working now :)

---

### Post by Pumalite on 2008-01-13
Good for you. Good luck.

---

### Post by MCBTunes on 2008-01-13
> **Pumalite said:**
> Good for you. Good luck.

Hi. I was hoping you could help me as well.  I just did the same process for my BFG 8800GT, the pkg2 nvidia driver. However after starting gdm again my fan started going full blast... I restarted my machine and as it was shutting down it displayed a bunch of errors. As it booted back up again and it said it was going into low-res mode and could not find my video card. I clicked continue and my computer started beeping like crazy so I hard reset.... now I'm back in windows.... any idea how I can solve this problem?

---

### Post by MCBTunes on 2008-01-13
I think I have royaly screwed things up.  I decided to go into configure and choose my monitor,  then I had the ability to set the higher resolution. I was happy, then when I booted up everything was massively distorted and there were several username/password sign in boxes and several mouse pointers across the screen, I could still type my user name and password in, but as soon as I got to the desktop everything was messed up beyond recognition.

---

### Post by PmDematagoda on 2008-01-13
MCBTunes, I strongly suggest that you read this [thread]("http://ubuntuforums.org/showthread.php?t=665018") carefully since the OP had a Nvidia 8800GT with pretty much your same problems, so that can help you.

---

### Post by Partyboi2 on 2008-01-13
Make sure you are installing the correct driver.
Go to a terminal and reconfigure xserver, which should allow you to have a desktop you can work with while trying to get the correct driver installed.
In a terminal
```
sudo dpkg-reconfigure xserver-xorg
```
Answer all the questions, if you are unsure what to choose then leave it at the deafult which is the one that is displayed highlighted on screen. But make sure you choose "nv" instead of "nvida"

---

### Post by BLTicklemonster on 2008-01-13
And if that don't work, chose vesa instead of nv or nvidia,

---

