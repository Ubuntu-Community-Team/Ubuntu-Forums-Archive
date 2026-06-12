---
title: "problems with icewm - no windows, only titlebars"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by subatomic on 2005-07-13
I have a pentium 266 with 32 meg of ram...   as such I wanted a very small lean install using icewm and xdm.   I started with the Ubuntu (hoary) installer (with "**server**" option at boot: ).  This is probably a known bug (i hope), but the installer fails when detecting network devices and then crashes.   I was able to get around this and finally install after I created a swap partition, then rerun the install, then during the install process switch to another virtual terminal to run a command to enable the swap partition (mkswap and swapon).  from there, everything baseline installed just fine.

then... the **problems** began!   I wanted to install a window manager (icewm to be specific).  so I did this:

```
# apt-get update
# apt-get install icewm
# apt-get install xserver-xfree86
# apt-get install x-window-system-core
# apt-get install xdm
# apt-get install numlockx
# apt-get install xterm
```

after rebooting, xdm starts and I log in, icewm runs and looks good.

but it's _not good_!  when I run xterm (or any application, including "logout"!), the titlebar appears but the window portion is missing!.  It's just a decapitated head (erm... titlebar) floating in space.   If I right click on the titlebar and choose [FONT=Courier New]fullscreen[/FONT],  THEN I see the window (but it's ferkin' fullscreen, not cool, right?).   Playing with the [FONT=Courier New]shade[/FONT] and [FONT=Courier New]resize[/FONT] menu options do not make the window appear.   ](*,)     Changing to other themes doesn't help, in fact some themes also make titlebar disappear (so that no part of the window appears on the desktop, except for in the task bar).

**Does anyone understand what is going on?   **  running [FONT=Courier New]top[/FONT], I do see [FONT=Courier New]Xorg[/FONT] in the process list running as root.  I'm also using [FONT=Courier New]xdm[/FONT], but I did try with [FONT=Courier New]gdm[/FONT] and got the same problem...


thanks for any help.

---

### Post by subatomic on 2005-07-14
I just did a complete reinstall using the following:

```
#  Do a server install of Ubuntu 5.04.
# edit /etc/apt adding Universe and removing CD repositories.
# apt-get update; apt-get upgrade
# apt-get install xserver-xorg mdetect xresprobe xxkb gdm icewm
# apt-get install x-window-system-core xfonts-scalable xfonts-100dpi xfonts-75dpi
# apt-get install synaptic mozilla-firefox ubuntu-artwork xterm xtermcontrol
```

after which (without rebotting) I typed startx, and it launched immediately into icewm...    SAME THING!   running any app starts ONLY ....  a titlebar!!   :mad:   the window portion of the window does not show.

WTF!

I have plenty of memory left (195 swap and 1 meg ram)


By the way, I just tried [FONT=Courier New]twm[/FONT], and that window manager works, I can start any app, and the window portion of the app shows...    I'd rather use icewm though!

---

### Post by t2kburl on 2005-07-14
not sure if this will help you, but I have it working on a similar machine

I also installed icewm-common, icewm-gnome, icewm-gnome-support and icewm-themes

I stuck with gdm (tried xdm but had issues with it --- sorry, can't recall what exactly, but I think I couldn't even log in)

I was able to change the gdm settings within icewm to diable the graphical login screen

---

### Post by subatomic on 2005-07-15
[QUOTE=t2kburl]not sure if this will help you, but I have it working on a similar machine
I also installed icewm-common, icewm-gnome, icewm-gnome-support and icewm-themes
I stuck with gdm (tried xdm but had issues with it --- sorry, can't recall what exactly, but I think I couldn't even log in)
I was able to change the gdm settings within icewm to diable the graphical login screen[/QUOTE]

[FONT=Courier New]xdm[/FONT] just works for me using the above sequence of apt-get's...   I can login.   [FONT=Courier New]xdm[/FONT] is so much smaller which is why I chose it.  Make sure your resolutions are set up right.  I had 1024x768 in there and my crappy monitor didn't support it so I got a blank screen the first time I tried this...

So I tried your install, but it didn't work again...Here's what I did:
I installed 
```
# apt-get install icewm-common icewm-gnome icewm-gnome-support icewm-themes
```

and at the end it said it was changing my window manager to [FONT=Courier New]icewm-gnome[/FONT].    
I ran [FONT=Courier New]startx[/FONT], and same thing, only a title bar floating.  I switched window managers from [FONT=Courier New]icewm[/FONT] to [FONT=Courier New]icewm-gnome[/FONT], same thing.

I also noticed that when I switch themes inbetween the teardown of the previous theme and setup of the next theme, 
I do see my xterm window for a brief moment.   but then the next theme starts and the xterm window goes away -  replaced by a floating titlebar.

it seems like my window is there, but [FONT=Courier New]icewm[/FONT] is supressing it somehow.  **any ideas?**

---

### Post by t2kburl on 2005-07-15
I booted up my box after reading this and it doesn't work properly, either
I do get the full windows in IceWM, though, but it takes FOREVER. I noticed that when Ice is running almost anything I do (including just moving the mouse around) and the CPU usage shoots up to 100% for a minute or more.
Not what I call a usable system. Took me over an hour to set up synaptic to do a few package installs, then it froze up completely as soon as it started downloading.
I'm thinking we probably need to run
```
sudo dpkg-reconfigure xserver-xorg
``` 
and figure out some lighter settings
I'll let you know what I come up with

btw the machine I'm using is a pentium 133 with 64 megs of ram and a 512 swap space

---

### Post by t2kburl on 2005-07-15
well .... I just tried re-installing with no luck  it just hangs at a blue screen ... shortly after "trying to enable frame buffer"

on the bright side, there is a nice new version of DSL out ...  I'll give that a try

---

### Post by subatomic on 2005-07-19
[QUOTE=t2kburl]well .... I just tried re-installing with no luck  it just hangs at a blue screen ... shortly after "trying to enable frame buffer"
[/QUOTE]


weird, I don't have any problems installing, assuming I setup my swap partition on another virtual terminal while the installer is running.

are you doing the [FONT=Courier New]server[/FONT] install?

---

