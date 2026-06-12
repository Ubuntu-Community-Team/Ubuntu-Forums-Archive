---
title: "X Server error when trying to install"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by MiThRaZoR on 2006-08-28
Here's the whole thing.

> Failed to start Xserver (your graphical inter). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
I choose yes it shows something like this:
> X Window System: Versions 7.0.0
Release date: 21 December 2005
X Protocol: Versions 11, Revision 0, Release 7...
...
....
Using config: /etc/x11/xorg.conf
Then it says,
> Would you like to view detailed X server output as well?
I choose yes and then it shows the same thing from before.
> X Window System: Versions 7.0.0
Release date: 21 December 2005
X Protocol: Versions 11, Revision 0, Release 7...
...
....
Using config: /etc/x11/xorg.conf
Then it says
> X Server is now disabled. Restart GDM when it is configured correctly.

Now what I'm thinking is that this has to do with my nVidia graphics card. If I switch to my Integrated Intel, would that work? Then I could use the sticky and upgrade it and then switch back to my nVidia.

Can I do that? Or is my problem something else instead of a graphics card?

Any help is appreciated. In one of the stickies, it says the problem is in 10.3 but int 10.4, it's fixed. Or something like that. I don't know what that's supposed to mean, but I'm just wondering, has there been a fix?

And today, I just downloaded the ISO from the Ubuntu website and tried to install Ubuntu with that CD. But I had the same problem.

I'm not a technical person so plain English please. ;)

---

### Post by Omnios on 2006-08-28
Hi if the error message is no screens found I believe it is a monitor issue. My old set up had a crappy monitor that had a similar problem. 

 Anyways there are a few tricks to try. Try the versa driver wich is supposidly a standard VGA driver type.  I fixed my problem by installing nvidia -glx and running the config changing from the nv driver to the nividia driver.

 If you have network out of the box you can install nvidia-glx from the command line though using the versa probably will allow you to load xserver and insall from there.

 Anyways the config file is /etc/X11/xorg.conf
also you can use
```
sudo dpkg-reconfigure xserver-xorg
```
 sudo dpkg-reconfigure xserver-xorg which like a turtle craphics type xorg config program.

---

### Post by MiThRaZoR on 2006-08-29
Okay, done that. Now when I finish the stuff for the reconfiguring thing, it just expects another command after that. I don't know what command to put in next.

---

### Post by Omnios on 2006-08-29
Well if you reboot it should try to start xserver but if it does not either startx or was it sudo startx, its been a while

---

### Post by MiThRaZoR on 2006-08-31
Tried that, it says Flex IO error number 104 or something like that. And that it can't start.

It said to go on wiki.x.org for help. So that might help.

I also did the Sudo apt-get update and sudo apt-get install xserver-xorg-core but that didn't help. I got the same error.

---

### Post by MiThRaZoR on 2006-09-01
Bump.

---

### Post by MiThRaZoR on 2006-09-02
Last bump.

---

### Post by MiThRaZoR on 2006-09-02
Actually, I'm planning to do it another way.

I'm going to install Breezy Badger then upgrade it from there. Do you think it will work without all the problems I'm getting now?

---

