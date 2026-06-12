---
title: "How do I setup the desktop shell?"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by tlouly on 2008-03-19
I have installed unbuntu 7.10 server.  I am at the command prompt.  How do I get to the the desktop shell?

---

### Post by chucky chuckaluck on 2008-03-19
do you have a desktop installed, or just the server edition?

---

### Post by tlouly on 2008-03-19
just the server edition.  i also can't get out to the internet just found that out.  i have the ip set but dns not set.

---

### Post by chucky chuckaluck on 2008-03-19
if you want a desktop, you have to install one, in addition to 'x' and a few other things. why did you install the server edition?

---

### Post by tlouly on 2008-03-19
i thought i can install a desktop shell for server edition.

---

### Post by banewman on 2008-03-19
I've done that and have a light fast system now. :)
But to get the desktop installed you'll need a net connection working...
then -
sudo nano -B /etc/apt/sources.list - and uncomment repositories, comment the cd
sudo apt-get update
sudo apt-get install xorg xterm wdm fluxbox menu synaptic dillo xchat conky thunar - is what apps I installed - you can install whatever you like
sudo dpkg-reconfigure xserver-xorg - to set the graphics
sudo /etc/init.d/wdm start - to use the graphical login and start you're new desktop
:)

---

### Post by AnRa on 2008-03-19
Do "sudo tasksel" and then select "Ubuntu desktop". ;)

---

### Post by tlouly on 2008-03-19
Anra - i am running that command was able to select unbuntu desktop now it is at the installing packages at 0% for the longest time, any ideas?

---

### Post by banewman on 2008-03-19
It should be ubuntu-desktop.
:)

---

### Post by Sef on 2008-03-19
To get a desktop, you could simply type or paste in these commands:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

Replace ubuntu with Kubuntu, xubuntu, fluxbuntu, icewm, or there might be some others in the repositories.

---

### Post by chucky chuckaluck on 2008-03-19
in my view, there's no point in doing a server installation and then installing (x.k)ubuntu-desktop. 

if you've done a server installation, chances are you don't want a whole mess of stuff. if you want a desktop, you need to do something like *sudo apt-get install x-window-system-core* and then install a window manager that you like (*sudo apt-get install moreminimalthanthoubox*).

---

### Post by OrangeCrate on 2008-03-20
<snip>

Posted in wrong thread.

---

