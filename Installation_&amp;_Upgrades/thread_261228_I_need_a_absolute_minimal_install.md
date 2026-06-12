---
title: "I need a absolute minimal install"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2006-09-19
Hello i would like to set up a ubuntu server to do 3 basic things
1. squid server  2. apache web server    3 . file server (ssh) 

I would like a graphical environment but i only have 2 10gb hd's installed and they are raid striped but the install is taking up to much space becuase the install is on one of the hard drives which is 10gb and i only have about 7gb hd left so that meens i have only 7gb on the other hd so is it possible if i could apt-get remove ...... everything but the base and x server or could i install ubuntu server and apt-get x server a gnome-desktop

---

### Post by croak77 on 2006-09-20
You can remove porgrams but it might be easier to do a server install then apt-get xserver-xorg x-window-system-core and whatever else you want. You don't have to use GNOME if space is an issue. Try xfce4 or fluxbox. There are plenty of small, lightweight window managers out there.

---

### Post by CameronCalver on 2006-09-20
ok so would apt-get install xserver-xorg && apt-get install x-window-system-core && apt-get install fluxbox 
would that give me a full graphical workspace 
also how would i go about editing my netowrk config eg system admin networking

---

### Post by CameronCalver on 2006-09-20
I have came to the conclusion that i would like to just install the normal ubuntu and uninstall things becuase i am familiar with the normal gnome evvirnment.
Can someone tell me a apt-get remove command that will remove every app that i dont need becuase all it is going to need is apache squid and ssh and i noticed in synaptic there is a base system cat could i just uninstall everthing exept things that are in the section

---

### Post by croak77 on 2006-09-20
Youy can just do apt-get once , that's what I did, sudo apt-get xserver-xorg x-window-system-core fluxbox. If you want a login manager, install xdm or you'll just have to create a /home/username/.xinitrc with, 'exec fluxbox', in it. So when you type startx it will start fluxbox. As far as network config, what do you use now?

---

### Post by croak77 on 2006-09-20
If you are going to uinstall packages, just be careful not to uninstall anything critical. You can also use a tool called deborphan to show unneeded dependencies but I'm not sure how accurate it is. Just be cautious.

---

### Post by kerry_s on 2006-09-20
server install
login >sudo su < to become root
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repo's
apt-get update
apt-get install x-window-system-core xterm synaptic 
apt-get install gdm fluxbox(or icewm, wmaker, gnome-core, kdebase...)
reboot
select your wm in session and login


I split the apt-get up because if you do it all at once it grabs gnome stuff as depends for gdm, but if you do it after it will be smaller with only whats needed.
This would give you a basic desktop you can drop gdm if you want to use startx, you can also drop synaptic if you prefer apt-get. I recommend synaptic so you can see all the stuff installed(status>installed) and trim it even more by removing stuff you don't need, like the extra drivers for vid cards you don't have. I recommend gdm or the wm dosen't really work right when started by startx.
After you trim with synaptic and install what you want get rid of the usr/share/doc and usr/share/man that will give you back 150+mb. I'm sure if you stick with just server stuff you should be able to get under 500mb.
I have a fluxbox and wmaker minimal install. Fluxbox is 640mb with all the basic apps for internet browsing. Wmaker is 571mb with the internet stuff installed. Try different things till you find the one that matches your machine. I've been playing with wmaker for only 3 days so i'm still learning about it. Here's wmaker that i'm playing with now(i use duel monitors)You can see my size in conky. ;)

---

### Post by CameronCalver on 2006-09-20
so if you had nothing on that server how much does the installation take up and also why not dam small linux

---

### Post by kerry_s on 2006-09-20
DSL is way to limiting and because of it's cut down nature you'll get alot of problems with simple things. It's far better to use the server install with the alternate cd and build your desktop to you. I use almost the same apps as DSL-N but mine are more up to date and apt-get works.

---

### Post by CameronCalver on 2006-09-20
so how much space does your install take up includng all the internet tools etc

---

### Post by kerry_s on 2006-09-20
Fluxbox is 640mb
Wmaker is 571mb

There installed on different drive's on 1 partion.
Like i said, i have alot installed that you proably won't install for your server.According to synaptic i have 457 packages installed. I usally install as i need things instead of installing all up front, that way i know i need it. ;)

---

### Post by CameronCalver on 2006-09-20
and how big is gnome and another thing if i have the ubuntu server iso image on my computer is there anyway i could put the iso image on a hard drive and then run it becuase i dont have any cdroms

---

