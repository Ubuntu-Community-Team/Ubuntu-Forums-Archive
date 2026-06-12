---
title: "Installing a minimalist Ubuntu..."
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Raindance on 2011-02-15
Hey all,

So, I've been playing around with various distributions including Arch Linux, openSuse, and Ubuntu with it's derivatives. So far, I feel that Ubuntu flows the best out of them all, offering the best mix of user-friendliness, eye-candy, and performance.

HOWEVER, I really like doing things from the ground up and like having complete control over what I am using/spending resources on. OpenSuse was very attractive to me because of it's [URL="http://www.susestudio.com/"]Suse Studio/URL] which allows you to start with a basic system and add, manually, each and every package you want so you get exactly what you want. 

Does Ubuntu offer any system like this? Or, alternately, is there a "barebone" download in which you get basically a command line with networking and can apt-get all of the packages you want?

I appreciate your time!
-Raindance

---

### Post by PaulReaver on 2011-02-15
yep there's the mini.iso  that's the net install disc... (i do this one) :)


and there is also the alternate.iso 
if you press f6 when the menu comes up you can install a minimal system

you'll find them on the ubuntu release page
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

hope it helps

---

### Post by snowpine on 2011-02-15
Here is a good guide to building a custom Ubuntu system from the ground up using the minimal install CD:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Raindance on 2011-02-15
Hey thanks for the quick replies!

If I go with the minimal install, I will still be able to install, say, XFCE or Gnome if I choose, correct? 

I am note really worried about my hardware, just mostly I want to control the packages I have installed. I will probably use Gnome(maybe KDE or XFCE haven't decided), so this is not an issue. 

If I chose Gnome over IceWM, are there any commands I'd need to change? For instance, I assume it's something like this at command line;
> sudo apt-get gnome-desktop
startx

Would "startx" start up Gnome or KDE just like the other?

Thanks!

---

### Post by snowpine on 2011-02-15
The correct syntax is:

```
sudo apt-get install nameofpackage
```

You can install either gnome-core or gnome-desktop-environment. Check out these links to see the difference of what's included:

[http://packages.ubuntu.com/maverick/gnome-core](http://packages.ubuntu.com/maverick/gnome-core)
[http://packages.ubuntu.com/maverick/gnome-desktop-environment](http://packages.ubuntu.com/maverick/gnome-desktop-environment)

ps: 'startx' will start whatever desktop environment is installed, so yes, it will work with Gnome. :)

---

### Post by PaulReaver on 2011-02-15
> **Raindance said:**
> Hey thanks for the quick replies!

If I go with the minimal install, I will still be able to install, say, XFCE or Gnome if I choose, correct?    

Yep :)   as long as you can set up internet access from the command line...

> **Raindance said:**
> 
If I chose Gnome over IceWM, are there any commands I'd need to change? For instance, I assume it's something like this at command line;

Would "startx" start up Gnome or KDE just like the other?


you'll defo need to install xinit.... for startx

you could install a login manager like gdm kdm or xdm
I'm sure there are others on the forums that'll know in more detail.

---

### Post by Raindance on 2011-02-15
Awesome thanks for the help! One more question; would JeOS Ubuntu be a decent starting point? I'm having a hard time getting my laptop to connect to our network manually...think I'm going to need more than the tiny one given!

Thanks!

---

### Post by snowpine on 2011-02-15
I do not think JeOS is necessary for the typical user. See the link in post #3 for more details on my suggestion, the Ubuntu mini.iso. As the tutorial mentions, you'll need a wired internet connection with a supported Ethernet card. :)

---

### Post by Raindance on 2011-02-15
Very cool, thanks for the help everyone. I wired in to my connection and got everything turning nicely. 

Appreciate the time, look forward to hanging around!

---

### Post by mörgæs on 2011-02-15
Though you have the system running already, maybe these will be interesting to you:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

