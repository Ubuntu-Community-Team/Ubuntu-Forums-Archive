---
title: "No graphical login"
date: 2009-11-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-11-25
Anyone else lose their graphical login?

I just go straight to a tty, then I can login and startx.

I also notice that I can't "unlock" the gdm gui.

---

### Post by ranch hand on 2009-11-25
Everything is cool here.  I assume by the "GDM gui you are referring to the "Loginscreen" useless gui.  I can unlock it.  Not sure why I would want to but I can.

---

### Post by darco on 2009-11-25
> **kansasnoob said:**
> Anyone else lose their graphical login?

I just go straight to a tty, then I can login and startx.

I also notice that I can't "unlock" the gdm gui.

Was that due to the partial upgrading offering that I see today?

I also see kernel 2.6.32.5-5 is waiting in the wings....


d

---

### Post by kansasnoob on 2009-11-25
I first noticed this after this round of updates:

> Commit Log for Tue Nov 24 11:13:55 2009


Upgraded the following packages:
gedit (2.28.0-1ubuntu2) to 2.29.2-0ubuntu1
gedit-common (2.28.0-1ubuntu2) to 2.29.2-0ubuntu1
libgtksourceview2.0-0 (2.8.1-1) to 2.9.2-0ubuntu1
libgtksourceview2.0-common (2.8.1-1) to 2.9.2-0ubuntu1
linux-generic (2.6.32.4.4) to 2.6.32.5.5
linux-headers-generic (2.6.32.4.4) to 2.6.32.5.5
linux-image-generic (2.6.32.4.4) to 2.6.32.5.5

Installed the following packages:
linux-headers-2.6.32-5 (2.6.32-5.6)
linux-headers-2.6.32-5-generic (2.6.32-5.6)
linux-image-2.6.32-5-generic (2.6.32-5.6)


I've tried the older kernel and same thing. I figure it's just part of the development game but thought I'd see if others have the same problem.

---

### Post by zika on 2009-11-25
> **darco said:**
> Was that due to the partial upgrading offering that I see today?

I also see kernel 2.6.32.5-5 is waiting in the wings....


dWas there a partial upgrade today? There was gedit that was kept back but it is over now ...
```
~$ uname -a
Linux ... 2.6.32-5-generic #6-Ubuntu SMP Mon Nov 23 12:25:24 UTC 2009 x86_64 GNU/Linux
```

---

### Post by kansasnoob on 2009-11-25
> **darco said:**
> Was that due to the partial upgrading offering that I see today?

I also see kernel 2.6.32.5-5 is waiting in the wings....


d

I haven't had any partial updates here.

---

### Post by darco on 2009-11-25
hmm, not sure why I am getting this message. I did run update prior..

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  deluge deluge-common linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  app-install-data-partner avant-window-navigator-data-trunk
  avant-window-navigator-trunk awn-applets-c-core-trunk
  awn-applets-python-core-trunk awn-settings-trunk computer-janitor
  computer-janitor-gtk gconf-defaults-service gconf2 gconf2-common gedit
  gedit-common hdparm libawn1-trunk libeggdbus-1-0 libexif12 libgconf2-4
  libgtksourceview2.0-0 libgtksourceview2.0-common libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libqt4-dbus libqt4-xml libqtcore4
  libqtgui4 libv4l-0 paprefs pavucontrol pm-utils policykit-1 pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-module-zeroconf pulseaudio-utils python-awn-extras-trunk
  python-awn-trunk tomboy xserver-xorg-input-evdev
45 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 13.1MB of archives.
After this operation, 2,052kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by kansasnoob on 2009-11-25
> **darco said:**
> hmm, not sure why I am getting this message. I did run update prior..

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  deluge deluge-common linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  app-install-data-partner avant-window-navigator-data-trunk
  avant-window-navigator-trunk awn-applets-c-core-trunk
  awn-applets-python-core-trunk awn-settings-trunk computer-janitor
  computer-janitor-gtk gconf-defaults-service gconf2 gconf2-common gedit
  gedit-common hdparm libawn1-trunk libeggdbus-1-0 libexif12 libgconf2-4
  libgtksourceview2.0-0 libgtksourceview2.0-common libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libqt4-dbus libqt4-xml libqtcore4
  libqtgui4 libv4l-0 paprefs pavucontrol pm-utils policykit-1 pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-module-zeroconf pulseaudio-utils python-awn-extras-trunk
  python-awn-trunk tomboy xserver-xorg-input-evdev
45 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 13.1MB of archives.
After this operation, 2,052kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

I dunno.

I tried launching gdmsetup from terminal and get this:

> lance@lance-desktop:~$ gdmsetup

** (gdmsetup:1890): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:1890): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:1890): DEBUG: init delay=30
** (gdmsetup:1890): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:1890): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:1890): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1890): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1890): DEBUG: adding monitor for '/home/lance/.face'
** (gdmsetup:1890): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1890): DEBUG: Found 2 sessions for user lance
** (gdmsetup:1890): DEBUG: GdmUserManager: not adding session without a x11 display: /org/freedesktop/ConsoleKit/Session1
** (gdmsetup:1890): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:1890): DEBUG: GdmUserManager: sessions changed user=lance num=1
** (gdmsetup:1890): DEBUG: GdmUserManager: added session for user: lance
** (gdmsetup:1890): DEBUG: GdmUserManager: history output: lance    93

** (gdmsetup:1890): DEBUG: GdmUserManager: history output: nobody   4

** (gdmsetup:1890): DEBUG: GdmUserManager: excluding user 'nobody'

** (gdmsetup:1890): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:1890): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:1890): WARNING **: Error calling GetValue('daemon/TimedLogin'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:1890): DEBUG: init user='(null)' auto=False

** (gdmsetup:1890): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files



No idea what "The name org.gnome.DisplayManager was not provided by any .service files" means.

---

### Post by DougieFresh4U on 2009-11-25
Your not alone as I keep getting dumped to 'tty1'
No desktop. Have reinstalled Lucid 3 times and after reboot, dumped to 'tty1'
My other 3 Lucid partitions boot just fine.

---

### Post by kansasnoob on 2009-11-25
> **DougieFresh4U said:**
> Your not alone as I keep getting dumped to 'tty1'
No desktop. Have reinstalled Lucid 3 times and after reboot, dumped to 'tty1'
My other 3 Lucid partitions boot just fine.

I can still login OK. Just enter user name, then password, then startx. So it's a minor inconvenience.

---

### Post by ublintu on 2009-11-25
Hi,
Sorry, because I post this in here: I have the same problem, but in karmic.
Actually a lot of people have the same problem with the "tty1 screen". I could find several posts in the forum in this topic. 
It happened with me after an update and it`s happening randomly in my case.

---

### Post by DougieFresh4U on 2009-11-25
> **kansasnoob said:**
> I can still login OK. Just enter user name, then password, then startx. So it's a minor inconvenience.

startx spits a bunch of errors for me
**connection to X server lost**

---

### Post by kansasnoob on 2009-11-25
Goody, goody, the fun's finally beginning!

I must be sick. I actually look forward to borkage like this!

---

### Post by caryb on 2009-11-25
I guess this is related to another thread about kde being broken! I have the same problem in Kubuntuland, when I sudo startx I get a black screen & a mouse & that's it.


Cary

---

### Post by Gina on 2009-11-26
Mine goes to a tty screen at first but if you leave it a minute or two it goes to the animated graphical screen and then the GUI login.  You can log in at the tty screen then again if you leave it, Lucid goes graphical and continues as expected.

I did wonder if this was deliberate in some way to allow command line settings before the main startup.  Just in the testing phase.  But as to why - no idea :lol:

---

### Post by kansasnoob on 2009-11-26
> **Gina said:**
> Mine goes to a tty screen at first but if you leave it a minute or two it goes to the animated graphical screen and then the GUI login.  You can log in at the tty screen then again if you leave it, Lucid goes graphical and continues as expected.

I did wonder if this was deliberate in some way to allow command line settings before the main startup.  Just in the testing phase.  But as to why - no idea :lol:

I'll wait on the next reboot to see if it goes to the gui.

I suffer from a major case of impatience;)

---

### Post by Gina on 2009-11-26
That's not a good thing to have with computers :lolflag:

---

### Post by ublintu on 2009-11-29
Hi,
These days I`m reading a book and I found something, which is might be helpful:

On the 120th page in the Beginning Ubuntu Linux 3rd Edition: 
"...all I see is a black screen with some text at the top saying
&#8220;Ubuntu hardy ubuntu tty1&#8221; and beneath that &#8220;ubuntu login:.&#8221;
For some reason, the automatic configuration of your graphics card failed during installa-
tion. See the following section for instructions on configuring your GUI manually....."

But in the next section nothing about this or helpful in this case.

Edit: for me too. If I leave it for a while, I can get graphical login

---

### Post by kansasnoob on 2009-11-30
I've actually left mine for several minutes and it never goes to a graphical login. It just sits and waits forever until I enter my login, pwd, and startx.

---

### Post by sports fan Matt on 2009-11-30
I haven't rebooted in a week..as i've been on vacation.  Would it be wise to reboot and see what occurs?

---

### Post by sports fan Matt on 2009-11-30
Everything worked fine but I got a white screen before the desktop loaded.

---

