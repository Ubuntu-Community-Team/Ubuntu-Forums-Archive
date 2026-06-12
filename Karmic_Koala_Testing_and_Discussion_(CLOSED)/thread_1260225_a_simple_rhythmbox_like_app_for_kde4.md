---
title: "a simple rhythmbox like app for kde4?"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-09-07
Simple as is there a kde based app that is similair to rhythmbox available for karmic?

I hate playlist orientated players so amarok does my head in, i just want a simple one like rhythmbox any ideas, i've tried google searching but can't find anything similair.

---

### Post by taavikko on 2009-09-07
Not really answering to your question but, whilst using amarok
I've loaded the entire library as a single playlist...

Though starting the app takes then forever :D
~12k songs

Now for the answering part, what stops you installing RB in KDE?
heavy depends would be the obvious answer to that one...

---

### Post by Whiffle on 2009-09-07
Try JuK

---

### Post by ELD on 2009-09-07
> **Whiffle said:**
> Try JuK

KPackageKit cannot find any "JuK" package, i looked online and it seems it's only for kde3.4?

---

### Post by taavikko on 2009-09-07
> **ELD said:**
> KPackageKit cannot find any "JuK" package, i looked online and it seems it's only for kde3.4?

It's "juk"

```
aptitude show juk
Package: juk
State: not installed
Version: 4:4.3.1-0ubuntu1
Priority: optional
Section: kde
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 1737k
Depends: kdebase-runtime (>= 4:4.3.0), kdelibs5 (>= 4:4.3.1), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1),
         libqt4-dbus (>= 4.5.1), libqt4-phonon (>= 4.5.1), libqt4-qt3support (>= 4.5.1), libqt4-xml (>=
         4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libstdc++6 (>= 4.1.1), libtag-extras0 (>=
         0.1.1), libtag1c2a (>= 1.5), libtunepimp5
Suggests: k3b
Conflicts: juk-kde4
Replaces: juk-kde4
Description: music jukebox for KDE 4
 JuK is a powerful music player capable of managing a large music collection.

 Some of JuK's features include:
 * Music collection, playlists, and smart playlists
 * Tag editing support, including the ability to edit multiple files at once
 * Tag-based music file organization and renaming
 * Automatic tagging using MusicBrainz
 * CD burning support using k3b
 * Album art using Google Image Search

 This package is part of the KDE 4 multimedia module.
Homepage: http://www.kde.org/

```

---

### Post by Whiffle on 2009-09-07
Hmm I have it under kde 4.2, and i searched in aptitude and its available there.


I however do not like it, because apparently at this version, it has crossfade between tracks that can't be turned off.

---

### Post by ELD on 2009-09-07
Ah right got it now, this should do nicely :)

---

### Post by VMC on 2009-09-07
On another kde4.3 distro I have all three installed with the system. RB is the only one that works correctly. juk and amarok fail miserably. 

I'm surprised that kubuntu didn't include RB.

---

### Post by PC_load_letter on 2009-09-07
I'm not familiar with Rhythmbox since I use Amarok 1.4 on Gnome. I would recommend 'Songbird'. Fantastic music player that integrates well with KDE or Gnome, and the web surfing component of it is great in retrieving band info and pics. It's iTunes-like player.

The latest version of Songbird features a decent equalizer, do they have that in Amarok 2.0 yet?

---

### Post by seeker5528 on 2009-09-10
No equalizer in Amarok 2 for the foreseeable future.

A: Doesn't seem very high in the list of priorities of things the developers see as something Amarok needs, there are still a lot of other things to be done.

B: Seems it is a non-starter at the moment anyway.... >  we simply can't make an equalizer if the underlying sound architecture doesn't give us the means to do so. We are not the ones to address to for that task, go ask the Phonon and more especially the Xine people to provide the structure for it.

 [http://forum.kde.org/viewtopic.php?f=116&t=73701&start=30#p122530](http://forum.kde.org/viewtopic.php?f=116&t=73701&start=30#p122530)

Later, Seeker

---

### Post by xebian on 2009-09-10
> **seeker5528 said:**
> No equalizer in Amarok 2 for the foreseeable future.

A: Doesn't seem very high in the list of priorities of things the developers see as something Amarok needs, there are still a lot of other things to be done.

B: Seems it is a non-starter at the moment anyway.... 

 [http://forum.kde.org/viewtopic.php?f=116&t=73701&start=30#p122530](http://forum.kde.org/viewtopic.php?f=116&t=73701&start=30#p122530)

Later, Seeker

But it looks like a work in progress.  If you try the 2.2 (2.1.98) beta it has an equalizer but greyed out because presumably phonon does not support it disclaimer.

Still the 2.2 beta code name "crystal clear" sound is much improved and I personally don't think it needs one.

---

### Post by xebian on 2009-09-10
> **VMC said:**
> On another kde4.3 distro I have all three installed with the system. RB is the only one that works correctly. juk and amarok fail miserably. 

I'm surprised that kubuntu didn't include RB.

RB is not a KDE apps that's why but you can install it if you want.  But it doesn't even come close to what Amarok is IMHO.

---

### Post by seeker5528 on 2009-09-10
> **xebian said:**
> But it looks like a work in progress.  If you try the 2.2 (2.1.98) beta it has an equalizer but greyed out because presumably phonon does not support it disclaimer.

I didn't see that in there but I wasn't looking and if it's not functional and not expected to be functional for a while, the packages in Debian experimental were probably built without it.

Somebody did mention in the Amarok forum that they thought Gstreamer had EQ stuff in it, so maybe it's not far out after all, depending on the back end you use.

I'm kind of annoyed by the fact that phonon-gstreamer has replay gain support, but xine-phonon doesn't and while I did prefer the gstreamer-backend with Amarok 1.4 the phonon-gstreamer backend so far has some issues with spaces in the name that prevent me from using it, had some additional issues with video in dragon player when using phonon-gstreamer as well. I think there has been a few QT updates since the last time I tried it, so don't know how much of these issues may have been fixed.

Later, Seeker

---

