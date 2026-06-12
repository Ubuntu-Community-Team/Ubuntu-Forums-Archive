---
title: "Natty with KDE Dual Monitor Issue"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by mebunto on 2011-06-14
Hi, I have a pretty stable Natty setup on Sandybridge pc with dual monitors connected to vga and DP2, with the latest xorg ppa drivers.  I set up both monitors in monitor settings, and saved as the default, however the setting is lost when I reboot.  Is there a way of fixing this?

Second question is to ask whether I can get some decent screen savers for kde?

Thanks

---

### Post by dabl on 2011-06-14
First, the settings.

Alt-F2 "kdesudo systemsettings" and enter your super user password.

then make your screen settings, and "apply", and exit.  That should save the settings permanently.

KDE screen savers can be a separate reply.  :)

---

### Post by Zorael on 2011-06-15
Could that be related to these bugs?
[list][*][Screen Resolution is not being restored after relogin](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/268434)
[*][resolution not preserved by KDE](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/571657)[/list]

Looking at the startup script, I would suggest you also make sure your **~/.kde/share/config/startupconfigkeys** file contains a line like thus;
```
krandrrc Display ApplyOnStartup **[COLOR="Green"]_true_[/COLOR]**
```

As for screensavers, install these packages;
```
kscreensaver kscreensaver-xsavers kscreensaver-xsavers-extra kscreensaver-xsavers-webcollage xscreensaver-gl xscreensaver-gl-extra xscreensaver-screensaver-bsod
```
One terminal command to install them all;
```
$ sudo apt-get install --no-install-recommends kscreensaver kscreensaver-xsavers kscreensaver-xsavers-extra kscreensaver-xsavers-webcollage xscreensaver-gl xscreensaver-gl-extra xscreensaver-screensaver-bsod
```

---

### Post by mebunto on 2011-06-16
Thanks for the replies guys.  I did the kdesudo command, changed and saved the settings - rebooted - but the issue remains.

There is an error message after I run the command:

> temple@ubuntu:~$ kdesudo systemsettings
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/temple/.config/ibus/bus
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
temple@ubuntu:~$ 


I've checked the screen resolution bugs and that isn't applicable in this case; although I think it is representative of the fact that the display software in general isn't quite right.

I've checked all the screensaver packages, and I've installed them all apart from the dodgey ones.

I've just checked startupconfigkeys and the krandrrc line was set "false" so I've changed that to "true" and I'm rebooting now ...

That was interesting!  All monitor settings were lost and I had to re-configure them.  startupconfigkeys had been rewritten and set to "false" again.

I'm going to edit it again.  At the moment it looks like this:

> kcminputrc Mouse cursorTheme 'Oxygen_Black'
kcminputrc Mouse cursorSize ''
ksplashrc KSplash Theme Default
ksplashrc KSplash Engine KSplashX
krandrrc Display ApplyOnStartup false
krandrrc Display StartupCommands ''
krandrrc [Screen0]
krandrrc [Screen1]
krandrrc [Screen2]
krandrrc [Screen3]
kcmfonts General forceFontDPI 0
kdeglobals Locale Language '' # trigger requesting languages from KLocale
kdeglobals Locale Country ''

Now I will edit monitor settings, which should give me VGA1 running at 1680x1050(Auto) and DP2 at 2560x1600 to the left of VGA1, with DP2 being the primary output.  But startupconfigkeys didn't change - should it?

---

### Post by hsantanna on 2011-07-23
> **mebunto said:**
> Hi, I have a pretty stable Natty setup on Sandybridge pc with dual monitors connected to vga and DP2, with the latest xorg ppa drivers.  I set up both monitors in monitor settings, and saved as the default, however the setting is lost when I reboot.  Is there a way of fixing this?


This is related to this KDE bug:
[Bug 183143 - Display Settings are Lost on Logout ]("https://bugs.kde.org/show_bug.cgi?id=183143")

please vote to that bug, so developers will pay more attention to this opend bug since 2009. [-o<

I'm also affected by this and it annoys me a lot, because as teacher I use a different projector on each classroom, with a different resolution each one.

> Second question is to ask whether I can get some decent screen savers for kde?

There are some really good screensavers packages on repository (including 3D/gl ones). I think they are the same Xscreensaver packages (but not the Xscreensaver daemon) which kscreensaver uses. I'm not on kubuntu right now so a can't checklist those packages for you (when i really need to use HDMI output I have to sadly boot on windows).

I checked this ([http://packages.ubuntu.com/search?searchon=names&keywords=kscreensaver]("http://packages.ubuntu.com/search?searchon=names&keywords=kscreensaver")) and will suggest you to try this ones:

kscreensaver, kscreensaver-xsavers, xscreensaver-gl, kscreensaver-xsavers-webcollage, kscreensaver-xsavers-extra

just do

```
sudo apt-get install kscreensaver kscreensaver-xsavers xscreensaver-gl kscreensaver-xsavers-webcollage kscreensaver-xsavers-extra
```

---

### Post by mebunto on 2011-09-27
didn't notice your posting - I've added 20 votes as it's so annoying!!!

---

