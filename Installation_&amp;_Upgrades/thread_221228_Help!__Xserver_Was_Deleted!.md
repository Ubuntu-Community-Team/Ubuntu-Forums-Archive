---
title: "Help!  Xserver Was Deleted!"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by cyphrix on 2006-07-22
Ok, so I'm stupid and deleted xserver-xorg.  I'm on a black screen, completely commandline.
I tried sudo dpkg-reconfigure xserver-xorg but it didn't work

How do I get xserver installed?!?!?!?  Please help, I have tons of data that I cannot afford to lose!

---

### Post by aysiu on 2006-07-22
In this order: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by cyphrix on 2006-07-22
Ok, I somehow deleted xserver.  I cannot get to my GUI login, all it gives me is an error stating that XSERVER cannot be loaded and it drops me to a
root@josh-desktop.

I tried to dpkg-reconfigure xserver-xorg, went through the processes but it still doesn't work.  I tried recovery mode and it says:

'Package 'xserver-org' is not installed and no info is available. 

Someone please help.  I have tons of data that I cannot afford to lose.

---

### Post by Ziox on 2006-07-22
you can try to reinstall xserver-xorg:
sudo aptitude install xserver-xorg

---

### Post by Ben Armston on 2006-07-22
Have you tried ```
sudo apt-get install xserver-xorg
``` ;)

---

### Post by cyphrix on 2006-07-22
I tried everything listed above...looked like it was about to work and then I got the same error when I tried to start.

I have a window now that says:

GDM:  Xserver not found: /usr/bin/Xgl :1 :1 -fullscreen -ac -accel
glx:pbuffer -accel xv:pbuffer -auth /var/lib/gdm/:1.Xauth -nolisten
tcp vt7
Error:  Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.

Any ideas

Thanks guys/gals for all of your help!!!!!!

---

### Post by cyphrix on 2006-07-22
I tried everything listed above...looked like it was about to work and then I got the same error when I tried to start.

I have a window now that says:

GDM: Xserver not found: /usr/bin/Xgl :1 :1 -fullscreen -ac -accel
glxbuffer -accel xvbuffer -auth /var/lib/gdm/:1.Xauth -nolisten
tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.

Any ideas

Thanks guys/gals for all of your help!!!!!!

---

### Post by aysiu on 2006-07-22
Xgl is way out of my league. ```
sudo aptitude remove xgl
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
``` maybe...

---

### Post by Ziox on 2006-07-22
i've got an idea, can you open up /etc/X11/xorg.conf and paste it here?

---

### Post by taurus on 2006-07-22
By the way, how come you post the same thread in two different places?  Aysiu is trying to help you here, [http://www.ubuntuforums.org/showthread.php?t=221228](http://www.ubuntuforums.org/showthread.php?t=221228)...

---

### Post by cyphrix on 2006-07-22
tell me the command and I'll open it.  sorry, kinda new to this.

should I have an internet connection while trying to download and install xserver when using apt?

---

### Post by taurus on 2006-07-22
```

more /etc/X11/xorg.conf

```

---

### Post by cyphrix on 2006-07-22
I have a wireless connection... rausb0

I don't know how to connect to the internet with it via this command line interface though.  If I do need that internet connection, just tell me how to connect and I'm sure it will work using apt.

---

### Post by Ziox on 2006-07-22
gksu gedit /etc/X11/xorg.conf

and yes

---

### Post by Buffalo Soldier on 2006-07-22
Threads merged.

---

### Post by Ben Armston on 2006-07-22
You do need an internet connection. To check that you currently have one type

```
ping -c3 www.google.com
```

On the last but one line, make sure that you have received at least one packet. If you haven't, we need to get that working before we can try to reinstall X.

To get the contents of /etc/X11/xorg.conf type 

```
cat /etc/X11/xorg.conf 
```

Ben.

---

### Post by cyphrix on 2006-07-22
ok, so I opened up the x11.conf file but it is HUGE!  It would take me forever to write the contents to this file.  Which section specifically did you want me to post?

If you guys could get me connected to the internet wirelessly I could try installing Xserver again and I'm sure it will work.

Only problem is, this is a desktop and my router and modem are both upstairs.  If I have to drag it up there, I will, but I'll save that for last.

Thanks again guys!

---

### Post by Ben Armston on 2006-07-22
What output did you get from ```
ping -c3 www.google.com
```

Ben.

---

### Post by cyphrix on 2006-07-22
received nothing back.  

I don't have it set up yet to where my wireless connects on start up.  I have to run wireless assistant to get connected.

---

### Post by Ben Armston on 2006-07-22
In that case we have come to the end of the help I can give you :( I don't have wireless network, so I can't test the commands on my own machine first. But when someone comes along who does know more they will need to know some more info. So could you provide the output of ```
iwconfig
``` This will give you the name of your wireless card something like ath0 perhaps. Then run ```
iwlist ath0 scanning
```
chaning ath0 to the interface given in the output of the previous command.

Ben.

---

### Post by Ben Armston on 2006-07-22
The last command needs to be run as root so change

```
iwlist ath0 scanning
``` to

```
sudo iwlist ath0 scanning
```

Ben.

---

