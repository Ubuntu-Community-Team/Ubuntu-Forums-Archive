---
title: "Nautilus crashing on Edit - Preferences..."
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-09-01
I just did a fresh install of Alpha 4 to address an app issue I had and I now find that if I try to launch Nautilus and choose Edit - Preferences, it crashes.  Anyone else seen this?

---

### Post by bl33d on 2009-09-01
Yea

---

### Post by mariner09 on 2009-09-01
Well, is there anyway to modify settings like icon size?  I looked through gconf and it wasn't obvious.

---

### Post by pulpo69 on 2009-09-01
Nautilus crashing on Edit - Preferences...I can confirm this.

---

### Post by bl33d on 2009-09-01
> **mariner09 said:**
> Well, is there anyway to modify settings like icon size?  I looked through gconf and it wasn't obvious.

Don't know sorry. I have never had problems with Edit -> Preferences in Gnome before.

---

### Post by taavikko on 2009-09-01
```
[ 1337.619474] nautilus[3843]: segfault at 8 ip 000000000043cc84 sp 00007fff8ba0de20 error 4 in nautilus[400000+1ae000]
```

Affected as well.
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/422282](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/422282)

---

### Post by miegiel on 2009-09-01
> **taavikko said:**
> ```
[ 1337.619474] nautilus[3843]: segfault at 8 ip 000000000043cc84 sp 00007fff8ba0de20 error 4 in nautilus[400000+1ae000]
```

Affected as well.
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/422282](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/422282)

Thx for the bug report link. Got a slightly different output from *tail /var/log/messages* here
```
kernel: [  964.125089] nautilus[3330]: segfault at 4 ip 0807a21f sp bff64820 error 4 in nautilus[8048000+1bf000]
```

---

### Post by zoomy942 on 2009-09-01
gah.  this bug got me too.

---

### Post by VMC on 2009-09-01
I'm affected too but get nothing from messages:
```
grep nautilus /var/log/messages

```
I'll check in on the bug report:
[422282]("https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/422282")

---

### Post by Darkshade on 2009-09-01
Finally something! It's been ages (or felt like it) since something broke on my system for the last time.
Breakage <3 :D

---

### Post by berthiggins on 2009-09-01
Yeah I have the same bug.

---

### Post by steeleyuk on 2009-09-02
This bug should be fixed for everyone now with the latest updates...

---

### Post by kansasnoob on 2009-09-02
> **steeleyuk said:**
> This bug should be fixed for everyone now with the latest updates...

Errrm, still can't open nautilus with admin privileges:

> lance@lance-desktop:~$ gksudo nautilus
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 

** (nautilus:3670): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3670): WARNING **: No marshaller for signature of signal 'DownloadFinished'


That's after the updates and a reboot.

---

### Post by gwenn on 2009-09-02
Same bug for me too.

---

### Post by taavikko on 2009-09-02
> **kansasnoob said:**
> Errrm, still can't open nautilus with admin privileges:


Different bug: [https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841)

---

### Post by drs305 on 2009-09-02
> **mariner09 said:**
> Well, is there anyway to modify settings like icon size?  I looked through gconf and it wasn't obvious.

You can change the nautilus icon sizes via gconf-editor. The command is for icon view but list view is near it. Sizes are smallest, smaller, small, standard, large, larger, largest. To reset to the default, right click, "Unset key".

```

gconf-editor /apps/nautilus/icon_view/default_zoom_level

```

In nautilus there is also a size % window toward the upper right above the main panel or via the View, Zoom In menu (CTRL+ +).

---

### Post by kansasnoob on 2009-09-02
> **taavikko said:**
> Different bug: [https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841)

Thanks, I can confirm that removing brasero and libbrasero-media0 (which also removes rhythmbox) does allow gksudo nautilus to work properly.

---

### Post by kansasnoob on 2009-09-02
Definitely a bug in brasero 2.27.91-0. I installed (and locked) 2.26.0-0:

[http://packages.ubuntu.com/jaunty/i386/brasero/download](http://packages.ubuntu.com/jaunty/i386/brasero/download)

with the installed versions of libbrasero-media0 and rhythmbox and gksudo nautilus runs fine.

EDIT: that appears to be true only until I start Brasero again, so I'm wrong, just downgrading brasero doesn't work!

---

### Post by exploder on 2009-09-02
Todays updates seemed to have cured the bug with Nautilus as root and the preferences bug.

---

### Post by kansasnoob on 2009-09-02
> **exploder said:**
> Todays updates seemed to have cured the bug with Nautilus as root and the preferences bug.

Not here. I've done a bit more playing and nautilus opens as root OK after downgrading both brasero and libbrasero-media0 to the Jaunty versions. Of course that's no "fix" nor even a decent workaround because it also requires a downgrade of rhythmbox and the Jaunty version crashes.

Anyway they have it "tagged" right as being a bug in brasero (maybe more specifically libbrasero-media0).

---

### Post by kansasnoob on 2009-09-02
taavikko, thanks for the info.

I added some info to the bug report and subscribed.

I have faith it'll be fixed by beta!

---

### Post by mariner09 on 2009-09-03
FWIW, the nautilus updates fixed the issue I had...

---

