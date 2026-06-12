---
title: "X issue after install"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Shad0wguy on 2005-10-13
Hey all.  I just sign up to these forums to find help for my problem.

I installed the 64-bit version of Ubuntu as a dualboot on my computer.  Now the instalation went fine, however, upon boot I get an error.  The message that comes up is...
"Failed to start X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
If I hit yes, it gives me a lot of technical info that I can't decipher.  I have tried tweaking xorg.conf and no luck.  The only thing I noticed was that when I check the log file after the error, I see a message saying  some fonts couldn't be loaded.

Does anyone have any ideas?  This is driving me insane trying to get this working.

---

### Post by adwait on 2005-10-13
It would help if you could post the log file here. Try running
```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by jnoreiko on 2005-10-13
Did you have the nvidia drivers installed before you upgraded?
It sounds like the very same problem I have had.

---

### Post by jnoreiko on 2005-10-13
```
sudo dpkg-reconfigure xserver-xorg 
```


hasn't improved things.

The log it shows has lines like

> /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!

after that there lots of line about fonts.

---

### Post by jnoreiko on 2005-10-16
Has anyone with this problem managed to fix it... other than by reinstalling from scratch?

---

### Post by heimo on 2005-10-16
[quote=jnoreiko]Has anyone with this problem managed to fix it... other than by reinstalling from scratch?[/quote]

Did you try commenting out "dri" line from module-section of /etc/X11/xorg.conf?
```
Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
#        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
```

---

### Post by jnoreiko on 2005-10-16
That takes care fo the libdri error (what does dri do by the way? won't I need it?)

Still getting lots of lines
> warning: font renderer for ".pcf" alreadt registered at priority 0"

---

### Post by ladoga on 2005-10-16
I have this same(?) problem after dist-upgrade too. 
Unable to startx.

here's my /var/log/Xorg.0.log
[http://www.saunalahti.fi/ladoga/Xorg.0.log](http://www.saunalahti.fi/ladoga/Xorg.0.log)

startx reports stuff at end of that log:
```
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

Fatal server error:
could not open default font 'fixed';
the X server's font paths might be misconfigured, remote font server(s)
may be unreachable, and/or local fonts may not be installed or are not
configured correctly.

People inexperienced with the X Window System should have either the
"x-window-system" or "x-window-system-core" packages installed.
# apt-get install x-window-system-core
# apt-get install x-window-system

Other useful commands to run include:
$ dpkg --status xserver-common
$ dpkg --status xfonts-base
$ zmore /usr/share/doc/xorg-common/FAQ.gz

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

i reinstalled xwindow-system-core and xfont packages but problem remains.
if i try to install xfonts-base-transcoded apt-get complains:
```
REinstallation of xfonts-base-transcoded is not possible, it cannot be downloaded
```

my sources.list should be ok tho:
[http://www.saunalahti.fi/ladoga/sources.list](http://www.saunalahti.fi/ladoga/sources.list)


Im getting so much trouble with these dist-upgrades i think id better switch to debian. Otherwise Ubuntu has been great for me.

---

### Post by jnoreiko on 2005-10-16
That looks like it's exactly the same as mine.
Were you usign the nvidia drivers before upgrade?

---

### Post by mbwardle on 2005-10-18
I noticed a lot of the same error messages, but the final one was the critical one for me.

It went something like:
Cannot open default font "fixed"

I worked around the problem by adding the line:
fixed -b&h-lucidatypewriter-medium-r-normal-sans-14-100-100-100-m-80-iso8859-1

to /usr/share/X11/fonts/100dpi/fonts.alias since nothing else I tried worked.

There were similar problems during the Hoary->Breezy development, but these were because the fonts used to be kept somewhere like /usr/lib/X11/fonts but are now kept in /usr/share/X11/fonts.  This time the directories were all correctly configured, but there was nothing to tell the X server which default font to use.

I filed [bug 18039]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18039") for this.  If it's the same problem you have, please add any extra information there.

---

### Post by Shad0wguy on 2005-10-18
[QUOTE=jnoreiko]Did you have the nvidia drivers installed before you upgraded?
It sounds like the very same problem I have had.[/QUOTE]

I'm using ATI.

---

### Post by jnoreiko on 2005-10-18
It hasn't worked.
I booted into recovery mode, since regular boot freezes on the X server's bluescreen warning.
I made the font alias change, and tried gdm. I got a warning that no screen could be opened.
I thought this might be due to the other things I tried to fix this. So I put 'nvidia' back as a driver, and uncommented 'dri' (see above).
Running gdm after that gave me the same errors about fonts.

---

### Post by Patrik Johansson on 2005-10-18
I had the problem with no screen found  so heres atleast how you solve that....
I also used the ati driver.
After getting the bluescreen, just press enter and when you get back to the login, login in and then write :
```

sudo dpkg-reconfigure xserver-xorg
```
This will allow you to make som changes to your current xserver setup.
The only thin you have to change is the display driver, its set to ati so just change it to "vesa", that worked for me.
Leave everything else as it is.
Then when you reboot everything should work just fine!

---

