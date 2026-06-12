---
title: "write in Japanese with Karmic 9.10"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilcontegis on 2009-10-04
Hi guys, I always installed anthy successfully since 7.04. But with the 9.10 I cannot succeed to make it working! Can somebody please tell me how to do it? Maybe the guide I am following is a bit old and not does not work anymore.
Thank you very much.
Regards,
Teo

---

### Post by overdrank on 2009-10-04
Moved to Karmic Koala Testing and Discussion

---

### Post by Zorael on 2009-10-05
Well, you get to choose between scim, uim and ibus as your input methods. Anthy will work with either of those. ibus (I-Bus) seems to be the up-and-coming method, but it's still lacking features. I understand Fedora is using it per default in 12?

As a warning, I'm having issues with dead keys (^´`¨~ etc) not working with scim (at all with direct input) and ibus (xim apps), but I haven't tried uim for a while. I tried it earlier but didn't like it when I noticed the panel didn't autohide when it wasn't in use (direct input).

Further, if you run KDE, none of these have Qt4 panel applets. So you either have to use the GNOME one and apply ninja hax to get them to not look ugly as sin, or you resort to using the Qt3 panel, ending up having to install KDE 3.5.9 libs that no other app uses anymore.


For scim, grab:
[list=1][*]scim
[*]scim-anthy
[*]scim-bridge-client-qt
[*]scim-bridge-client-qt4
[*](skim if you want the **_Qt3 panel_**. The Gnome panel is included automatically in scim, and there is no Qt4 panel yet.)
[*](scim-tomoe if you want the handwriting recognition tool, need to add the japaneseteam ppa)
[*](scim-tegaki if you want this alternative handwriting recognition tool) (currently broken)[/list]
Uncertain what scim-uim does. Uncertain as to the difference between scim-qtimm and scim-bridge-client-qt (both are input libs for Qt3 apps).


For uim, grab:
[list=1][*]uim
[*]uim-anthy
[*]uim-applet-gnome
[*](uim-applet-kde if you want the **_Qt3 panel_**. There is no Qt4 panel yet.)
[*]uim-qt
[*]uim-qt4
[*](uim-xim pulled as a dependency)[/list]

For ibus, grab:
[list=1][*]ibus
[*]ibus-anthy
[*]ibus-gtk
[*]ibus-qt4[/list]
Uncertain as to whether ibus works with Qt3 apps at all, but it seems the Qt4 input libs work with Qt3 apps as well?


Regardless of which input method you choose, set it to be the default for your current locale, such as by using im-switch. This will open a menu in which you can pick your method of choice.
```
$ sudo im-switch -c
```
Remove sudo if you want to change your user's specific setting. And if you want to change the method for a different locale than the current, add the argument **-z lang_LANG**. My default locale always end up as **all_ALL** (Swedish locale, English language setting), but yours might differ.
```
$ sudo im-switch -z all_ALL -c
$ sudo im-switch -z en_US -c
$ sudo im-switch -z ja_JP -c
...
```
Order of argument matters; -c must be last.

To change the input method for all installed locales, do the following. Again, remove sudo to make it a user-specific setting.
```
$ for X in /etc/alternatives/xinput*; do sudo update-alternatives --config $X; done
```

If your chosen locale doesn't have your input method installed as an alternative (which seems to happen with ibus), you can add it with **update-alternatives --install**, but I don't know how to do that properly anymore. It just gives me recursive symlinks when I try. So refer to the man page, then tell me how.
[INDENT]The alternative is to manually edit **/var/lib/dpkg/alternatives/xinput-lang_LANG**, such as **xinput-en_US**. Refer to what files are available in that directory.[/INDENT]

The file you want to *add a reference to*, either with update-alternatives --install or by manually modifying **/var/lib/dpkg/alternatives/xinput-***, is located by default in **/etc/X11/xinit/xinput.d**, and by default named after the input method (**scim**, **uim**, **ibus**, **skim** in case of scim with the Qt3 panel applet). This file contains environment variables that X exports at launch to make sure all thereafter started apps use the specified input method.

The variables are:
[list][*]XIM=(label of method)
[*]XIM_PROGRAM=(path to executable)
[*]XIM_ARGS=(arguments to be passed to executable, if any)
[*](XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=boolean whether executable runs in the background or not, very optional)
[*]GTK_IM_MODULE=(label of method to be used for GTK apps)
[*]QT_IM_MODULE=(label of method to be used for Qt apps [both Qt3 and Qt4, I believe])
[*]DEPENDS=(packages needed to be installed for the input method to work)[/list]

In default installations, said file might be misconfigured. This is the case for skim installations, at the very least, which LACK a value for the **XIM_PROGRAM** variable. There is a launchpad bug report for this, but the maintainers frankly don't seem interested. Perhaps scim is just dead upstream.

An example **/etc/X11/xinit/xinput.d/ibus** would thus be;
```
XIM=ibus
XIM_PROGRAM=/usr/bin/ibus-daemon
XIM_ARGS="-x"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-ibus.so ]; then
    GTK_IM_MODULE=ibus
else
    GTK_IM_MODULE=xim
fi

if [ -e /usr/lib/qt4/plugins/inputmethods/libqtim-ibus.so ]; then
	QT_IM_MODULE=ibus
else
	QT_IM_MODULE=xim
fi
DEPENDS="ibus, ibus-gtk, ibus-qt4"
```
The *if-then-else-fi* clauses in there just make sure the files that manage input under GTK and Qt exist.

A (by me) ***strongly recommended*** file for scim and skim would be;
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```

Reboot. May work by logging out and in, definitely works if you restart the X server (from a tty: sudo stop gdm && sudo start gdm, or sudo stop kdm && sudo start kdm)



Troubleshooting checklist;
[list=1][*]All relevant packages installed?
[*]Did you restart X?
[*]Is the input method setting for your locale pointing to the right xinput.d file (**/etc/X11/xinit/xinput.d/***)? Double-check what the /etc/alternatives/xinput-lang_LANG symlink points to. [indent]**_NOTE_**; **im-switch** is only a tool that will make it *easier* to change input methods. In essence, it will set the **/etc/alternatives** and/or **~/.alternatives** symlinks _FOR YOU_. The symlinks are still what decides which method is to be used.[/indent]
[*]Do you have user-specific settings overriding system-wide ones? See **im-switch -l**.
[*]Is the xinput.d file in use properly configured? Must have entries for XIM and XIM_PROGRAM to work with XIM apps, must have entry for GTK_IM_MODULE and QT_IM_MODULE to work with GTK and Qt apps respectively.
[*]After having logged in, open up a terminal and do 'env | grep IM'. Does it list the variables, and do they have the proper values? If not, bad symlinks or bad xinput.d file; see earlier steps.[/list]

Before assuming that you have it all properly set up, try it in a GTK, a Qt *and* a XIM app. If you run GNOME, you have plenty of GTK apps. As for Qt apps, well, I'm not sure what gnomeys use. As for XIM, install **xterm** and try your keybinds in it.


edit, forgot the ppas.
ibus packages, just slightly newer thant he ones in the main repos: [https://launchpad.net/~ibus-dev/+archive/ibus-1.2-karmic](https://launchpad.net/~ibus-dev/+archive/ibus-1.2-karmic)
japaneseteam for tomoe packages, ppa has to be added as a jaunty repo: [https://launchpad.net/~japaneseteam/+archive/ppa](https://launchpad.net/~japaneseteam/+archive/ppa)

---

### Post by ilcontegis on 2009-10-05
thank you man!:popcorn:

---

### Post by oozzo on 2009-10-27
It seems weird that when I used 6.04 up until now I was able to easily manage my language support without having to f/ around too much. This is absurd, what was Canonical thinking?

---

### Post by bobince on 2009-10-27
(shrug)... I just installed ibus-anthy, then enabled it from System->Administration->Language Support and configured it to add anthy from the notification icon. Works fine for me, though I don't use dead keys (I much prefer the compose key).

It's still not really ideal that you have to have a separate daemon enabled from the not-really-obvious location of ‘language support’, rather than it all being in the Keyboard config UI. But it's not really difficult.

---

### Post by McDuff on 2009-10-28
is it possible to use more than four keyboard-layouts with i-bus?

---

### Post by ilcontegis on 2009-10-28
i think so...you just need to add it in the ibus options

---

