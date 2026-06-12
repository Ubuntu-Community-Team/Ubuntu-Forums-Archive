---
title: "How do I do a minimal install, like this?"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by Higgins909 on 2015-09-27
I'm wanting to do a minimal install, of ubuntu server, install mate on it, and use it as a desktop.
Maybe where I went wrong was trying to do this on a copy of ubuntu server?
I want to get this going on a vm, then fairly decent for a while on my laptop.

Need things like
wifi
sound
lan
video driver
proxy use

and with those installed, hope I can install thing like this on my own:
Lightworks
Gimp or something like that
some games
firefox
docky

I've done something similar on a copy of ubuntu desktop, but I don't really think it became light...
it was more of just a gui switch, and the same login screen that I did n didn't like.

Edit: I know there is ubuntu mate and itself might have some sort of minimal install mode, but this is for learning purposes, to try and use slack and arch one day.

---

### Post by DK1993 on 2015-09-27
There is a nice long form tutorial on how to do this here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) and for Ubuntu Server specifically: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Caution: There are a lot of steps involved, however it is very thorough and explains every step and the necessity of each step. Good luck :)

---

### Post by Bucky Ball on 2015-09-27
For a minimal install there are not a lot of steps involved and don't use the server ISO, a livecd customisation or anything else but the mini.iso which is there for the purpose. 

Go [here]("https://help.ubuntu.com/community/Installation/MinimalCD")> Download the ISO> Create install media, disk or USB> plug in an ethernet cable> install> don't choose a machine profile when you get to that bit (tasksel).

When you've finished and reboot the computer you should be able to log in and install whatever you like. To do this, you are going to need to do some research to find the command line names of the programs you want to install. You are also going to need to settle on a desktop environment, windows manager, etc. ...

A very basic install which should get you up after the first boot would look something like this:

```
sudo apt-get install xfce4 synaptic gimp lightdm firefox pcmanfm lxterminal xorg
```

That *should* get you up and anything else you need you can install via Synaptics or a terminal. It gives you, in order, a desktop environment, a package manager, gimp, a desktop manager, a web browswer, a file manager and a terminal. Example only, your line might look different, depending on what you like.

A minimal install is well worth the effort and is all I've used for about five years now. :)

---

### Post by Higgins909 on 2015-09-29
Could someone tell me mini.iso vs server minimal install?
The server minimal install is using around the same storage on the hdd and is using 183mb of ram vs 315mb on the mini...
I even installed xorg I think it was and MATE but not running as I failed to config, on the server.
The mini install also took like a hour because of purple screens taking their time to load.

That's a good list for me man, I would of had to find out later what I actually needed, now I can just google a list of terminals and package managers and file managers and choose.

---

### Post by Bucky Ball on 2015-09-29
If you want a minimal install, use the mini.iso. You are not wanting to use this as a server are you? If so, the server iso. If you do a mini and decide you want to use the machine as a server, simply install the appropriate components from Synaptics, terminal or whatever package manager you want.

The server install comes default with software for servers which, if you're not using your machine as a server, is redundant and you don't need it.

---

