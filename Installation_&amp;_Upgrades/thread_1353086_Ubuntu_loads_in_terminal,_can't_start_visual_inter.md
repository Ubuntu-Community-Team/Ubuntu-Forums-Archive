---
title: "Ubuntu loads in terminal, can't start visual interface"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Laucien on 2009-12-12
Well, that's definitely the awesomest problem I've seen so far lol :D. When Ubuntu boots up it goes directly to terminal, and I don't know how to start visual interface.

I tried sudo gdm and got
```

** (gdm-binary:1825): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1825): WARNING **: Could not acquire name; bailing out
```

Heh. Help?

---

### Post by commodore256 on 2009-12-12
Try Ctrl+Alt+F2, login (you will not see asterisks in place of your password, but it's there) and type in...

```
sudo apt-get remove gdm
```

```
sudo apt-get install gdm
```

Then do

```
sudo reboot
```

---

### Post by Laucien on 2009-12-12
I can't even get to type anything anymore, after the ubuntu logo on bootup I get only black screen with that white _ on the top left corner :(
It happened before I got to try this you said.

e: Ok I managed to get to the 'tty6' screen, now there's "xxxx-laptop login:" but I can't type anything...

---

### Post by Laucien on 2009-12-12
I started terminal via live cd and done that, but it still gets stuck on the black screen after the ubuntu logo :(

---

### Post by Laucien on 2009-12-14
Anyone? :(

---

### Post by thetechnaddict on 2009-12-19
Same problem following update. 

I've rebooted into recovery mode, and dropped to shell with networking, which gives me a root terminal.

Removed gdm using apt-get
reinstalled gdm...

Still no go

To be more specific - Ubuntu loads and delivers me to a white terminal screen in the upper left hand corner of the screen. 

On entering "sudo gdm" and providing password I am given the warning:

** (gdm-binary:1519): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1519): WARNING **: Could not acquire name; bailing out

I also reinstalled gmd (apt-get --reinstall install gmd)

running startx shows xwindows is already running.

I've also installed KDE and set that to default during the install procedure

On rebooting I am presented with a KDE login screen (under gmd the user was automatically logged in)

Enter username and password...

Everything hangs; well the cursor moves, and there is the pretty kde wallpaper and nothing else.

On reboot (the nasty way) I selected xterm to give me a terminal

sudo kdm start gives no response at all 
sudo gmd start

screen flickers and then response:

gmd-binary[1508]: WARNING: Unable to find users: no seat-id found
gdm-binary[1508]: WARNING: GdmDisplay lasted 0.059145 seconds

for what it is worth dbus is running

---

### Post by thetechnaddict on 2009-12-19
I've just re-installed 9.10, then upgraded - and same problem - so it wasn't an interrupted upgrade, the upgrade has killed gdm.

---

### Post by thetechnaddict on 2009-12-19
I'm way over my head here  - but here's something...

I rebooted in recovery mode, then went to terminal with networking
gives me a root cli
typed startx 
Gnome starts
Logged out
logged in as user
get the xterm
exit (like logging out)
get gdm
login

Now all works...

Is this a permissions issue?

---

### Post by thetechnaddict on 2009-12-21
Oops - worked for while, now goes to blank screen even whith startx from root

---

### Post by BossDj on 2009-12-23
I'm having this problem as well. 99% of problems I encounter with Ubuntu directly relate to my old nvidia graphics card. Do you all happen to have nvidia (or at least ancient) video cards?

---

### Post by HeadHunter00 on 2009-12-23
in the terminal screen, type in:
> sudo apt-get install kdm
and then:
> sudo dpkg reconfigure kdm
and select kdm. After that:
> sudo restart kdm

---

### Post by HeadHunter00 on 2009-12-23
Other display manager is slim. To install that, just replace all the kdm with slim

---

