---
title: "Ubuntu server 22.04.1 setup,  wireless networker."
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by rbcc-12 on 2023-02-24
During setup,  setup asks to "connect to network " i got to "show visible networks" 
Then it shows my connection. 
I then choose edit network and choose ip4.  The screen hangs on this screen. 
Is there something that can give me an ip address. 
John

---

### Post by MAFoElffen on 2023-02-24
For the Ubuntu Server Live Installer:
> 
The Linux server installation software, in general, does not include wireless network support packages, so it relies on the user to enable the Wi-Fi connection.

RE: [https://yping88.medium.com/how-to-enable-wi-fi-on-ubuntu-server-20-04-without-a-wired-ethernet-connection-42e0b71ca198](https://yping88.medium.com/how-to-enable-wi-fi-on-ubuntu-server-20-04-without-a-wired-ethernet-connection-42e0b71ca198)

What version of Ubuntu Server are you trying to install? When you post back with that, I will that part of the instructions to the needed packages for that version of Server...

---

### Post by ActionParsnip on 2023-02-24
Just install offline, then get online later. Keeps things simple. Did you SHASUM / MD5SUM the ISO you downloaded (or use torrents) to verify the file you downloaded is complete and consistent?

---

### Post by rbcc-12 on 2023-02-24
22.0.4.1 is the version I have installed.

---

### Post by rbcc-12 on 2023-02-24
I dont know where this goes but heres the question : 
Is there a way to get gnome to work with ubuntu server 22.1.0?

I tried three different ways and couldnt get it to work. 

Thank you for all your help.  John

---

### Post by MAFoElffen on 2023-02-25
Most of my desktops start as Ubuntu Server... Then I install a Desktop... For just the Gnome Desktop (DE) and a graphical login (DM) such as LightDM
```

sudo apt install gnome-session lightdm

```
Then you could install whatever GUI app you wanted, without the bloat of apps you would never use...

Or go all out and install 'everything'
```

sudo apt install ubuntu-desktop gnome-session

```

---

### Post by TheFu on 2023-02-25
If you add a desktop to a server install, don't expect many of the subsystems to be change and integrated into the DE.  

The idea of a "server" using wifi just seems ... er .... wrong to me.  Putting something so bloated as Gnome onto a server is server-abuse. ;)   I could get behind loading openbox or fluxbox or fvwm for a lite-GUI experience, but Gnome?  If you want that, install the full, default, Ubuntu Desktop which includes Gnome and all the fancy integrations from the start.

Any desktop version of Linux can load any server software. The exact same kernel is used.

---

