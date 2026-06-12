---
title: "Rhythmbox seems to have disapeared, had to reinstall alsa mixer"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-05-18
I just updated with todays updates.  Seems like everything works alright except that Rhythmbox does not play.

That is to say it seems to be playing but nothing comes out of the speakers.  I was able to add a new folder of music to it with no problem.  It looks fine.

When checking the mixer all I got was the pulse audio mixer was using alsa yesterday.

Went to synaptic and found that the alsa mixer was not installed.  Installed it.

Ran a search for Rhythmbox and the only thing that came up was potamus.  Installed that and it plays so the sound card and alsa are working.

WTF happened to Rhythmbox?

---

### Post by ranch hand on 2009-05-18
Rebooted to see what would happen.

Would not boot, stalled on loading the bluetooth stuff.  Have no idea about that, have no such devices.

Booted fine when going through recovery.

No effect on rhythmbox, still not there for playing anything.

---

### Post by ranch hand on 2009-05-20
Still can't get rhythmbox to feed to my card.  Movie Player works fine.

Rhythbox should be in synaptic, apt-get finds it.

Have no idea what to try.  Rhythmbox is still not listed in synaptic.

Removed Rythmbox with apt-get and reinstalled same way.  No change.

Removed synaptic with apt-get and reinstalled it and update-manager.  Synaptic now does find rhythmbox.

---

### Post by ranch hand on 2009-05-21
Tried installing all restricted audio stuff, no change.

---

### Post by freeman2000 on 2009-05-21
Is Rhythmbox the only app lacking sound?  Can you get sound from last.fm on Firefox?  Or from any of the other "players" on your system?  I don't know if this helps, but in the pre-alpha stage I didn't have any problems, but once Alpha 1 downloaded, I would lose all sound whenever I came out of KDE and went back into gnome.  Something was "muting" my sound card.  Once I got into gnome, I would have to recheck all sound levels, and also click on the "speaker" icon on my laptop to turn the sound back on.  Then I had to do a restart to actually get the sound back.  An update a few days ago seems to have taken care of this for me.  Good luck.

---

### Post by ranch hand on 2009-05-21
Yes I have sound Movie Player plays the ogg files just fine.  If I go to the music folder and cursor over the file it starts to play.

Rhythmbox seems to be the only problem.  It does not make much sense to me but I will continue to check it daily.

I have never tried an alpha before and find it rateher interesting.  Right now I am on a Jaunty-64 partition.  A real nice OS.

---

### Post by jmmL on 2009-05-21
Have you tried starting rhythmbox from a terminal to see if it throws any obvious errors?

Also, I've recently had problems with pulseaudio on startup, so sometimes I have to run```

killall pulseaudio
pulseaudio --start
```
before I can get any sound out.

---

### Post by ranch hand on 2009-05-21
You know, sometimes I really am simple.  I prefer to use apt-get for the info I get.  I have used the terminal to start apts.  But did I try it here?  No.

So I popped over to this (Kinky Kitty) partition and gave it a whack.
```

ker@ubuntu:~$ rhythmbox

(rhythmbox:4600): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11

```
Opened another terminal and tried
```

killall pulseaudio

```
reopened rhythmbox and got the smae error but also got a static noise when I hit play.
Ran
```

pulseaudio --start

```
restarted rhythmbox w/same error and no static.

Pulse Audio may be part of the problem.  The main problem I am having right now is that I really don't understand the error message.

I think I need to do some studying on that.

Thanks, you may have pointed me where I need to go.

---

### Post by dagrump on 2009-05-21
You might take a look at the #8 post in the "distorted audio playback" thread fixed the static & skipping for me.

---

### Post by ranch hand on 2009-05-21
dagrump
I never got that far.  I found the thread and it was number 3 on my list of things to try.

What actually worked was following part C on

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It was kind of interesting.  It appears that Kinky Kitty (and yes I think the next one should be Lumpy Lama) believed that "libsdl1.2debian-alsa" was installed.

When I went to
```

ker@ubuntu:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

```
I got
```

The following packages will be REMOVED:
  libsdl1.2debian-alsa

```
Which became interesting when apt-get got to the removal of said package
```

dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu3) | libsdl1.2debian-all (= 1.2.13-4ubuntu3) | libsdl1.2debian-esd (= 1.2.13-4ubuntu3) | libsdl1.2debian-oss (= 1.2.13-4ubuntu3) | libsdl1.2debian-nas (= 1.2.13-4ubuntu3) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu3); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.

```
All that was neccesary then was to fine tune the alsa mixer to the sound I wanted through rhythmbox.

Why the sound worked with Movie Plyer and Potamus but not Rhytmbox is still a mystery to me but it is all working now.

Thanks to all who had suggestions, they pointed me in directions I would not have gone on my own.

---

