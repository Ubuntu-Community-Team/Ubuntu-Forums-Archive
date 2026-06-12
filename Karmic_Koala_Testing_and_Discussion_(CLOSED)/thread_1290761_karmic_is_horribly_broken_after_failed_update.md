---
title: "karmic is horribly broken after failed update"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DouglasAWh on 2009-10-13
I removed everything in $dir = /var/cache/apt/archives/ but after an apt-get upgrade and still getting

```

gtk-update-icon-cache: error while loading shared libraries: /usr/lib/libobject-2.0.so.0: file too short
WARNING: icon cache generation failed

Errors were encountered while processing:

/$dir/gnome-session-bin*
/$dir/gnome-session-canberra*
/$dir/nautilus-data*
/$dir/rhythmbox*
/$dir/gnome-settings-daemon*

```

never mind the extra slashes in my variable...I've kept them for readability.  And no, the output does not actually include the *, but I don't think that part is important. I've tried to uninstall nautilus, but it says I should re-install before I uninstall because it's horribly broken (I don't remember the exact output, but that's the gist).  

I've tried the recovery mode dpkg and that doesn't work.  I've been prompted at times to use the -force (or something like that) and that doesn't work.

If this is going to take a lot of trouble-shooting, I feel like I might be best off doing a re-install, but I'd really like to avoid that.

In the end, the problem is that gdm/kdm/whatever won't start.  X wasn't starting, but I got that fixed...but the image it displays is mangled.  This machine still works fine on Jaunty and minus and hiccup somewhere in the middle has been working fine with Karmic since day zero.

---

### Post by ranch hand on 2009-10-13
I think this may be a good time for an "apt-get dist-upgrade".  This may well fix your files.  If you can't get good function I would try booting to xterm and using that.

---

### Post by kansasnoob on 2009-10-13
> **DouglasAWh said:**
> I removed everything in $dir = /var/cache/apt/archives/ but after an apt-get upgrade and still getting

```

gtk-update-icon-cache: error while loading shared libraries: /usr/lib/libobject-2.0.so.0: file too short
WARNING: icon cache generation failed

Errors were encountered while processing:

/$dir/gnome-session-bin*
/$dir/gnome-session-canberra*
/$dir/nautilus-data*
/$dir/rhythmbox*
/$dir/gnome-settings-daemon*

```

never mind the extra slashes in my variable...I've kept them for readability.  And no, the output does not actually include the *, but I don't think that part is important. I've tried to uninstall nautilus, but it says I should re-install before I uninstall because it's horribly broken (I don't remember the exact output, but that's the gist).  

I've tried the recovery mode dpkg and that doesn't work.  I've been prompted at times to use the -force (or something like that) and that doesn't work.

If this is going to take a lot of trouble-shooting, I feel like I might be best off doing a re-install, but I'd really like to avoid that.

In the end, the problem is that gdm/kdm/whatever won't start.  X wasn't starting, but I got that fixed...but the image it displays is mangled.  This machine still works fine on Jaunty and minus and hiccup somewhere in the middle has been working fine with Karmic since day zero.

"I've tried to uninstall nautilus"? How is that possible? Do you also have Thunar or something installed?

"In the end, the problem is that gdm/kdm/whatever won't start." Maybe try "sudo apt-get install --reinstall gdm".

---

### Post by DouglasAWh on 2009-10-13
> **ranch hand said:**
> I think this may be a good time for an "apt-get dist-upgrade".  This may well fix your files.  If you can't get good function I would try booting to xterm and using that.

tried dist-upgrade. What do you mean about using xterm?

---

### Post by DouglasAWh on 2009-10-13
> **kansasnoob said:**
> "I've tried to uninstall nautilus"? How is that possible? Do you also have Thunar or something installed?

I uninstalled it from shell, in order to clear out the stuff giving errors to tried to uninstall.  I try the suggestion with gdm, though I'm not sure how that's going to fix, say, the rhythmbox error.

---

### Post by ranch hand on 2009-10-14
> **DouglasAWh said:**
> tried dist-upgrade. What do you mean about using xterm?
when you get to the login screen and click on the user there is a bunch of stuff that opens on the bar at the bottom of the screen.

On is "session" and in the little box it says "gnome".  If you click on the little arrow you will get some other choices.  One is xterm.

If you click on that and log in, you will get a small terminal in the upper right corner of your screen that will work fine if you keep the cursor inside it.  Works just like your regular terminal.

---

### Post by VMC on 2009-10-14
> **ranch hand said:**
> when you get to the login screen and click on the user there is a bunch of stuff that opens on the bar at the bottom of the screen.

On is "session" and in the little box it says "gnome".  If you click on the little arrow you will get some other choices.  One is xterm.

If you click on that and log in, you will get a small terminal in the upper right corner of your screen that will work fine if you keep the cursor inside it.  Works just like your regular terminal.

Its the default terminal that comes with X. Also little know info regarding xterm is that it does have menus. Hold the control key down and using your mouse keys, push either left, right or middle. You will see three different menus.

---

### Post by DouglasAWh on 2009-10-14
> **ranch hand said:**
> when you get to the login screen and click on the user there is a bunch of stuff that opens on the bar at the bottom of the screen.

This might be great, if I ever got to a login screen. All the work I have done has been from netroot.  If I try to boot normally, I can't even use CTRL+ALT+ F keys to change sessions.

---

### Post by DouglasAWh on 2009-10-15
I've traced this back to glibc, but if I try to uninstall that there are like a bazillion dependencies.  I'd type the error, but I've changed my language to non-English to help myself learn...which is great until I can't effing boot!

So, I try to use 

```

setlocale en_US.utf-8

```

However, this throws errors like OMGZ!!!!!ELEVEN!!!11!!!!!!!1111

I don't even know where to start. Obviously I can't stroll back if I'm  in an actually shell but all the errors seem to do with python:

/usr/lib/python2.6/dist-packages/aptsources/distinfo.py has 4 errors that I can see.

/usr/lib/python2.6/gettext.py has 4 errors.

I posted in the ubuntu+1 IRC and got no help.  Can someone please help?

---

### Post by ranch hand on 2009-10-15
Well, you are in a mess.

I really would run;
```

sudo apt-get update

AND THEN;

sudo apt-get dist-upgrade

```This is not something that I would do as a first choice but files are well screwed.  I think it may very well be a help in your case.

I have, in the coarse of this testing cycle, had every one of my 9.10 variations (5 32bit and 7 64bit) unbootable at least once.  I have resorted to dist-upgrade twice.  It did the job both times too.  It really is using a large hammer, but sometimes that is what you need.

EDIT
I am going to be gone (day work on a remote ranch) for a couple of days.  When I get back, I will be checking this thread first off.  I want to see it marked "Solved" and to be able to see how this was done.  HAVE FUN

---

### Post by ronacc on 2009-10-15
try what ranchhand suggested first . if that does not work, boot into your live cd , mount your / and try replacing /usr/lib/python2.6/dist-packages/aptsources/distinfo.py and /usr/lib/python2.6/gettext.py with the ones from the live cd then try again .

---

### Post by DouglasAWh on 2009-10-15
> **ranch hand said:**
> Well, you are in a mess.

I really would run;
```

sudo apt-get update

AND THEN;

sudo apt-get dist-upgrade

```

Did that. I've tried every version of that possible, trust me.  Something in dpkg needs to be cleared or I need to attack these errors head on. 

Interestingly enough, I've updated another install of Karmic from alpha 2 and I get a similar error to one of the many I was getting with the install at home:

```

WARNING: WARNING: /usr/share/pyshared/lsb_release.py is linked but does not belong to any package.
Errors were encountered while processing:
acpid
acpi-support
xserver-xorg
xorg
ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Again, that was just one of my errors at home though.

I think I'll probably just re-install.  Booting up a live CD and installing packages isn't really worth it on a beta release.

---

### Post by ranch hand on 2009-10-16
Well, I am back.  Steers shipped, heifers processed, cows culled.  I am whipped.

The warning about /usr/share/pyshared/lsb_release.py is nothing to worry about. Just delete it.  It is an orphan left over from Jaunty that does not get auto-removed.

Ubuntu-desktop is really not something I would worry about too much either.  It is the meta-package for you desktop stuff.  This is not going to stop you from booting.

Did you try the --force command with dpkg (see "man dpkg")?

---

### Post by DouglasAWh on 2009-10-17
> **ranch hand said:**
> Well, I am back.  Steers shipped, heifers processed, cows culled.  I am whipped.

The warning about /usr/share/pyshared/lsb_release.py is nothing to worry about. Just delete it.  It is an orphan left over from Jaunty that does not get auto-removed.

Ubuntu-desktop is really not something I would worry about too much either.  It is the meta-package for you desktop stuff.  This is not going to stop you from booting.

Did you try the --force command with dpkg (see "man dpkg")?

I did try the --force with dpkg sadly, but...

I just reformatted.  I hadn't realized I'd done this, but all my data was on a different partition, so it seems to have gone flawlessly...of course, I haven't booted up the Jaunty partition since the reformat, so that could be totally fubared. :)

---

