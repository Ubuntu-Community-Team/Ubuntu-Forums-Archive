---
title: "No window manager?"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by ChrisOfBristol on 2012-06-28
I've just installed 12.04 after trying a couple of other distributions. 

I have no window borders, header bar or buttons, note even a menu. I know that I can get some things to work for the duration of the login by typing alt-F2 then:

```
metacity --replace &
``` or ```
compiz --replace &
```

I think there is some problem with some preferences somewhere which mean that no window manager starts.

I have had this problem before on other distributions and was told to delete loads of my directories related to Gnome in the hope of deleting the relevant setting, but it didn't work. 

It might be possible to fix it by taking a backup, formatting the disk and then replacing my data but I wouldn't be prepared to take that drastic a step. 

I think that what I need to know is how to define which window manager or desktop manager or some combination of the two loads at login or startup.

---

### Post by matt_symes on 2012-06-28
Hi

Are you using the Unity-2D session or the standard Unity3D session ?

Kind regards

---

### Post by ChrisOfBristol on 2012-06-28
> **matt_symes said:**
> Are you using the Unity-2D session or the standard Unity3D session ?

If I use Unity I get nothing on the desktop, no launcher strip down the side whatever I do.

If I use Unity-2D I get a top panel, if I press the left-Window$ key I get the Dash.

---

### Post by matt_symes on 2012-06-29
Hi

Can you post the output of 

```
cat /usr/share/gnome-session/sessions/ubuntu-2d.session
```

Kind regards

---

### Post by ChrisOfBristol on 2012-06-29
chris@Asus:~$ cat /usr/share/gnome-session/sessions/ubuntu-2d.session
[GNOME Session]
Name=Ubuntu 2D
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;shell;
DefaultProvider-windowmanager=metacity
DefaultProvider-panel=unity-2d-panel
DefaultProvider-shell=unity-2d-shell

DesktopName=Unity
chris@Asus:~$

---

### Post by matt_symes on 2012-06-29
Hi

You having the problem in Gnome Shell and not Unity-2D (although Unity3D is also giving you problems)  ? 

It's in gnome shell where you are not seeing the window decorations ?

I'm rather confused. Can please highlight in which desktop environment you are having your main problem and the reason for this thread.

Kind regards

---

### Post by ChrisOfBristol on 2012-06-29
I have removed a comment from message 5 because it seems to have caused confusion.

As I said in message three, the problem occurs when I login to Unity or Unity-2D.

For the purpose of trying to fix Unity - so when I typed the "cat" command  for example - I login using Unity or Unity-2d, I do **NOT** use gnome-shell.

----------------------------------------------------------------------------------------------------------------------------------------------------------------
Until it's fixed, so that I can use the computer - to type this message for example - I have installed gnome-shell as well and I login to Gnome-Classic and type "metacity --replace &" whenever I actually want to *use* the computer.

---

### Post by matt_symes on 2012-07-01
Hi

Is there anything in the .xsession-errors log file that may highlight why metacity is not starting ?

After logging into Unity2D, open a terminal and type

```
grep -i "metacity" ~/.xsession-errors
```

Please do this before starting metacity using the --replace option. Please post the output back here.

If not, there maybe a workaround by adding ```
metacity --replace
``` as a startup item but this is a work around and not a fix.

Kind regards

---

### Post by ChrisOfBristol on 2012-07-01
> **matt_symes said:**
> Is there anything in the .xsession-errors log file that may highlight why metacity is not starting ?
There are lots of errors, including ones which mention Unity-2D.

```
gnome-session[5807]: WARNING: Could not parse desktop file /home/chris/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
gnome-session[5807]: WARNING: could not read /home/chris/.config/autostart/xfce4-settings-helper-autostart.desktop
gnome-session[5807]: WARNING: Could not parse desktop file /home/chris/.config/autostart/xfce4-tips-autostart.desktop: Key file does not have key 'Name'
gnome-session[5807]: WARNING: could not read /home/chris/.config/autostart/xfce4-tips-autostart.desktop
gnome-session[5807]: WARNING: Could not parse desktop file /home/chris/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[5807]: WARNING: could not read /home/chris/.config/autostart/xfconf-migration-4.6.desktop
gnome-session[5807]: WARNING: Could not parse desktop file /home/chris/.config/autostart/deja-dup-monitor.desktop: Key file does not have key 'Name'
gnome-session[5807]: WARNING: could not read /home/chris/.config/autostart/deja-dup-monitor.desktop
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

** (nautilus:5883): WARNING **: Can not get _NET_WORKAREA

** (nautilus:5883): WARNING **: Can not determine workarea, guessing at layout
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/thunderbird.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 

           ***Removed lots of hotkey statements***

unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by ChrisOfBristol on 2012-07-01
> **matt_symes said:**
> If not, there maybe a workaround by adding```
metacity --replace
``` as a startup item but this is a work around and not a fix.
This works fine for Gnome-shell but is no good for Unity as although some things come back it doesn't work properly.

---

### Post by matt_symes on 2012-07-02
Hi 

Can we check to see if it's your user settings.

Create a new user and login as that user. Do you still have the same problems ?
[FONT=monospace]
[/FONT]> Could not parse desktop file /home/chris/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name' 
gnome-session[5807]: WARNING: could not read /home/chris/.config/autostart/xfce4-settings-helper-autostart.desktopHave you had xfce installed on this install before ? I take it this is not a fresh install. 

What is the story behind this installation ? The problem could be in a whole number of places you see.

> This works fine for Gnome-shell but is no good for Unity as although some things come back it doesn't work properly.You keep mentioning gnome shell. Can we make sure we are singing from the same song sheet.

Unity      (aka Unity3D) - The standard Ubuntu Desktop that is the default DE on a fresh install.
Unity2D (aka gnome-fallback session) - The other option on a fresh install of Ubuntu when Unity will not run due to hardware.
Gnome shell - This must be installed from the repos. It is the default DE in Fedora and completely different from the two above.

For simpilicty it may be better to back up and reinstall as this is not a fresh installation.

Kind regards

---

### Post by ChrisOfBristol on 2012-07-03
> **matt_symes said:**
> Create a new user and login as that user.Everything's fine if I login as guest.
> Have you had xfce installed on this install before ?
I take it this is not a fresh install.
What is the story behind this installation ?
I have tried XFCE and other distributions on this computer in the past. When I installed Ubuntu 12.04 I had /home in a separate partition which I left untouched. The / and /swap partitions were formatted. 
> You keep mentioning gnome shell.I understand the differences between the three desktops you mention. I had to install gnome-shell in order to be able to use the computer to post these messages etc. I only mention it in case having it installed might be relevant. When I am attempting to get Unity to work I always logout then login again using the Unity-2D option.
> For simpilicty it may be better to back up and reinstall as this is not a fresh installation.As I explained in my first post I would not consider this as an option.

---

### Post by ChrisOfBristol on 2012-07-03
I took a chance and deleted the .desktop files mentioned in the first few rows of the .xsession-errors file since they referred to XFCE and deva-dup so I thought that they were probably redundant, and they were muddying the waters.

I then logged in again, the results were the same, but the .xsession-errors file is clearer as unity-2d is mentioned repeatedly:

```
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

** (nautilus:4116): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4116): WARNING **: Can not determine workarea, guessing at layout
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/thunderbird.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 

            *****I've removed the rest of the key statements*****

unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
```

---

### Post by ChrisOfBristol on 2012-07-03
Searching for anything relating to "Could not open device:  Virtual core pointer" in the first line in .xsession-errors listed above, I came across a reference to "xstartup" in the page linked to below. Is there anything like xstartup in Uubuntu and if so could there be something missing from that?

[http://forums.fedoraforum.org/showthread.php?t=201885]("http://forums.fedoraforum.org/showthread.php?t=201885")

---

### Post by ChrisOfBristol on 2012-07-05
A bit more experimentation - I've tried starting the different window managers with the different DEs:

Gnome....................just works
Gnome Classic.....requires "metacity --replace &" in Startup Applications

Unity.......................requires "compiz --replace &" in Startup Applications
Unity 2D.................requires "metacity --replace &" in Startup Applications and still only half works

---

