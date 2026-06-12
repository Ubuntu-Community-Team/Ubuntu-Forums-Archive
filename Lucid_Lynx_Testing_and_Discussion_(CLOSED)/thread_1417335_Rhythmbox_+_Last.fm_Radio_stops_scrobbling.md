---
title: "Rhythmbox + Last.fm Radio stops scrobbling"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-02-27
I use Rhythmbox and Last.fm regularly, but I normally scrobble locally stored music.

After listening to the "Personal Radio" and "Neighbour Radio" channels in Rhythmbox I realized that only the first one or two songs would successfully scrobble. The Last.fm channel continues to play, but scrobbling stops.

Can anyone confirm this? Also, is it new to Ubuntu 10.04?

---

### Post by Jaymac on 2010-04-23
Can confirm this affects me too - and worked perfectly in 9.10.

---

### Post by null_pointer_us on 2010-04-23
EDIT:

Sorry, didn't realize this was specific to Rhythmbox integration with Last.fm.

Q. How do you test whether tracks are being scrobbled?

A. Rhythymbox -> Edit -> Plugins -> Last.fm -> Configure

This configuration window shows successful status for scrobbling first track, but clicking the Configure button again after playing additional tracks does nothing. No dialog, no error. Also, the tracks do not show up in my Last.fm history in the browser. I suppose this is related?

```
$ apt-cache policy rhythmbox-plugins
rhythmbox-plugins:
  Installed: 0.12.8-0ubuntu3
  Candidate: 0.12.8-0ubuntu3
  Version table:
 *** 0.12.8-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```

Browsing through some unrelated launchpad bug reports for rhythmbox+last.fm, one of the developers asked for the output of the following command. Maybe it will give some more information?

```
rhythmbox -D lastfm &> rhythmbox-debug.txt
```

I'm trying this now... Nope, it shows the same line for every file whether scrobbled or not:

```
(08:50:45) [0xd89040] [process_queue] rb-lastfm-source.c:1486: request queue is empty

```

Only the timestamp changes.

-----------------

ORIGINAL (separate bug):

Last.fm is broken for me.

[LIST]
[*]Ubuntu 10.04 RC (amd64)
[*]Firefox 3.6.3
[*]32-bit Flash 10.0 r45[/LIST]

Occasional Symptoms:

[LIST]
[*]Frequent timeouts.
[*]Buffering message "sticks" until page is reloaded.
[*]Songs fail to play.
[*]Comments will not load.
[*]Favorites will not stick.
[*]Last.fm occasionally reports that it is an unsupported platform.[/LIST]

Is everyone else who experiences this problem on the amd64?

I'm guessing this is Yet Another AMD64 Flash Problem (YAAFP).

---

### Post by null_pointer_us on 2010-04-23
Something noticed:

Clicking the Skip or Ban buttons seems to make scrobbling work fine on the next song.

Clicking the Loved button seems to make the song show up on last.fm profile details as a favorite regardless of whether Rhythmbox properly adds it to the list of recently played songs.

:confused:

---

