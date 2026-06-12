---
title: "Upgrade from 6.10 to 8.04 failed, can't log in now"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by JettRink on 2008-07-12
I just finished the 6.10 dapper to 8.04 hardy using synaptic upgrade tool.

The upgrade seemed to go fine until the first reboot.

Now I can't login. 
The login page is corrupted and there is no text box to enter my user name.

Anybody have any suggestions on how to fix this without a reinstall ???

---

### Post by oilchangeguy on 2008-07-12
> **JettRink said:**
> I just finished the 6.10 dapper to 8.04 hardy using synaptic upgrade tool.

The upgrade seemed to go fine until the first reboot.

Now I can't login. 
The login page is corrupted and there is no text box to enter my user name.

Anybody have any suggestions on how to fix this without a reinstall ???

first, i hope you backed up any data before you attempted the upgrade. second what are your computers specs? it might not be able to run 8.04. and dapper is 6.06, not 6.10.

---

### Post by JettRink on 2008-07-12
yes, it's release 6.06

I have an AMD Athalon 1000 mhz with 512k memory

---

### Post by steve8track on 2008-07-12
Are you sure the user name box isn't there?  Maybe the resolution is wrong and it is just off of screen.  You could try editing your /etc/X11/xorg.conf for different resolutions, and try:

```
sudo dpkg-reconfigure xserver-xorg 
```

You can get to a vertual terminal by using Ctrl+Alt+ some number 1 through 6 usually.  To get back to the graphical user interface, use Ctrl+Alt+7 or sometimes a larger number.

It should help you to set screen resolutions, as well as fix other problems with the video settings.  Try a generic video driver for more reliability at first (like vesa) and later use drivers more specific to your card.

Also, if the resolution is just wrong, you could try typing your name and password on the screen (blindly) and see if it logs in.  If it does, you can experiment with different screen resolutions to see which one works well by using gvidm in the command line (while logged in).  The syntax is:

```
gvidm 640x480@60
```

Where the first number is the width, the second is the height, and the last number is the Hz.

Also, if used by itself (just type "gvidm") a menu will appear by your mouse that lets you select available options.

You may also be able to try this without logging in graphically, although I haven't tried it.  When in a virtual console, you can send commands to the xserver using syntax like this:

```
gvidm 640x480@60 -- :1
```

The "-- :1" sends the resulting command to screen 1.  You may have to try other numbers, like 2 or 3.

I hope this helps.  Let me know if it works.  Good luck.

Steve

---

### Post by steve8track on 2008-07-12
I tried out the "-- :1" idea just now, and it didn't work for me.  Sorry :-(  Oddly I made my login screen blank white when switching back to Screen 1.  I had to do just as I suggested to you and just type my name and password without being able to see what I was doing.

System->Administration->Login Window can help you possible fix it after you are logged in.

Good luck again,

Steve

---

