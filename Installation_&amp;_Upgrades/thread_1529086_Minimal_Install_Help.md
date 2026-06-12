---
title: "Minimal Install Help"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by pbolle on 2010-07-11
Im trying to do a complete minimal install and im stuck with what optino to choose at one of the last questions where it says - 

What packages would you like to install
and it says like
Ubuntu desktop
Kubuntu DEsktop
Edubuntu desktop
etc etc.

which option should i choose if i just want to go into command line and install my packages from there??

thanks

---

### Post by daniel_w93 on 2010-07-11
could you list all the options that you have please?
But from the 3 you've got there I'd choose ubuntu desktop cause there aren't as many useless default programms instaled with it

---

### Post by ks07 on 2010-07-11
I presume the prompt you are referring to is 'tasksel', which also runs on installation of ubuntu server. If you scroll all the way to the bottom of the list there is an option for 'manual package installation'. Highlight it with the arrow keys, spacebar to select it and then press enter. This should exit the program and dump you to a command line. :)

---

### Post by pbolle on 2010-07-11
> **ks07 said:**
> I presume the prompt you are referring to is 'tasksel', which also runs on installation of ubuntu server. If you scroll all the way to the bottom of the list there is an option for 'manual package installation'. Highlight it with the arrow keys, spacebar to select it and then press enter. This should exit the program and dump you to a command line. :)
when i do that it brings me to a somewhat graphical interface that lets me pick and choose the packages..

---

### Post by mikewhatever on 2010-07-11
Don't install anything with 'desktop', because it won't be anywhere near minimal. Gnome-core or kdebase would be better choices. Better still, tell us what you need.

---

### Post by pbolle on 2010-07-12
what i want is just a command line..
i did it once, then reformatted to try and do it again and now dont remember how i did it

my main goal is to create a lxde based distro made from ubuntu

i just want a command line after the install.

i just tried not checking any of the boxes and when i restarted i just got a blinking cursor for 40 minutes +

---

### Post by wojox on 2010-07-12
When you get to the 

**boot:** type *cli* and it should just install the command line and won't bother opening taskel. From there you can reboot to a terminal and apt-get or aptitude whatever you want.

---

### Post by wojox on 2010-07-12
If for some strange reason it does open Taskel don't mark anything and just ignore that screen.

---

### Post by pbolle on 2010-07-12
> **wojox said:**
> When you get to the 

**boot:** type *cli* and it should just install the command line and won't bother opening taskel. From there you can reboot to a terminal and apt-get or aptitude whatever you want.
im sorry but i dont understand 
when i get to the
boot:
when i restart now i just get the blinking cursor and i cant do anything..

---

### Post by thahir1986 on 2010-07-12
Just download ubuntu mini from [here ]("https://help.ubuntu.com/community/Installation/MinimalCD")

and write the iso file as cd and connect the system with internet connection and boot with cd.

and in the install package option like

ubuntu-desktop
kde-desktop
etc...,.

dont select anything if u want the command line boot....[-X


after the installation, login with ur user account and

for lxde installation type

```
sudo nano /etc/apt/sources.list
```

and in the end of the file just append, (for ubuntu 8.04 hardy heron, if ubuntu 9.04 jaunty jackolope just replace jaunty instead for hard)

```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main

```

and press control + o  to save and control + x to exit.

after that 

```
sudo aptitude update
sudo aptitude install lxde lxterminal
```


reboot and enjoy ubuntu mini with lxde desktop.....=D>


I hope this one useful for u.:popcorn:

---

### Post by dzon65 on 2010-07-12
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Once you get to the command line:
sudo apt-get update
sudo apt-get install xorg gksu menu lxde synaptic
sudo etc/init.d/gdm start (or:sudo service gdm start)
You will then be looking at a lxde login screen.

---

### Post by mörgæs on 2010-07-12
Install as little as possible from the menus. After the absolute minimal is installed, boot and install the rest from the command line. 

The Psychocats tutorial or 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
will tell you what to choose.

There is also a script for installation, if you prefer:
[http://perfectbuntu.category5.tv/](http://perfectbuntu.category5.tv/)

---

### Post by pbolle on 2010-07-12
thanks for your help guys but i tried all the methods and i keep ending up with a blinking cursor..

i dont know what the problem could be... :(
please help :(

---

### Post by thahir1986 on 2010-07-13
did ur installation finish with the reboot message ?

---

### Post by pbolle on 2010-07-13
yes it did finish with the reboot message..

---

### Post by pbolle on 2010-07-13
bump 
please help :(

---

### Post by mörgæs on 2010-07-13
For principal reasons I don't help a bumped thread. Sorry.

---

### Post by pbolle on 2010-07-15
wow.
so because i need help to solve this problem and nobody will look at a thread 6 pages back you will prevent me from using this distribution?
thanks trollface.jpg

---

### Post by Megaptera on 2010-07-16
I hope someone is kind enough to help! Sorry but I've not the experience to help. No idea why someone would ignore a 'bumped' thread most unhelpful 

Not in keeping with the spirit of Ubuntu one might say. "Ubuntu is an ancient African word meaning 'humanity to others".

---

### Post by pbolle on 2010-07-16
> **Megaptera said:**
> I hope someone is kind enough to help! Sorry but I've not the experience to help. No idea why someone would ignore a 'bumped' thread most unhelpful 

Not in keeping with the spirit of Ubuntu one might say. "Ubuntu is an ancient African word meaning 'humanity to others".

finally someone understands..
Thank you :)
I obviously needed help and nobody wanted to help so I bumped it:P

---

