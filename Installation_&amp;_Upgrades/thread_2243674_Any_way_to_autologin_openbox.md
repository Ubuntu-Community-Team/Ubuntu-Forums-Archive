---
title: "Any way to autologin openbox?"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by boyofford on 2014-09-10
Hi all,

trying to create a minimal install with various programs using openbox and minimal install to create a media centre.

One of problems I've got is getting it to autologin, which is a must as intend to run primarily from remote control.

I read it was possible with slim login manager but on install slim does not even show.
Also read you could do this...[http://linux.koolsolutions.com/2009/03/15/howto-autologin-into-your-linux-system-without-xdm-gdm-kdm-etc/]("http://linux.koolsolutions.com/2009/03/15/howto-autologin-into-your-linux-system-without-xdm-gdm-kdm-etc/")
but that doesn't ssem to work for me.

anyone got any other ideas?

---

### Post by boyofford on 2014-09-10
Scratch that.
Got it working with slim.

---

### Post by boyofford on 2014-09-14
edit: still not solved, slim is extremely flakey and not autologin properly.

---

### Post by fantab on 2014-09-14
Tell us what steps you've taken so far and what exactly is the problem... 'flakey' doesn't exactly describe the problem.
Post screenshots if possible.

Edit */etc/slim.conf* to uncomment the 'auto_login' command and replace  'no' with 'yes': 

 > auto_login                yes 

You have to be careful when using 'autologin' with slim as it disables 'gnome-keyring' to unlock and cause problems with gnome-keyring dependent apps, like chromium for instance.
EDIt: This issue appears to have been fixed since slim 1.3.5-1

---

### Post by vasa1 on 2014-09-15
> **fantab said:**
> ...
Edit */etc/slim.conf* to uncomment the 'auto_login' command and replace  'no' with 'yes': 
...
@fantab, similar information is here: [http://crunchbang.org/forums/viewtopic.php?id=24227](http://crunchbang.org/forums/viewtopic.php?id=24227) but they mention one more step which is to "Uncomment and change default_user to your username".

I don't use autologin myself and so don't know what does or doesn't work.

---

### Post by fantab on 2014-09-15
> **vasa1 said:**
> @fantab, similar information is here: [http://crunchbang.org/forums/viewtopic.php?id=24227](http://crunchbang.org/forums/viewtopic.php?id=24227) but they mention one more step which is to "Uncomment and change default_user to your username".

I don't use autologin myself and so don't know what does or doesn't work.

Thanks vasa... my bad.
Yes OP has to "*Uncomment and change default_user to your username*".
edit: Even [this wiki]("https://wiki.archlinux.org/index.php/Slim#Enable_Autologin") says so.

I had tried Slim some time back with Arch, but not with 'autologin', I don't use it either.

---

### Post by boyofford on 2014-09-15
Apoligies for lack of info, It was late and was thinking that maybe I'd posted in wrong place anyhow!

With slim I changed the lines in /etc/slim.conf
```
# default_user        simone
and
auto_login          no

```
to
```
default_user        rich
and
auto_login         yes

```

I then have xbmc starting automatically via adding xbmc to ~/.config/openbox/autostart

The autostarting xbmc was working fine when starting openbox via startx command previously, and I think via slim when loging in normally( I think!? I tried loads of stuff I didn't understand fully in a short amount of time lol and late at night!)

However after setting up with autologin as above sometimes it would just work, say 25% of the time.
Other times it would get to openbox then was a massive lag before xbmc opened, say 25% of time again.
Sometimes in above scenarios shutdown/reboot options had vanished from xbmc.
The other 50% of time it would quickly go to xbmc screen for a second then go back to slim login screen.

I've no tried setting up with "nodm" login manager, which works but is again slow to load xbmc and also shutdown/reboot options appear to of disappeared from shutdown menu.....I'm looking into seeing if can that sorted at the moment.

Also tried various things scattered accross web that didn't seem to work at all and I've forgotten as only writing down stuff that looks promising.
I tried other login managers but had loads of dependencies and slowed down xbmc start/running, I'm only using a old dell dimension for this that I plan to hide up the chimney in our house.

The minimal install version I'm using is 14.04 if thats important.
I've probably done 5+ installs in a virtual pc testing various stuff and restored verious snapshots though only one install so far on this old dell, but not against reinstalling it if you think I've just messed it up to much lol.

---

### Post by boyofford on 2014-09-15
I should probably add my setup for "nodm"
/etc/default/nodm
```
# nodm configuration

# Set NODM_ENABLED to something different than 'false' to enable nodm
NODM_ENABLED=true

# User to autologin for
NODM_USER=rich

# First vt to try when looking for free VTs
NODM_FIRST_VT=7

# X session
NODM_XSESSION=/etc/X11/Xsession

# Options for the X server
NODM_X_OPTIONS='-nolisten tcp'

# If an X session will run for less than this time in seconds, nodm will wait an
# increasing bit of time before restarting the session.
NODM_MIN_SESSION_TIME=60

```

/home/rich/.xsession
```
#!/bin/sh
openbox-session
```

---

### Post by boyofford on 2014-09-15
After a little more digging I've realised that not only are the power options missing but dvd drive is not being munted using "nodm".

However if I exit and restart xbmc using sudo xbmc in terminal then all options return.
Must be a permissions/groups thing right? on the hunt for a solution now.

Actually seems to boot openbox/xbmc pretty quick so maybe "nodm" is the way forward, as well as I can sort this stuff out? Should I start a new thread?

typing "groups" in terminal gives me
```
rich adm dialout cdrom sudo audio dip video plugdev users lpadmin sambershare
```

---

### Post by boyofford on 2014-09-15
yet another (pre me going to bed!) update

now got openbox starting using a script I modifyed from xbmc forums, I've left in some stuff that ain't needed, like original comments
```
# xbmc-upstart
# starts XBMC on startup by using xinit.
# by default runs as xbmc, to change edit below.
env USER=rich

description     "XBMC-barebones-upstart-script"
author          "Matt Filetto"

# if you use mysql you need to wait for your network device
# that means you should add 'and net-device-up IFACE!=lo' behind the udevtrigger

start on (filesystem and stopped udevtrigger)
stop on runlevel [016]

# tell upstart to respawn the process if abnormal exit
respawn
respawn limit 10 5
limit nice 21 21

script
# exec su -c "xinit /usr/bin/xbmc --standalone -- /usr/bin/X -bs -nolisten tcp :0" $USER
# the following two are to get an idea, if you want to user a window manager
exec su -c "xinit /usr/bin/openbox-session --  /usr/bin/X -bs -nolisten tcp :0" $USER
end script
```
The above I created as /etc/init/xbmc.conf 

This starts extremely quick but still can not shutdown/reboot or use dvd drive.
I've realised that can't even get to dvd drive using pcmanfm which I'm using as file manager.

Any ideas? something lingering from previous install? therefore reinstall again?

p.s. sorry this seems to be turning into more of a blog

---

### Post by boyofford on 2014-09-15
I'll mark as solved tomorrow,  and post link to solution for lurkers!

---

### Post by boyofford on 2014-09-16
Basically I tweaked the upstart outlined here to suit openbox-session [http://forum.xbmc.org/showthread.php?tid=165707]("http://forum.xbmc.org/showthread.php?tid=165707")
and created a file /etc/polkit-1/localauthority/50-local.d/custom-actions.pkla as mentioned here [http://forum.xbmc.org/showthread.php?tid=174854&pid=1795059#pid1795059]("http://forum.xbmc.org/showthread.php?tid=174854&pid=1795059#pid1795059")

---

