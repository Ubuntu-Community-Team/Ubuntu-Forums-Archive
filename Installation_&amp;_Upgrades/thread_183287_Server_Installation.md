---
title: "Server Installation"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by larry on 2006-05-27
Hi,
I am trying to understand better how Ubuntu (and Linux in general) works.
That is why, instead of following the standard installation of (K)ubuntu on my laptop, I went for a server installation having then the idea of setting up a simple desktop with openbox and a few selected apps.
Well, the server installation is fine, but now I am finding out that I have no idea of how to set up some graphical environment and what I should install to see something resembling a desktop (let alone installing Gnome/KDE) and so on.
Before now, I was running Ubuntu Dapper and Openbox as an alternative to Gnome.
Any suggestions about what to do? Is there a tutorial with some quick rules to follow?
I would like to get to the bottom of this and I cannot leave my laptop as it is (with little more than the command line) for a long time.
Cheers

Larry

---

### Post by aysiu on 2006-05-27
Log in and type: ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm openbox menu firefox synaptic
sudo /etc/init.d/gdm start
```

---

### Post by Sutekh on 2006-05-27
Openbox? Great choice!

This is a great little Window Manager, especially on its own.  

The only extra thing I'd add to aysiu's commands, is obconf (the Openbox config)
```

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm openbox **obconf **menu firefox synaptic
sudo /etc/init.d/gdm start
``` 
These are some helpful links for installing/configuring

[Openbox Web Page]("http://www.icculus.org/openbox/")

[Ubuntu Wiki - Openbox]("https://wiki.ubuntu.com/Openbox")

 This link is for Breezy, but works fine for Dapper.

[Ubuntu Forums - How to use Openbox in GNOME and by itself.]("http://www.ubuntuforums.org/showthread.php?t=75471")

This last link is for the Openbox menu editor, which is very useful.

[Openbox Menu Editor]("http://sourceforge.net/projects/obmenu")

---

### Post by larry on 2006-05-28
[QUOTE=Sutekh]Openbox? Great choice!

This is a great little Window Manager, especially on its own.  

The only extra thing I'd add to aysiu's commands, is obconf (the Openbox config)
```

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm openbox **obconf **menu firefox synaptic
sudo /etc/init.d/gdm start
``` 
These are some helpful links for installing/configuring

[Openbox Web Page]("http://www.icculus.org/openbox/")

[Ubuntu Wiki - Openbox]("https://wiki.ubuntu.com/Openbox")

 This link is for Breezy, but works fine for Dapper.

[Ubuntu Forums - How to use Openbox in GNOME and by itself.]("http://www.ubuntuforums.org/showthread.php?t=75471")

This last link is for the Openbox menu editor, which is very useful.

[Openbox Menu Editor]("http://sourceforge.net/projects/obmenu")[/QUOTE]


Alright, I am almost done. Unfortunately, the procedure above does not create the .xsession file in the home directory, so when I choose to log in using the default session, I end up with a system which does not even own a window manager!
Any idea why this is happening? Is the .xsession file for openbox stored somewhere else in the system or do I have to invent one?
Many thanks...a bit of extra effort and I'll be there!

Larry

---

### Post by larry on 2006-05-28
Alright, it was my mistake (I should have enabled some extra repo).
Three questions:
1) any difference if I use kdm rather than gdm for a system based on openbox?
2)adding a panel, in the past, made my system much slower (gnome-panel was bad, but even pypanel, which was very basic, made things slower)
3) I thought I should havev the menu.xml and rc.xml somewhere in my home directory under  ./config/bla bla but this is not the case.
Should I create them?
I would like to configure them by hand.

Many thanks

Larry

---

### Post by Sutekh on 2006-05-28
[quote=larry] 1) any difference if I use kdm rather than gdm for a system based on openbox?[/quote]KDM might work different to GDM in terms of looking for the default .xsession file.
[quote=larry]2)adding a panel, in the past, made my system much slower (gnome-panel was bad, but even pypanel, which was very basic, made things slower)[/quote]
Try fbpanel (universe repository) for a light panel
[quote=larry]3) I thought I should havev the menu.xml and rc.xml somewhere in my home directory under ./config/bla bla but this is not the case.
Should I create them?
I would like to configure them by hand.[/quote]
Copy them from the system ones, they should be in **/etc/xdg/openbox/ or ****/usr/local/etc/xdg/openbox**. You want to copy them to [B]$HOME/.config/openbox/

[/B]All this is in this link

[http://www.icculus.org/openbox/docs.php](http://www.icculus.org/openbox/docs.php)

---

### Post by larry on 2006-05-28
Hi,
Well, I think I am almost done. My system looks lean, the boot time is less than one minute from pressing the power button to having Openbox up and running.
I have only a problem now: the hotplug is not working.
I did not have this problem in the past (but then I had first installed gnome and then openbox).
In my .xsession file I have the line:

gnome-volume-manager

Any CD/DVD which I introduce in the laptop is recognized automatically, but the same does not happen with my usb memory stick.
I did everything as you suggested in your posts, so you should have a rough idea of what my system looks like.
Maybe it is trivial to have the hotplug enabled, but I have never done it before (never needed to do it by hand).
Any suggestion here is welcome!
Many thanks

Larry

---

### Post by larry on 2006-05-28
I did not have gnome volume manager set up correctly...now everything seems fine.
Many thanks to all the people on the forum who patiently educated me!
Ubuntu's community is really nice!
Cheers

Larry

---

### Post by Sutekh on 2006-05-28
Good on you.  Openbox is supremely fast (hardware dependant of course), especially with Dapper.  It used to take me less than 20s to boot into Openbox.

---

### Post by larry on 2006-05-29
[QUOTE=Sutekh]Good on you.  Openbox is supremely fast (hardware dependant of course), especially with Dapper.  It used to take me less than 20s to boot into Openbox.[/QUOTE]

I did notice an improvement in the overall performance of my box!
OpenBox is safe and sound and will probably stay there for a long time.
Two quick questions: how do I modify the content of the Debian menu?
And then: I installed and then removed ark, but when I use natilus --no-desktop to browse through my folders, if I right click on a folder I am still shown the option "open with ark".
These are small glitches, yet I would like to know if they can be ironed out.
Cheers

Larry

---

### Post by Sutekh on 2006-05-29
I was under the impression that the Debian menu was populated with just about everything and can't be edited.  I'll check on that though.

Ohh the nautilus thing.  If you right-click a folder and choose Properties and the the Open With tab, can you remove Ark?

---

### Post by Sutekh on 2006-05-29
You can use this guide to help you configure the Debian menu (just one of many copies I found)

[http://linux-cd.com.ar/manuales/debian-menu/index.html#contents](http://linux-cd.com.ar/manuales/debian-menu/index.html#contents)

Looks like some reading though...

---

### Post by larry on 2006-05-30
[QUOTE=Sutekh]You can use this guide to help you configure the Debian menu (just one of many copies I found)

[http://linux-cd.com.ar/manuales/debian-menu/index.html#contents](http://linux-cd.com.ar/manuales/debian-menu/index.html#contents)

Looks like some reading though...[/QUOTE]


Many thanks. It is actually a long reading the one to get on top of Debian menu (I thought it would be much simpler).
As to Nautilus, unfortunately it is not that easy.
BTW, you seem to know a lot about OpenBox and your suggestion about fbpanel was well worth trying, so could you please tell me if you use Nautilus or some other tool to browse through your desktop?
Cheers

Larry

---

### Post by Sutekh on 2006-05-30
[quote=larry] Many thanks. It is actually a long reading the one to get on top of Debian menu (I thought it would be much simpler).[/quote]Yeah I was surprised at the level that was required to edit it.

I think fbpanel is great, has it been working faster for you?

I used Openbox pretty extensively for a while, in the end I succummed to eye candy and am know using XFCE, but I highly rate Openbox.

I tried to keep everything as minimal as possible and tried to hold out against using a file manager, mostly using the command line for browsing.   

I did try some, if you really want one I found Thunar and Rox-Filer to work quite well.  Thunar is probably the easiest to get used to, but I don't know of any .debs for Breezy only Dapper.  Rox can take some getting used to.  

I didn't use either to browse my desktop either, I kept it completely empty.

---

### Post by larry on 2006-06-01
[QUOTE=Sutekh]Yeah I was surprised at the level that was required to edit it.

I think fbpanel is great, has it been working faster for you?

I used Openbox pretty extensively for a while, in the end I succummed to eye candy and am know using XFCE, but I highly rate Openbox.

I tried to keep everything as minimal as possible and tried to hold out against using a file manager, mostly using the command line for browsing.   

I did try some, if you really want one I found Thunar and Rox-Filer to work quite well.  Thunar is probably the easiest to get used to, but I don't know of any .debs for Breezy only Dapper.  Rox can take some getting used to.  

I didn't use either to browse my desktop either, I kept it completely empty.[/QUOTE]


I see. As a little surprise, I can tell you that Thunar is available in the Ubuntu repositories (it is described as XFCE standard file manager).
It is pretty fast!
I will be given a laptop for my job in some weeks' time, so I may give Xubuntu a try.
One question: I know it comes with its own set of apps, but do KDE & Gnome apps really blend well with Xubuntu as it claims?
**************************************************
Back to the forum, 99% is fine on my box, but if I try to include

gnome-settings-daemon

in the .xsession file, then I break my system (the mouse is not recognized, I lose the background and I have to switch off my laptop by hand). How comes? Synaptic tells me that gnome-settings is installed correctly.
Cheers

larry

---

