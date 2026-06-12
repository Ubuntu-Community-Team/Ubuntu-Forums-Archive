---
title: "Nvidia Drivers on Edgy"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by Sprite1990 on 2006-12-03
Just downloaded and installed the new 6.10 32bit X86 Ubuntu.

Trying to install NVIDIA-Linux-x86-1.0-9629-pkg1.run atm.

Downloaded them onto a USB stick as my Linux machine doesnt have the net, copied the file onto Desktop then double clicked and selected "Run in Terminal". It then starts to load up but comes up with an error: Nvidia-installer must be run as root.

Please be kind, this is the first time i've meddled with Software, let alone Linux.

---

### Post by taurus on 2006-12-03
Just follow the directions from this link...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by Sprite1990 on 2006-12-03
I probably won't understand it but i'll give it a shot.

Oh joy, looks like im after "Method 2" which seems the hardest...

---

### Post by Sprite1990 on 2006-12-03
I got to the stage where I run the Nvidia driver but when it starts it now says "ERROR: you do not appear to have libc header files installed on your computer."

---

### Post by taurus on 2006-12-03
Did you forget to run this command?

```
sudo aptitude install linux-generic
```

---

### Post by Sprite1990 on 2006-12-03
Just tried that and it still didnt work (I tried that exact command "sudo aptitude install linux-generic") Do i need to be connected to the internet to get that?

Aw crap I forgot to say that I was using [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) instead of the one you listed as the one you listed said I have to get something from the internet.

It was that wget [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc) which I cant do. Can I just save the [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc) text onto a USB stick, drop it in my /home/dan folder on my Ubuntu machine then use the method of installation that you sugested ?

---

### Post by taurus on 2006-12-03
> **Sprite1990 said:**
> Just tried that and it still didnt work (I tried that exact command "sudo aptitude install linux-generic") Do i need to be connected to the internet to get that?
#-o 

If your machine is not connected to the net, how are you going to download anything?

Are you using a generic or just a 386 kernel?

```
uname -r
```

---

### Post by Sprite1990 on 2006-12-03
:( sorry :(

Well I downloaded the i386 version of Edgy, so it uses the 386 Kernel right ?

(As I said im new to this so don't know anything, but thanks a lot for your help so far :))

EDIT: Would it just be easier if i brought my machine downstairs, connected it to the internet, then follow the guide you suggested?

BTW if I wanted to connect to the internet i'd be using nForce 4 Ethernet port and a Netgear DG834G v3 Router.

---

### Post by taurus on 2006-12-03
I think you are using the generic i386 kernel if you installed it from a CD and didn't install another kernel!  That's why I need to see the output of that command from a terminal!

```
uname -r
```

---

### Post by Sprite1990 on 2006-12-03
2.6.17-10 Generic

---

### Post by taurus on 2006-12-03
Yes, connect your machine directly to the net and install whatever else you need.  That's the fastest and easiest way to go.  And by the way, you are using the generic i386 kernel, not i386.

---

### Post by Sprite1990 on 2006-12-03
Will I need drivers for my Ethernet and Router beforehand ?

BTW thanks a lot for your help, last time i tried Linux (Mandriva) I just gave up after a while, hopefully it works this time ! :D

---

### Post by taurus on 2006-12-03
What kind of ethernet do you have?  Probably don't need a driver for it...

---

### Post by Sprite1990 on 2006-12-03
Spec on Epox website says:

LAN:
1Gb Ethernet from onboard Vitesse VSCS8201 Gigabit Ethernet PHY.

---

### Post by taurus on 2006-12-03
Connect it and turn on your machine.  See if Ubuntu detects it...

---

### Post by Sprite1990 on 2006-12-03
It works ! Yay !

Anywho i'm half way through the guide you linked to and everything is working so far :D

Thanks a lot for your help !

---

### Post by taurus on 2006-12-03
Just plug 'n play, eh!

And if you want to install anything else before you move your computer upstairs and without network connection, better do it once you are done with nvidia...  ;)

---

### Post by Sprite1990 on 2006-12-03
Well i've finished installing the drivers, I know they work as I now pass the Graphics Card settings in Cedega.

However, I can't set the resolution above 1024x768 :(

Do you, by any chance, know how to fix this ?

---

### Post by taurus on 2006-12-03
You can edit your /etc/X11/xorg.conf and add in whatever resolution you want.

```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down near the end and you will see a bunch of lines with things like "1024x768".  Add in your resolution in front of those lines...  Save it and reboot and you would see a white nVidia logo!

---

