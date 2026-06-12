---
title: "Xorg problem after upgrade to feisty"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by mjj on 2007-03-26
I have an AMD64 box with an ATI 1600 video card which as been running fine on edgy for a number of months with the fglrx driver. I decided to upgrade it to feisty once the beta came out. However, it's killed my X :-(


I don't use gnome or KDE but just fvwm and upgraded via apt-get dist-upgrade. Whenever, I start X as a user, every keypress acts as if it were Ctrl-Alt-+ (ie changes to the next screen resolution). Then if I kill the X server, I get lots of error messages regarding MPOL_???? (I'm not in front of it at the moment) then various processes get killed. Typing anything after returning to console takes a while to respond then after a minute or so, all goes back to normal on the console.

The weird thing I noticed is that if I copy the fvwm config and .xinitrc to /root and start X from there all is fine. Also, removing all but the start of an xterm when starting X still fails as the user.

Any ideas ?

Thanks,
Matt.

---

### Post by melissawm on 2007-03-27
Have you tried logging in to the recovery mode and typing, as root:
```

dpkg-reconfigure xserver-xorg

```? It will guide you through the configuration of the X server. It usually works.. try this an then still from the recovery mode 
 ```

startx
 
```If it works, try logging in to normal mode...

---

### Post by mjj on 2007-03-27
Thanks. Forgot to mention I'd try that. Tried again with no luck. Seem to have got rid of the memory errors somewhere along the line.

I'm guessing permissions problems somewhere since it works as root but on what ? No errors showing up in the log.

---

### Post by melissawm on 2007-03-27
I'd try looking for a .xfce directory or something like that in your home directory and removing it (or renaming it for backup). Then restart the x. Maybe that's why it works from another user's home. Just a thought, I'm no expert :P

---

### Post by mjj on 2007-03-28
No .xfce at all but your assistance is appreciated.

Having discovered that things were working as root was a big help. I kept looking for what might not readable/writable to the user but couldn't find anything obvious. 

When trying things, I managed to make the root one just produce a blank screen. I ssh'd in from another machine to and discovered that there was some xkbcomp process running. Never found where that was started from but it lead me to some forum posts about blank screens. Some how or other I decided to check the environment and realised that I had a variable XKEYSYMDB set on my user account. That was pointing to a non-existent file. Removed the variable and no more problem :-)

---

