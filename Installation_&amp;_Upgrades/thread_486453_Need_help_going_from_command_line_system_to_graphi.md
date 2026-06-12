---
title: "Need help going from command line system to graphical system"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by mmathur on 2007-06-28
I could use some help with installing Feisty as command line system and then installing what I need to convert the system to have a graphical user interface.

The reason I am installing Ubuntu as a command line system first is because I am setting up the system on a machine with a Logical Volume (LV) setup and only the alternate install CD will allow me to setup the install to use the LV.

Can someone help me by telling me what command I will need to run to install all the components I need to convert my command line system to a system with a graphical UI (e.g. GDM, Xorg...or something, etc). 

I have tried this by following some directions I found for edgy and I reconfigured the Xorg server.  
I ran this command: 
sudo apt-get install gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base usplash-theme-ubuntu

The problem I'm having is that after I start up the machine and enter in the user name and password, the system starts logging in and then it just hangs.  All I have is the tan background color and a cursor...no icons or menus and the mouse buttons don't do anything.  I can change my session and login to an openbox session, but that doesn't get me what I need and I can't start a web browser in the openbox session.  Any help would be appreciated.
Thanks.

---

### Post by kevinlyfellow on 2007-06-28
Do you know if the window manager is starting up (or trying to)?  If it isn't try putting 'openbox' as an option on the kernel line in grub.

---

### Post by mmathur on 2007-06-28
How can I check if the window manager is trying to start up?

I do notice that the icon with the foot print (which I think is gnome display manager???) is missing after I log into the machine.  All I get is two icons that appear instead of three icons when I load off of the live CD.

---

### Post by kevinlyfellow on 2007-06-29
Hmmm...  ok, why don't you try this

run the commands
```

sudo rm -r ~/.gconf
sudo apt-get install ubuntu-desktop
```

and see if you can log in.  What this will do is install the planned out desktop found in a normal ubuntu install.  From my understanding you have gdm (where you put in your username and password to login) working, correct?

If your happy with that setup, you can safely remove openbox (that's an alternative window manager, metacity is default).

---

### Post by mjgrim on 2007-08-14
I think you can find what you're looking for in [this guide]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

---

