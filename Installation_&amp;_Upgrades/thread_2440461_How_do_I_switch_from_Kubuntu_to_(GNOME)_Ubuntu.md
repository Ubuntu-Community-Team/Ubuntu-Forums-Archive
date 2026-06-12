---
title: "How do I switch from Kubuntu to (GNOME) Ubuntu"
date: 2020-04-10
forum: Installation &amp; Upgrades
---

### Post by prkos on 2020-04-10
I used to be a GNOME user for many years. 

This year I installed Kubuntu 19.10 to try it out and although I'm super happy with some bits overall I think I was a lot more productive on GNOME and I'd like to get back to it. 

How can I do that? 

Do I need to do a complete OS clean install? 

Can GNOME be installed while using Plasma and made to replace the Plasma (on reboot or similar)? 

Can GNOME and Plasma coexist? 

What's the best way to proceed here?

---

### Post by webaake on 2020-04-11
Yes. You can install the package ubuntu-gnome-desktop. It will install a ton of packages. Log out and when logging again in you chose gnome session. They can co-exist but KDE and Gnome are both heavy DE:s and it can, sometimes, create problems.

---

### Post by CatKiller on 2020-04-11
> **prkos said:**
> Can GNOME and Plasma coexist? 

Yes. As webaake says, you can install the metapackage that covers the parts you're interested in. You might want everything in the ubuntu-desktop, or you might only be interested in Gnome itself. 

At the login screen you'll be able to pick which one you want to log into, and everything works as you'd expect. 

The thing that makes it a pain, though, is that now you've got two file browsers, two text editors, two, calculators, two settings applications, two package manager front ends, two of everything that's installed in a desktop environment by default. A lot of those things are going to show up in both menus, and you may find that the wrong one gets launched automatically when you're doing stuff.

It's possible to tidy that stuff up as you go, so that you only see the stuff that you're interested in when you're using a particular desktop environment. It's also possible to install a new desktop environment and then remove all the components of the old desktop environment. Since we're coming up to a new LTS, though, I would recommend just sticking with Plasma till the end of April and then do a fresh install of 20.04 with whichever desktop environment you prefer.

---

### Post by prkos on 2020-04-11
Thank you both! 

I installed the ubuntu-gnome-desktop package and I have successfully logged out of Plasma and logged into GNOME. It was a bit confusing on the login screen which option to choose, I chose plain "Ubuntu", although the first on the list were two options with the same name, something like "GNOME x org" or sth. 

I need to spend time now to configure the settings, although it feels good to be back, the Super key to Shell makes such a huge difference for me. 

Clementine audio player now shows its window correctly after clicking on the tray icon. On Plasma it shows the window contents correctly only the first time, the second time the window contents is just blank until I Quit and restart it. But the "Scroll over icon to change track" doesn't work on GNOME either. 

Thank you CatKiller for suggesting to wait the next LTS. I figured if I'll be reinstalling everything I must as well do the "dual" test to make sure which flavor I really want. I only plan on using the one as default and tweak it to my liking so it makes sense to have it all clean. I have a feeling Plasma effects, as super exciting as they are, and as useful as some behaviour details are on Plasma, GNOME gets out of the way more when it comes to the frequent app switching, searching etc making it more usable. 

I wish I could cherry pick with a lot more control which features to use from which environment. The April's fools joke was a very cruel one to me :-#

---

### Post by prkos on 2020-04-25
Which package(s) can I purge to remove the Plasma but keep the KDE apps and their config? I've decided to stick with G :D

---

### Post by DuckHook on 2020-04-25
> **prkos said:**
> Which package(s) can I purge to remove the Plasma but keep the KDE apps and their config? I've decided to stick with G :D
You may find the link in my sig: "The Best 'buntu Flavour" useful. You have already decided on your DE, so ignore the stuff about the various DEs. Focus on the areas that explain why mixing DEs is a bad idea.

Since Focal has just come out, my suggestion would be to backup all of your important data, then do a virgin install of vanilla Ubuntu for a clean and trouble-free experience.

---

### Post by CatKiller on 2020-04-25
> **prkos said:**
> Which package(s) can I purge to remove the Plasma but keep the KDE apps and their config? I've decided to stick with G :D

The easiest way to do it is to back up your files (the configuration for all your applications is stored in your Home folder) do a fresh install of Ubuntu 20.04, since you prefer to use Gnome, and then install just whichever KDE applications you want to use.

---

### Post by DuckHook on 2020-04-25
&#8593;+1

It is also worth noting that some KDE apps will drag in almost as many QT dependencies as if you were doing a full Kubuntu install. To see the extent of the dependencies each app will drag in, you may wish to simulate the install first with apt's -s flag. Example:```
sudo apt install -s dolphin
```

The amount of dependencies that will be dragged in might surprise you.

A purely personal opinion, but I have chosen to forego KDE apps, even those I find a bit superior to their Gnome counterparts, because I do not want to spam my Gnome desktop environment. By way of example, here is what gets dragged in for just a simple Dolphin install:```
duckhook@Zeus:~$ apt install -s dolphin
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  baloo-kf5 catdoc ffmpegthumbs kdegraphics-thumbnailers kdelibs5-data kinit kio kpackagelauncherqml
  kpackagetool5 kwayland-data kwayland-integration libattica0.4 libdbusmenu-qt2 libdbusmenu-qt5-2
  libdlrestrictions1 libdolphinvcs5 libepub0 libfam0 libhfstospell9 libkdecore5 libkdeui5 libkf5archive5
  libkf5attica5 libkf5auth-data libkf5auth5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin
  libkf5baloowidgets-data libkf5baloowidgets5 libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data
  libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5
  libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5
  libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data
  libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5
  libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data
  libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5
  libkf5notifications-data libkf5notifications5 libkf5package-data libkf5package5 libkf5parts-data
  libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkio5 libkonq-common libkonq5-templates libkwalletbackend5-5 liblmdb0
  libphonon4 libphonon4qt5-4 libpolkit-qt5-1-1 libpoppler-qt5-1 libqt4-opengl libqt4-svg libqt5quickcontrols2-5
  libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5script5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libsolid4 libstreamanalyzer0v5 libstreams0v5 libvoikko1 libzip4 phonon
  phonon-backend-gstreamer phonon-backend-gstreamer-common phonon4qt5 phonon4qt5-backend-vlc
  qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 sonnet-plugins
```
That's 150 packages!

&#8230;and that's just for one app. There is no way that a succession of such installs won't end up making trouble at the next version upgrade.

Different strategies exist to mitigate this problem. They all have their pros and cons:

[LIST=1]
[*]Running such apps in a VM,
[*]If feeling adventurous, using Docker or LXD. This last is in my sig: *Sandboxing Apps with LXD*. Please note that this method is not recommended for Linux newbies.
[/LIST]

---

