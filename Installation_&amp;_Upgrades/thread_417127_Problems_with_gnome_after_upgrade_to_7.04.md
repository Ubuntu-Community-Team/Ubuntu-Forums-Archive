---
title: "Problems with gnome after upgrade to 7.04"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Mikebgr on 2007-04-21
As title suggests, i'm having a bit of a problem after the upgrade. When i log in, a window pops up :
" I've detected a panel already running,
and will now exit."

And also this appears in another window:

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem."
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mike"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/6433
Initializing gnome-mount extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_1"
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
Can't register passkey agent
Passkey agent already exists
gkrellongrun: No such file or directory : /dev/cpu/0/cpuid

(update-notifier:6539): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```Looks like there is a problem with a key binded to nothing, and a passkey agent being registered 2 times( ? ) but I cant fix those, nor I know if they are the cause of my problems.

Note that i'm posting from ubuntu right now, as I may not have any gnome-panel(s) running, but a firefox launcher i have in my desktop works

Also note that gkrellm seems to work fine! (it shows both "cpu" usage)

Any help appreciated!

Update: loging in with fluxbox works just fine, and also I created a new user and logged into gnome with the new user and all worked fine too! So it must be some of my settings. Anyone care to help?

---

### Post by Mikebgr on 2007-04-21
Is my information not clear enough or is my problem too hard? Or just none bothers?

---

### Post by sverre76 on 2007-04-21
I am having the same problem. I am also having some kind of problems with https / ssl in firefox. Could both these have something to do with errors when installing encryption / decryption or ssl packages or something like that?!

I am clueless however, but hopefully my reply can bump your post back up so that we can get some attention :)

---

### Post by sverre76 on 2007-04-21
I have got it working now. I am not sure how, but I think all I did was re-installing python with
```
sudo aptitude reinstall python2.5
```

Then I removed Mozilla Firefox and installed the one available at mozilla.org by following [this tutorial]("https://help.ubuntu.com/community/FirefoxNewVersion")

---

### Post by Mikebgr on 2007-04-22
I fixed my problem too! After lots of hours and lots of tinkering around I dont know what caused the problem. One weird thing:

I logged in as an extra user in gnome. Then I didnt log out, but I just "switched user" and tried to log in to my main account. Things worked a little better then, and I managed to resetup my session-manager settings.

---

