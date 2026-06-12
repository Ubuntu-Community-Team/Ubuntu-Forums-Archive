---
title: "Upgrade to gutsy - no gui shutdown/restart"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by GaiusJuliusCaesar on 2007-10-20
I recently upgraded to Gutsy and on reboot I got a message following the first login to say GNOME had a problem applying settings and it would try again next login.  I logged out and logged back in and now the GUI buttons for shutdown and restart are missing both from the menu and login window.

On another post I saw the following to try and remedy;
Menu: System > Administration > Login Window
In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

Trouble is I have a rather odd resolution display (1024x480) and I can't see the bottom of this window to get to the setting.  Can anyone help with a work around, like which conf file would hold these settings so I can make the changes from an editor, (even which keystrokes to press to check the box and select okay on the dialogue would work).

Thanks for any help anyone can offer.

---

### Post by rex_the_first on 2007-10-20
It may seem silly but did you change your login theme?  Also could the resolution mean the buttons are still there but not shown on your screen (i.e. you can move your mouse further down than the monitor shows).  If so you might need to set X11 with your resolution.

---

### Post by GaiusJuliusCaesar on 2007-10-20
Thanks for the quick reply.  It took me a while to get the xorg.conf settings right for the odd resolution, when I move the  cursor to the bottom of the screen it stops there (also you can see top and bottom panels).

The box just cuts off  at the bottom of the screen, a lot of GNOME boxes do too but I've been able to work around most of them.  I tried a number of alternative DEs like XFCE but they all suffer from the 480 high problem and GNOME being the least offender.

When I got the laptop in Windows putting the res to anything higher (vertically) than 480 it would shift up and down with the cursor which was ugly but useful for this type of problem.  Is there anyway to do this in xorg?

I would say that I can't wait for a resolution independent desktop environment scaling everything to fit but then my machine would probably be too old to run that anyway.

---

### Post by rex_the_first on 2007-10-20
Could you attach your /etc/X11/xorg.conf
What graphics card is in your laptop, have you check on google to see if people have problems with it?  Maybe you need to install a new driver for it but I am not sure.

---

### Post by GaiusJuliusCaesar on 2007-10-20
Sure the conf file is attached.  It's the display though; it can't do any higher that 1024x480.  Running modes like 800x600 or 1024x768 result in the screen not displaying below the 480 mark.

The computer's a Sony VAIO picturebook (PCG-C1XD) with a neomagic display adapter and an LCD with a native display of 1024x768.

I think the only way to resolve my problem would be to edit the settings for the login window via a conf file, assuming that where the settings are kept.  Do you know where the login window settings are, could someone post their's so I can compare.

I don't know if it's related but I got the same error message when logging in last;
> There was an error starting the GNOME Settings Daemon.

Some things , such as themes, sounds, or background settings may not work properly
.....
GNOME will still try to restart the Settings Daemon next time you log in

It said something else about not getting any error message from the failure.  I logged out and in and it didn't happen again.

---

### Post by rex_the_first on 2007-10-20
The xorg looks empty.  Could you post it again.  In the meantime I can only suggest trying to get 1024x768 working.  You could back up your xorg.conf and reset the xorg settings with
```
sudo dpkg-reconfigure xserver-xorg
```
but I don't know where the log in config is, sorry.

---

### Post by GaiusJuliusCaesar on 2007-10-21
Sorry about the empty xorg.conf file, I don't know what happened there.  I've reattached it to this post.

When I reconfigure xserver-xorg I end up with the display not working as this laptop's display doesn't go any higher than 1024x480.

I'm not sure if I was clear from the beginning but 1024x480 is the correct resolution for this display, it was made to work like that.  It took me some time to get xorg.conf to work properly with this res in the first place, the problem I have is;
GNOME isn't well designed to work at a vertical resolution of 480 as a lot of dialogue boxes are fixed height and go past the bottom of the screen.  Back to my initial post I need either;
[LIST=1]
[*]A way to change the setting via the conf file
[*]The key strokes to navigate the login tab; Click on the tab then the number of times to press the tab key to get to the checkbox, then toggle it with the space bar, then the number of times to press tab to get to the OK button
[/LIST]

Have a look at my attached file if you like, I may have to resort to enabling 1024x768 and using the vga out to get this resolved.

Can anyone help me with the list items above?

---

### Post by rex_the_first on 2007-10-21
>The computer's a Sony VAIO picturebook (PCG-C1XD) with a neomagic display adapter and an LCD with a native display of 1024x768.

Sorry I thought the native display was 1024x768 from your earlier post not 1024x480.  Sorry, I don't think I can help much.

---

### Post by GaiusJuliusCaesar on 2007-10-21
Oops, I am an idiot.  Sorry about that, so used to following 1024 with x768 that I made a fairly important typo.  Yes my problems are not the resolution but with GNOME's shortcomings on low vertical resolutions.

all the best
Julius

---

