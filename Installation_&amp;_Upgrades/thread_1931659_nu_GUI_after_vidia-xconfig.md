---
title: "nu GUI after vidia-xconfig"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by fidas on 2012-02-25
hi forum 

after 
sudo nvidia-xconfig 

logout and ubuntu 10.10 is  
without GUI :o  only console

what can be  done to  bring back my GUI ?

thx in advance

---

### Post by 23dornot23d on 2012-02-25
If you move the configuration file out of the way like this then it will boot ok

**cd /etc/X11**

**sudo mv xorg.conf xorg.nv1conf**

---

### Post by enjoijesus94 on 2012-02-25
try to 

> sudo /etc/init.d/gdm start

> startx

---

### Post by fidas on 2012-02-25
i didn't really understood what i have to do 

i am a newbie here  

thx

---

### Post by fidas on 2012-02-25
i tried both and  still i have a no gui

---

### Post by enjoijesus94 on 2012-02-25
> **fidas said:**
> i didn't really understood what i have to do 

i am a newbie here  

thx

I Understand.

Login into the console by entering your username and password for your ubuntu machine.

after enter 
> sudo /etc/init.d/gdm start
Then
> startx

---

### Post by fidas on 2012-02-25
> **enjoijesus94 said:**
> I Understand.

Login into the console by entering your username and password for your ubuntu machine.

after enter 

Then

i did  all of this  but  lots of errors  

" unable to connect to x server "
" server error "

---

### Post by enjoijesus94 on 2012-02-25
Whats Your Graphics Card ?

---

### Post by 23dornot23d on 2012-02-26
If you want to put it back to how it was before you used my commands

do the opposite .... 

> **cd /etc/X11**

**sudo mv xorg.conf xorg.nv1conf**

All the command did was to move the xorg.conf out to see if it was the xorg.conf
that was causing problems .... I do this on mine as the flat screen TV will not pick up
from boot up with the Nvidia driver set to run from it.

So to put it back as it was at the beginning .... just do this below .....

> **cd /etc/X11**

**sudo mv xorgnv1.conf xorg.conf**

Then its as it was to start with .....

The other commands that were given will not cause any problems either

startx basically starts the x server ( which gives you the graphic display )

and gdm .... is the ( gnome desktop manager ) ......

______________________________________________________

The thing you are missing is a valid display mode ....... 

What else did you do before running 

nvidia-xconfig

as all that that one command does is to create the xorg.conf

____________________________________________________________

So nothing has really changed unless you installed a new Nvidia Driver at
some point ....... 

You can always re-install the latest Nvidia driver - if your internet
connection is working ok ..... by doing the following.

[B]sudo apt-get update
sudo apt-get install nvidia-settings
sudo apt-get install nvidia-current
sudo nvidia-xconfig
[/B]
Then reboot your computer ......

---

### Post by fidas on 2012-02-26
> **enjoijesus94 said:**
> Whats Your Graphics Card ?

evga geforce 550Ti gtx

I was not able to install Ubuntu 11.10 with this card only 10.10 worked.:(

i got some errors when start to install 11.10

---

### Post by fidas on 2012-02-26
thx for your help but  i did re install seemed  to be the fastest according to  my low ubuntu knowledge. :)

---

