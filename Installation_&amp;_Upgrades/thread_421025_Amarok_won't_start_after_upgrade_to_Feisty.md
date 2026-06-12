---
title: "Amarok won't start after upgrade to Feisty"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by oudalrich on 2007-04-24
I upgraded to Feisty four days ago, and all in all it was less painful than expected. One of the few things that remain to be fixed is Amarok. When I start it from a terminal window, I get the following output:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80967b8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80967b8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty

```

Any ideas what's going wrong there? Sorry if this is a dumb question, I've only switched from Windows a few weeks ago.

---

### Post by oudalrich on 2007-04-30
Bump. I have tried purging and re-installing the amarok package through aptitude, but nothing changes. I get the same errors. The amarok and amarokapp processes are started, but nothing further happens. Does nobody have an idea what I can do?

---

### Post by oudalrich on 2007-04-30
I have changed the permissions on /etc/qt3/qt_plugins_3.3rc and now the errors relating to it are gone, but the others are still there -- and still no luck starting Amarok.

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096580 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096580 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

```

---

### Post by oudalrich on 2007-04-30
Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=212025"), I got rid of most of the error messages. What I get now is this:

```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80965a8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80965a8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

```

But still no Amarok!

---

### Post by oudalrich on 2007-04-30
Was a sound-related problem. This did the trick:

```
asoundconf reset-default-card
```

---

### Post by been on 2007-08-12
same problem... i tried to reset the default sound card too, but nothing happens... kopete isn't working too. all this trouble started when I was configuring the sound gear in amarok, then it crashed.

that's what I receive when I run amarokapp on terminal:

kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82758b0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82758b0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

one last thing: I have 2 sound cards here, but it never was a problem

---

