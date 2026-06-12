---
title: "How do I change QT theme from Gnome?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zooounds on 2008-10-08
I have always used kcontrol but it's no more it seems.

How do I do it now?

---

### Post by Hairy_Palms on 2008-10-08
sudo apt-get install qt4-qtconfig

---

### Post by zooounds on 2008-10-08
Chaning the theme with that tool does not effect the apperance of the applications...

I run ktorrent but it still looks the same.

---

### Post by Delvien on 2008-10-08
> **zooounds said:**
> Chaning the theme with that tool does not effect the apperance of the applications...

I run ktorrent but it still looks the same.

qttool doesn't do it, only minor changes.

You have to install kcontrol, try doing it again, see if you were missing libraries

```
 sudo aptitude install kcontrol 
```

kcontrol works for me, not sure why its not for you. When you run it in the terminal, does it give you errors?

---

### Post by zooounds on 2008-10-08
> **Delvien said:**
> qttool doesn't do it, only minor changes.

You have to install kcontrol, try doing it again, see if you were missing libraries

```
 sudo aptitude install kcontrol 
```

kcontrol works for me, not sure why its not for you. When you run it in the terminal, does it give you errors?

It says there is no install candidate for kcontrol and exit. Same as before.

```

f@air:~$ LANG="en" sudo apt-get  install kcontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2a kdebase-workspace-bin
E: Package kcontrol has no installation candidate

```

---

### Post by Hairy_Palms on 2008-10-08
ah, KDE apps can be changed with sudo apt-get install systemsettings

---

### Post by zooounds on 2008-10-08
> **Hairy_Palms said:**
> ah, KDE apps can be changed with sudo apt-get install systemsettings

systemsettings just show a blank window with "Overview" (greyed out) and a search box.

---

### Post by psyke83 on 2008-10-08
Also highly, highly recommended (to make VLC and QT4 apps look native): [http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)

We should package this for Intrepid+1 and set it as the default QT theme for GNOME.

---

### Post by zooounds on 2008-10-08
> **psyke83 said:**
> Also highly, highly recommended (to make VLC and QT4 apps look native): [http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)

We should package this for Intrepid+1 and set it as the default QT theme for GNOME.


Absolutely :)

My problem now is that I can set the theme at all in 8.10.

---

### Post by zooounds on 2008-10-08
Someone?

Sombody must have managed to change the qt-theme from Gnome (Ubuntu) or else we have an issue here for release day.

The qtconfig-program remebers my settings but it won't affect the apperance in any way.

The program I test with (ktorrent) is a QT4 program. These ugly menus are killing my eyes.

---

### Post by psyke83 on 2008-10-08
> **zooounds said:**
> Someone?

Sombody must have managed to change the qt-theme from Gnome (Ubuntu) or else we have an issue here for release day.

The qtconfig-program remebers my settings but it won't affect the apperance in any way.

The program I test with (ktorrent) is a QT4 program. These ugly menus are killing my eyes.

What about VLC? Remember that you need to manually click the File menu and Save for the style settings to take effect.

QGTKStyle doesn't work with older QT3 apps (which may account for KTorrent), or KDE apps use a different means to pick the theme.

---

### Post by zooounds on 2008-10-08
> **psyke83 said:**
> What about VLC? Remember that you need to manually click the File menu and Save for the style settings to take effect.

QGTKStyle doesn't work with older QT3 apps (which may account for KTorrent), or KDE apps use a different means to pick the theme.

I can't change to any other theme than the default one.

Edit: VLC change apprance but ktorrent won't. Ktorrent is QT4 could that be it?

---

### Post by BwackNinja on 2008-10-08
if vlc's appearance changes but ktorrent's doesn't, then ktorrent is a QT3 app or it sets its own style, try installing qt3-qtconfig instead.

---

### Post by zooounds on 2008-10-08
> **BwackNinja said:**
> if vlc's appearance changes but ktorrent's doesn't, then ktorrent is a QT3 app or it sets its own style, try installing qt3-qtconfig instead.

Very logic to have qtconfig-qt3 in package qt3-qtconfig ;)

Anyway, ktorrent stays the same. Maybe it forces it own style, if so I'll choose another bt-client. Anyway to tell?

---

### Post by vikrant82 on 2008-10-08
I have had similar issues changing theme colors for amarok.

Unfortunately, installing kcontrol was only way to do it. But its no longer installable with current versions of kde 4 libraries in intrepid repositories. 

So I had to manually forcibly install a few debs,

kcontrol_3.5.9-0ubuntu7_i386
kdebase-data_3.5.9-0ubuntu7.3_all
kicker_3.5.9-0ubuntu7.3_i386
libkonq4_3.5.9-0ubuntu7.3_i386

Installing these would probably break kde4 for a while (which you should be able to recover after you are done with kcontrol and have removed those debs.)

Doing this, I could figure out what files got modified in .kde folder. (I think some files in  ~/.kde/share/config, arranging by last modified date would help you there.)

It was funny to find that there's no way I could re-theme my kde 3 apps in intrepid, if I have installed kde4.

---

### Post by zooounds on 2008-10-08
> **vikrant82 said:**
> I have had similar issues changing theme colors for amarok.

Unfortunately, installing kcontrol was only way to do it. But its no longer installable with current versions of kde 4 libraries in intrepid repositories. 

So I had to manually forcibly install a few debs,

kcontrol_3.5.9-0ubuntu7_i386
kdebase-data_3.5.9-0ubuntu7.3_all
kicker_3.5.9-0ubuntu7.3_i386
libkonq4_3.5.9-0ubuntu7.3_i386

Installing these would probably break kde4 for a while (which you should be able to recover after you are done with kcontrol and have removed those debs.)

Doing this, I could figure out what files got modified in .kde folder. (I think some files in  ~/.kde/share/config, arranging by last modified date would help you there.)

It was funny to find that there's no way I could re-theme my kde 3 apps in intrepid, if I have installed kde4.

Nut ktorrent says it uses KDE 4. I do not want to break anything.

---

### Post by Starks on 2008-10-08
Everyone in this thread fails hard.

The best solution is as follows:

sudo apt-get install systemsettings
gksu systemsettings

---

### Post by nike984 on 2008-10-08
> **Starks said:**
> Everyone in this thread fails hard.

The best solution is as follows:

sudo apt-get install systemsettings
gksu systemsettings

Yes, as Stark mentioned, in KDE4, kcontrol will be substituted to "systemsettings".
You can change all the kde4 application's theme at there. 
If things doesn't works for you, install the whole kubuntu package by
sudo aptitude install kubuntu-desktop

then, "systemsettings" will work without any problem.

p.s. you don't even need gksudo for running "systemsettings"

---

### Post by zooounds on 2008-10-09
> **nike984 said:**
> Yes, as Stark mentioned, in KDE4, kcontrol will be substituted to "systemsettings".
You can change all the kde4 application's theme at there. 
If things doesn't works for you, install the whole kubuntu package by
sudo aptitude install kubuntu-desktop

then, "systemsettings" will work without any problem.

p.s. you don't even need gksudo for running "systemsettings"

Installing the whole kubuntu-package is not a option. It will fill my menus with program I do not want.

Running systemsettings with sudo will change the theme for my user? If I do not use sudo systemsettings fails as I mentioned above.

---

### Post by zooounds on 2008-10-09
I gave up an installed kubuntu-desktop. Systemsettings now works and I can change style. Installed the GTK-style and now everything looks perfect.

---

### Post by bash on 2008-10-09
Strange. qt4-qtconfig does the trick for me. VLC and Virtualbox both take on the gtkstyle theme.

Installed ktorrent in my VM and it seems completly oblivious to any theme changes. Just uses the default oxygen theme. And installing systemsettings doesn't help. It only offers to change the icon and the smiley theme.

---

### Post by Starks on 2008-10-09
jeez people!

systemsettings does not require a full kubuntu-desktop installation.

IT ONLY REQUIRES A BARE MINIMUM SET OF KDE4 LIBS.

---

### Post by zooounds on 2008-10-09
> **Starks said:**
> jeez people!

systemsettings does not require a full kubuntu-desktop installation.

IT ONLY REQUIRES A BARE MINIMUM SET OF KDE4 LIBS.

I know that but could you or someone else tell EXACTLY which packages to install. It's not enough with any of the packages mentioned here.

If you don't know please do not write in this thread just because you want to say how stupid we are.

I think of my self as a pretty competent user but my knowledge of KDE (especeiall KDE 4) is limited. 

All I wanted to do was to change the theme from the ugly default.

---

### Post by Starks on 2008-10-09
selecting systemsettings in the package manager will give you everything you need if you are intrepid.

see?

[http://packages.ubuntu.com/intrepid/systemsettings](http://packages.ubuntu.com/intrepid/systemsettings)

---

### Post by zooounds on 2008-10-09
> **Starks said:**
> selecting systemsettings in the package manager will give you everything you need if you are intrepid.

Nope.

---

### Post by Starks on 2008-10-09
> **zooounds said:**
> Nope.

explain. synaptic, aptitude, and apt-get fetch all of the needed packages for me.

---

### Post by zooounds on 2008-10-09
> **Starks said:**
> explain. synaptic, aptitude, and apt-get fetch all of the needed packages for me.

After isntalling systemsettings all I got was a "blank" page (like all the plugins used by systemsettings) were missing.

After running systemsettings as root and restarting it as me it worked better. After the the only module missing was the "theme module".

Hard changing the theme when this is missing.

Maybe it's a bug but it's reality.

After installing kubuntu-desktop everything worked. So SOMETHING is missing when only installing "systemsettings".

---

### Post by Starks on 2008-10-09
i think installing gtk-qt-engine (and its deps) should put the tab there.

---

### Post by zooounds on 2008-10-09
> **Starks said:**
> i think installing gtk-qt-engine (and its deps) should put the tab there.

That seems really strange indeed? Why should this package have any effect on systemsettings? Isn't that just another theme to select?

---

### Post by Starks on 2008-10-09
> **zooounds said:**
> That seems really strange indeed? Why should this package have any effect on systemsettings? Isn't that just another theme to select?

Yes, but selectable through Appearance tab in systemsettings it would create.

---

### Post by jeroenvrp on 2008-10-11
@zooounds:

I installed kdebase-workspace, that also pulls systemsettings in. Although I'm still not able to get more than a blank systemsettings when I run at as myself, I can do a 'gksudo systemsettings' and change everything I need. After this is done I copied /root/.kderc and all files in /root/.kde/share/config/ to the same location in my homedir. (/root/.kde and /root/.kderc where not there yet btw, so maybe you must move them out of the way first)

This is a workaround, but now all my KDE3 and KDE4 application will run the way I like it.

Good luck.

---

### Post by BwackNinja on 2008-10-12
installing kdebase-bin allowed me to change the theme with systemsettings.

---

### Post by tghe-retford on 2008-10-14
> **jeroenvrp said:**
> I installed kdebase-workspace, that also pulls systemsettings in...

This is a workaround, but now all my KDE3 and KDE4 application will run the way I like it.
That worked for me, without the need to run it as root. The only problem I have now is that I use a dark theme and whereas I can use QT3 Configuration, QT4 settings and KDE4 System Settings to change the colours QT applications use, I can't change the colours Kaffeine displays, whilst the fonts and cursor have changed.

---

### Post by quazi on 2008-10-27
Systemsettings is appearing blank for me as well unless ran as root.  

I was trying to change the appearance of amarok, but if I use the gksudo workaround, it only affects the fonts; the general appearance is unchanged.

---

### Post by quazi on 2008-10-30
> **tghe-retford said:**
> That worked for me, without the need to run it as root. The only problem I have now is that I use a dark theme and whereas I can use QT3 Configuration, QT4 settings and KDE4 System Settings to change the colours QT applications use, I can't change the colours Kaffeine displays, whilst the fonts and cursor have changed.

I tried installing kdebase-workspace, but I still get a blank window when I run systemsettings as a normal user.  Here's the terminal output:
```
$ systemsettings
findServiceByDesktopPath:  not found
systemsettings(3570) MainWindow::readMenu: "" Looking for children in ' "" '

```

---

