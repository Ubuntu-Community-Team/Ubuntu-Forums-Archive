---
title: "desktop -10.10 pwid could not be determined"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-11-17
i am trying to install desktop ubuntu in my p4 machine
with lg studioworks 520si monitor.
i get the message it could not find pwid and gets stuck before starting X server and gets stuck at desktop loading.
is there a command line installer ?
what command from no graphix boot?

---

### Post by nickleboyblue on 2010-11-18
For the ubuntu alternate installer, see:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

The alternate installer runs without graphics, and guides you through the installation in a similarly simple manner.  It does, however, require that you download yet another cd image and use that one instead.

Once the install is complete, if the graphics still don't work, determine what graphics card you are using and, if possible, get the driver for it from the command line.

At that point, backup your xorg.config file that is found at /etc/X11.  Then run your driver's xorg configure tool to write a new xorg.config file.  Reboot, and see if that fixes things.  If, before running the driver's xorg configure tool, you have at least some graphics running, restore your backed up xorg.config file and you'll have at least some functionality.

For an nvidia graphics card:

```
sudo apt-get install nvidia-glx #(or whichever driver your card needs)
cd /etc/X11
sudo mv xorg.conf xorg.conf.backup #(backup of the file)
sudo nvidia-xconfig
```

If it doesn't work, restore the old xorg.conf to retrieve previous functionality:

```
cd /etc/X11
sudo mv xorg.conf.backup xorg.conf
```

Hope that helps.

---

### Post by ramaswamyps on 2010-11-18
i am trying now dpkg fix--broken
it downloads 200mb files.
hope after this it will work.
i am now on command line of the cdboot up.

---

### Post by ramaswamyps on 2010-11-18
no luck.
it cannot complete dpkg run.
gets stuck.

---

### Post by nickleboyblue on 2010-11-18
Alright then, what are your system specs?  The important things to know are how much memory you have, Which motherboard, screen, and graphics card does your computer use?

If you can see things on your screen despite it telling you it can't find a pwid for your screen, there is a slight chance that you don't have a major problem, and a fix similar to the one above is possible, but it sounds like you might not have enough ram or some similar issue.

Does your computer boot alright on a live cd?

If you didn't build the computer yourself, you might check your model online and see if it's listed in the linux compatibility lists, and if others have had similar issues.  A little research can go a long way...

---

### Post by ramaswamyps on 2010-11-21
my desktop has p4 512 mb ram 2 hdds 80gb and 250gb ide control.
mother board is gigabyte [845 chipset] LG studioworks 520si monitor.
ubuntu-10 beta worked fine in this comp
this may not be hardware problem as the livecd does not show desktop in my laptop also which has 2 GB of ram.
laptop i have installed netbook distro of 10.10

then cd checks alright for md5sum and reading full cd by mediacheck.
there is something unknown going on here.

X ends up showing blank ubuntu desktop and then gets stuck there in laptop and desktop.

---

### Post by nickleboyblue on 2010-11-21
So, if I'm understanding this correctly, you installed the system, but when it boots, it gets all the way to the desktop but fails to bring up the top or bottom panels?

If that is the case, it could be caused by several things.  Most commonly, gnome-panel isn't working properly.

Once you get to the "blank desktop," hit Ctrl-Alt-F1 to enter a terminal.  Then, type the following:

```
sudo apt-get --purge remove gnome-panel*
```

Don't forget to include the asterisk.  Once that is finished, type:

```
sudo apt-get install gnome-panel*
```

Let us know if that works.

(Your system SHOULD work with your current specs, though there is a SLIGHT chance you need the motherboard drivers.  I say SLIGHT, because you said Ubuntu-10 beta worked on it.)

---

### Post by ramaswamyps on 2010-11-22
nope :(
i cannot install it yet. still the same problem.
the livecd cannot make a install or licd gnome ,just prior to that it gets stuck.
i am able to boot runlevel 1 without X
at the time it is starting X i get the pwid problem and proceeds to desktop and gets stuck.
but i could not find a line command to install.

---

