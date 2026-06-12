---
title: "Amarok Project Neon Problems"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by koolcracker on 2008-10-06
Okay, so trying to install Amarok 2 Beta 2, but when I try to install certain packages, i get an error message liek this:

amarok-nightly-strigi:
  Depends: amarok-nightly-kdesupport (=20080811+svn845176-0neon1) but 20081006.1+svn868387-0neon2 is to be installed

and I am getting the idea that I need to install that version of KDE support, but I don't know where to find it. Any help on isntalling amarok, maybe an alternate method, or a solution tot his problem would be great.

---

### Post by koolcracker on 2008-10-06
Okay, im not positive if I need those packages at all, im confused, but I am hoping that someone can point me in the right direction if I post the terminal output. this is just all the good stuff from the bottom haha, thanks. I would really like to get this up and running, I had the the first beta installed fine on my computer, and then I had a problem, reinstalled hardy from scratch, and now neither of them will install.

```
- "Creative Technology Ltd Creative Xmod (USB Audio)" 1 ("/dev/dsp1") index: 0 preference: 25 avail: true advanced: false  )
amarok(8472)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/home/graeme/.amarok-nightly/var/tmp/kdecache-graeme/ksycoca4"
amarok(8472)/kdecore (KLibLoader) kde4Factory: The library "" does not offer a qt_plugin_instance function.
amarok(8472)/kdecore (KLibLoader) kde3Factory: The library "" does not offer an "init_phonon_xine" function.
setting xine verbosity to 0 
Using Xine version  1.1.11.1 
amarok(8472) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
isEmpty 
outputPlugin:  pulseaudio 
outputPlugin:  alsa 
outputPlugin:  oss 
outputPlugin:  file 
outputPlugin:  none 
10000 "PulseAudio" "pulseaudio" 
Phonon::Xine::Backend(0x7973a0) 1 
Phonon::Xine::MediaObject(0x6f00d0) -> Phonon::Xine::AudioOutput(0x6f04a0) 
################################ Event:  TransitionTypeChanged 
################################ Event:  SetTickInterval 
################################ Event:  SetPrefinishMark 
0x88cc40 -> AudioOutput(0x6f0460) 
----------------------------------------------- audio_port created 
stored audio port is invalid 

UpdateVolumeEvent 
################################ Event:  UpdateVolume 
XineThread Rewire event: 
      MediaObject(0x88cc40)  ->  AudioOutput(0x6f0460) 
################################ Event:  SetTickInterval 
################################ Event:  SetPrefinishMark 
QObject::connect: Cannot connect (null)::rowsInserted( const QModelIndex&, int, int ) to Playlist::RowList::rowsInserted( const QModelIndex &, int, int )
QObject::connect: Cannot connect (null)::rowsRemoved( const QModelIndex&, int, int ) to Playlist::RowList::rowsRemoved( const QModelIndex&, int, int )
QObject::connect: Cannot connect (null)::rowMoved( int, int ) to Playlist::RowList::rowMoved( int, int )
QCoreApplication::postEvent: Unexpected null receiver
ASSERT: "!kaction->isGlobalShortcutEnabled()" in file /build/buildd/amarok-nightly-kdelibs-20081006.1+svn868387/kdeui/actions/kactioncollection.cpp, line 242
<unknown program name>(8471)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

graeme@graeme-laptop:~/amarok/src/context/build$ KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = amarok path = <unknown> pid = 8472
sock_file=/home/graeme/.amarok-nightly/socket-graeme-laptop/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
KCrash failed to exec(), errno = 2
```


Thanks alot to anyone who would be willing to give this a shot.

---

### Post by patchoro on 2008-10-07
Since last update same error here.

---

### Post by Gooler on 2008-10-08
And yet another one with this same problem...

---

### Post by cwk on 2008-10-08
I'm also having this issue. Any solutions?

---

### Post by fdmarco3 on 2008-10-09
I have this problem too in intrepid ibex kubuntu both with kde4 from repo and trunk kde4.

> setting xine verbosity to 0
<unknown program name>(3825)/: Communication problem with  "amarok" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

myuser@myuser-desktop:~$ KCrash: Application 'amarok' crashing...
sock_file=/home/myuser/.kde4/socket-myuser-desktop/kdeinit4__0

:confused:

---

### Post by jackhynes on 2008-10-09
Another one with the same problem. Using Ubuntu Intrepid.

---

### Post by r!ots on 2008-10-10
Exactly the same problem here on a fresh ubuntu 8.04 amd64 install. Any solution yet?

---

### Post by Gooler on 2008-10-14
I've upgraded today & installed a new packet called amarok-nightly-mysql-data. Now Amarok works again.

---

### Post by fdmarco3 on 2008-10-16
for me the problem is there even after the upgrades...:confused:

---

### Post by Warbo on 2008-10-23
There may have been an issue with Amarok 2 itself (since it works for me now I assume its been fixed), but there is no 'problem' with uninstallable packages.

Packages like kde-nightly-strigi are out of date (last updated sometime in August), since they have been merged into the other packages. For instance, strigi is now in kde-nightly-kdesupport. Those packages which won't install should not be installed anyway (I don't know why they're still in the repository)

---

### Post by krlhc8 on 2008-10-24
Here's what worked for me on Intrepid (GNOME) as an APT source line: 

[http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

Once installed, I didn't get a fancy menu item, but the command for a terminal is simply ```
amarok-nightly
``` (FYI).

---

### Post by KhaaL on 2009-02-09
> **krlhc8 said:**
> Here's what worked for me on Intrepid (GNOME) as an APT source line: 

[http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

Once installed, I didn't get a fancy menu item, but the command for a terminal is simply ```
amarok-nightly
``` (FYI).

I have that exact repo and also use the same command to start amarok-nightly, still it dosent like to play along with pulseaudio...

---

