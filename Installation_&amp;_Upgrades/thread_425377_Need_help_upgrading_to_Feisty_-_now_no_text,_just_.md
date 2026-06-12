---
title: "Need help upgrading to Feisty - now no text, just blocks!"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by c0rkee on 2007-04-27
Followed the upgrade instructions and installed all Edgy updates first, then rebooted.

Was going to update to Feisty, but although I can access most applications from their icons, all drop down & menu bars consist of rectangular blocks.
At logon, I just followed my usual routine, but was running blind.

Instead of the usual ubuntu graphic I get a basic Gnome box.

Obviously some sort of graphical error, but the question is - how do I navigate to sort it out when I can't view the any options & menus etc?

Any help would be appreciated..........

Cheers
Colin  :(

---

### Post by hal8000 on 2007-04-27
As you cant see any menues try  ctrl-alt-F1

Hopefully in console mode you may get a login prompt (console mode res should be different from normal X so this may work)

Reconfigure your Xorg with


sudo dpkg-reconfigure xserver-xorg


I always do this on debian systems to give me finer control over the display. You may get some other answers as well, hope that helps.

---

### Post by c0rkee on 2007-04-27
> **hal8000 said:**
> As you cant see any menues try  ctrl-alt-F1

Hopefully in console mode you may get a login prompt (console mode res should be different from normal X so this may work)

Reconfigure your Xorg with


sudo dpkg-reconfigure xserver-xorg


I always do this on debian systems to give me finer control over the display. You may get some other answers as well, hope that helps.
So far, so good, got inot the console mode and have attempted to reconfigure Xorg, but at the ned of choosing the various settings, I get
"xserver-xorg postinst warning: overwriting possibly customised configuration file. Backing up in/tec/X11/Xorg.conf 20020427211644"
then I get the ubuntu:~$ prompt again.  Tried just return and sudo install but no joy....
Any ideas what to enter here?

---

### Post by eapache on 2007-04-27
That just means that it is making changes to your config file and that it is being backed up in case you don't like the changes. Now try Ctrl-Alt-F7 to return to graphical mode, and Ctrl-Alt-Backspace once in graphical mode to restart the display manager with your re-configured settings. If that doesn't work, please list your hardware specs.

---

### Post by c0rkee on 2007-04-27
> **eapache said:**
> That just means that it is making changes to your config file and that it is being backed up in case you don't like the changes. Now try Ctrl-Alt-F7 to return to graphical mode, and Ctrl-Alt-Backspace once in graphical mode to restart the display manager with your re-configured settings. If that doesn't work, please list your hardware specs.
Still no joy - seems the settings didn't take (or more likely wrong) - but I'll persevere with it and try to match all the settings to my hardware, rather than using the automatic options offered.

Thanks for the offer of more help, but need some sleep before moving this along - will continue tomorrow....

---

### Post by c0rkee on 2007-04-28
> **c0rkee said:**
> Still no joy - seems the settings didn't take (or more likely wrong) - but I'll persevere with it and try to match all the settings to my hardware, rather than using the automatic options offered.

Thanks for the offer of more help, but need some sleep before moving this along - will continue tomorrow....
Tried manual configuration just now, but after using Ctrl-Alt-F7 screen says "X server now disabled"  Ctrl-Alt_backspace doesn't work (presumably as the X server is disabled).
Restarted using Ctrl-Alt-Del at least gets me back to where I started - rectangular text blocks.
I did get an X Server diagnostic screen earlier showing the following, but I realise this may not be valid anymore?
Using config file: "/etc/X11/xorg,conf"
(EE) (error) Unable to find valid framebuffer device
(EE) R128(0): Failed to open framebuffer device
(EE) Screen(s) found, but not have useable configuration
Fatal server error:
no screens found

I have taken shots of the detailed output screens, in case these might be of use in diagnosing the problem.

My Machine is a 900Mhz Athlon, mobo AMR K7VZA. The graphics card is an ATi rage Pro 128.

Hope this may help in sorting my ongoing problem - otherwise I think a reinstall may in be order.

Thanks
Colin

---

### Post by eapache on 2007-04-29
after Ctrl-Alt-F7 and the message 'X server disabled', do you get a command prompt? If so, type in

startx

which should start the server manually. Ctrl-Alt-Backspace restarts it if it is already running, but I forgot that reconfiguring it would turn it off entirely.

If you don't get a command prompt, type the same command into the prompt you do get directly after reconfiguring x.

---

