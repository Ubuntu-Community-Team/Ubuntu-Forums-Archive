---
title: "Im thinking of installing for the 1st time on..."
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by SF100 on 2006-12-20
Someone gave me a Dell Dimension 4500 and I am thinking of attempting my first install of Ubuntu outside of a few VM installs which were pretty problem free. Im going to make this a 100% Linux box, not a dual boot. 

Also I really dont want to have a perm monitor for it but would rather remote in with one of my windows machines after I finish the install. Is there software for Linux that allows remote access from a windows machine. 

What I would like to make this PC when Im done is a file server for my home network, for Movies, Mp3s, and other misc stuff. What advice can anyone offer. Does anyone know if Dell has Linux drivers or is there a place where I may be able to find any drivers I may need.

I am basically looking for any and all advice I can get on this. I'm a complete noob with Linux am a bit intimidated.

---

### Post by pay on 2006-12-20
I think you can use samba for remote access. Also look at VNC

---

### Post by SF100 on 2006-12-22
> **pay said:**
> I think you can use samba for remote access. Also look at VNC

Thanks where can I find VNC?

---

### Post by stalker145 on 2006-12-22
> **SF100 said:**
> Thanks where can I find VNC?

As for your Ubuntu box, VNC is built in to the system. Click to Preferences > Remote Desktop and Choose to "Allow other users to view your desktop" and "Allow other users to control your desktop". Make sure that you uncheck the box labeled "Ask you for confirmation" or you'll be sitting there all day waiting for your server to magically click.](*,) 

As for VNC for Windows, you should be able to find it either at one of the free download sites (i.e. Tucows, CNet) or Google for it. 

Good luck, and check back if you need more help.

---

### Post by SF100 on 2006-12-22
> **stalker145 said:**
> As for your Ubuntu box, VNC is built in to the system. Click to Preferences > Remote Desktop and Choose to "Allow other users to view your desktop" and "Allow other users to control your desktop". Make sure that you uncheck the box labeled "Ask you for confirmation" or you'll be sitting there all day waiting for your server to magically click.](*,) 

As for VNC for Windows, you should be able to find it either at one of the free download sites (i.e. Tucows, CNet) or Google for it. 

Good luck, and check back if you need more help.

Thanks!! 

I just dont want another monitor, well actually my wife said she will murder me if I clutter the area with another one. 

So VNC will act like a PCAnywhere type program and allow me to see the desktop and remotely access the ubuntu box Im setting up? 

I have to say the Ubuntu community is amazing to me, a very helpful bunch :)

---

### Post by stalker145 on 2006-12-22
> **SF100 said:**
> So VNC will act like a PCAnywhere type program and allow me to see the desktop and remotely access the ubuntu box Im setting up? 

Well... yes...

For me, VNC works well over my LAN. I would not, personally, open it up to the outside due to security issues. While it is *possible*, what I have read says that it is not *Advised*.

If you choose to open your computer to the outside, you will simply have to port forward your router on ports 5900 and 5901 (I believe) and have some way to get to your router's IP (DynDNS, straight IP, etc). Be careful in doing this if you go that route.

Personally, if I want to access my server from the outside, I use **[WebMin]("http://www.webmin.com")**. It's a nifty frontend for all your server applications (Samba, Apache, E-mail, Jabber, yadda yadda) and you can even do updates, upgrades, software installs, and browse your file system through it. It's a great tool for someone, like me, who doesn't care to do everything from the command line. Of course, sometimes you have to ;)

---

### Post by SF100 on 2006-12-22
> **stalker145 said:**
> Well... yes...

For me, VNC works well over my LAN. I would not, personally, open it up to the outside due to security issues. While it is *possible*, what I have read says that it is not *Advised*.

If you choose to open your computer to the outside, you will simply have to port forward your router on ports 5900 and 5901 (I believe) and have some way to get to your router's IP (DynDNS, straight IP, etc). Be careful in doing this if you go that route.

Personally, if I want to access my server from the outside, I use **[WebMin]("http://www.webmin.com")**. It's a nifty frontend for all your server applications (Samba, Apache, E-mail, Jabber, yadda yadda) and you can even do updates, upgrades, software installs, and browse your file system through it. It's a great tool for someone, like me, who doesn't care to do everything from the command line. Of course, sometimes you have to ;)

Actually I want this box to have restricted access to the outside other than for some basics web browsing, usenet, and updates and would want to 100% block any remote administration from outside the lan. I will probably be asking how to do that in a later post. I just dont want to have a monitor and where the box is having it share isnt an option.

Im just getting done with the install and realized I have no cable long enough to get it on the lan. Im also having some issues with drivers for the Rage 128 video card but with no lan access Im dead in the water until I get connected.

Thanks again for responding:D

---

### Post by SF100 on 2006-12-22
Got the VNC working using TightVNC. Thanks to those who took the time out to help.

---

