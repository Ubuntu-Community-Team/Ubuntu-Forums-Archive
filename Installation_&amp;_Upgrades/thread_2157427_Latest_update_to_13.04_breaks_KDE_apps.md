---
title: "Latest update to 13.04 breaks KDE apps"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by zenkaon on 2013-06-25
Hello,

I've just updated ubuntu 13.04 to the latest software update and my KDE apps no longer open.
For example:
```

 kdevelop
WARNING: deleting stale lockfile /home/john/.kde/share/apps/kdevelop/sessions//{bb9db3c9-4f9e-4412-ad8f-c0dc5a590142}/lock
WARNING: deleting stale lockfile /home/john/.kdevduchain/{bb9db3c9-4f9e-4412-ad8f-c0dc5a590142}/0/lock
kdevelop(3388)/kdevplatform (language) KDevelop::ItemRepositoryRegistry::open: version-hint not found, seems to be an old version 
kdevelop(3388)/kdevplatform (language) KDevelop::ItemRepositoryRegistry::open: "The data-repository at /home/john/.kdevduchain/{bb9db3c9-4f9e-4412-ad8f-c0dc5a590142}/0 has to be cleared." 
void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "F&ull Screen Mode" under id 81 
kdevelop(3388)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
qrc:/main.qml:23:1: QML QDeclarativeRectangle_QML_0: Binding loop detected for property "areaName"
static bool QDeclarativeMetaType::isModule(const QByteArray&, int, int) Qt 4.7 import detected; please note that Qt 4.7 is directly reusable as QtQuick 1.x with no code changes. Continuing, but startup time will be slower. 
QDeclarativeComponent(0x2ef8ea0)
QDeclarativeComponent(0x2ef8ea0)
kdevelop(3388)/konsole Konsole::Session::run: Attempted to re-run an already running session. 
The program 'kdevelop' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1496 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
kdevelop(3388)/konsole Konsole::SessionManager::~SessionManager: Konsole SessionManager destroyed with sessions still alive 

```

or:
```

amarok
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
amarok(3505)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3505)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3505)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::insertAction: Attempt to insert null action
amarok(3505)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
john@heplt025:~$ QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.127'
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (66,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (66,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (110,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (110,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (206,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (206,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (146,-1) are not possible
The program 'amarok' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 2017 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Does anyone know how to fix this?
I use KDevelop for work. This is quite serious for me, I'm back to using emacs

John

---

### Post by SeijiSensei on 2013-06-25
Try adding the [Kubuntu PPA]("https://launchpad.net/~kubuntu-ppa/+archive/ppa") and see it that helps.  I encountered some versioning conflicts after updating the other day which were resolved by adding the PPA.  I had to run "sudo apt-get upgrade" a couple of times to get all the dependencies ironed out.

---

### Post by zenkaon on 2013-06-25
Hi,

I got the following updates when adding the kubuntu ppa:
```

amarok amarok-common amarok-doc amarok-utils libsoprano4 soprano-daemon

```

This has fixed amarok, but KDevelop is still broken.

To be honest I don't really care about amarok so much, KDevelop is very important to my workflow.

---

### Post by IOFeed on 2013-07-03
The same problem here... 
Completely reinstalled kdevelop from source and no luck :\
Any ideas?

btw, found a thread in launchpad for this... [https://bugs.launchpad.net/ubuntu/+source/kdevelop/+bug/1178843?comments=all](https://bugs.launchpad.net/ubuntu/+source/kdevelop/+bug/1178843?comments=all)

---

### Post by Tazza101 on 2013-07-03
I have the same problem but just with amarok, I don't have kdevelop installed, but I have a VERY LARGE and meticulously tagged amarok library, I've spent so many hours working on that...
Unfortunately adding the kde-backports repo didn't fix amarok for me! I still get
```
francesco@algernon53:~$ amarokQDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
amarok(9014)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(9014)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(9014)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::insertAction: Attempt to insert null action
amarok(9014)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
francesco@algernon53:~$ The program 'amarok' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 3099 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```


I actually had this problem with an update from 'raring-proposed', but I reverted the updates and removed that repo, it wouldn't be nice to remove 'raring-updates' though!

---

### Post by D@NO on 2013-07-07
I'm affected too, but as a quick workaround I'm able to run kdevelop with KDE interface.

---

### Post by nilsolaris on 2013-07-13
Is this bug ever going to get resolved ?

---

### Post by nike984 on 2013-07-14
I think this bug is similar to 
[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/1195007](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/1195007)

This has been fixed in ubuntu proposed repository

If you are currently using kubuntu ppa, ppa-purge it then the patch will work. 

In my case, I had **ppa:kubuntu-ppa/backports**[COLOR=#333333][FONT=Ubuntu] and [/FONT][/COLOR][B]ppa:kubuntu-ppa/ppa,
[/B]so I did

```
sudo ppa-purge ppa:kubuntu-ppa/ppa
sudo ppa-purge ppa:kubuntu-ppa/backports
```

Now, the kde apps work flowlessly in my case.

---

