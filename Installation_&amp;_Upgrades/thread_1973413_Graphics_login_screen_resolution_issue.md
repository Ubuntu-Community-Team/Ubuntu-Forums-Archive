---
title: "Graphics login screen resolution issue"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by Mylorharbour on 2012-05-04
Following a troublesome 12.04 installation from a LiveCD I had graphics issues at the login screen and at the desktop.

I resolved the workspace issue by bringing up the dash and typing Displays. The resolution was set correctly but the characters weren't very sharp so I set it to a lower resolution then back again so that's now fine.

I rebooted to make sure it remembered the setting but the login screen is still oversized. I can just see the right hand side of the login box. Logging in resulted in a proper workspace so it's usable but needs refinement.

My display is 1680 x 1050. For what it's worth my grub file in etc/default reads:

[INDENT]# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480[/INDENT]

Anyone know how to adjust the login screen resolution?

---

### Post by Mylorharbour on 2012-05-07
Sorry guys, I've had to bump this. 
Does anyone know where the login screen resolution is set?

---

### Post by Mylorharbour on 2012-06-26
Apparently I'm not alone as others also have this issue. It appears I need to change the LightDM screen resolution to match my desktop (1680 x 1050). Any ideas?

Just a thought....if Ubuntu is failing to detect my monitor at start-up could this be due, in some way, to the ATEN KVM I'm using?

---

### Post by D3lta4rce on 2012-08-19
[http://gangmax.me/blog/2012/06/20/ubuntu-12-dot-04-login-screen-resolution-problem/](http://gangmax.me/blog/2012/06/20/ubuntu-12-dot-04-login-screen-resolution-problem/)

This site has the tip on setting the LightDM resolution, which sets the login screen resolution. 

However a word of warning, I tried it and stopped my Login screen from starting at all,  even though all the settings I used in the LightDM configuration file was correct for the  screen.  It appears there may be something not mentioned in the tip which probably needed doing in my case. 

To get back to a working system, I had to use a live cd and boot into that so I could get a working desktop running so I could go back on-line and find the tip pages again and follow the instructions again but this time reset everything back.

My login screen started intermittently dropping into an unsuitable resolution for my screen after I upgraded from 11.10 to 12.04, I did find a restart would sometimes bring the login screen back to the correct resolution for my screen, but over time this stopped working and the resolution of the login screen stayed stuck at this unsuitable setting.
I then tried a fresh reinstall of 12.04 just in case the upgrade from 11.10 was the problem, I also could not find any useful information on changing the login screen resolution, but this fresh install hasn't helped either as I'm now stuck with a system where the login screen is off the left and right sides of the screen to the extent the login box isn't visible so I can't select users or desktop modes.

Some people on these forums seem to be under the impression the grub resolution settings are the ones that we are after changing, but others say grub resolution doesn't change the login screen resolution.  That's down to LightDm configuration.

It would have been good to have a GUI utility that can change the login screen resolution as I'm not after reprogramming Ubuntu just to get the login screen working for me.

Anyone know of a GUI utility which can change the login screen resolution??

---

