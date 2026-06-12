---
title: "Make Jack audio server work with realtime priorities on Karmic"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hzFVOW00pw on 2009-09-15
In Jaunty, it was necessary to deinstall pulseaudio, and to change your sound settings to use ALSA. This is not necessary in Karmic.

However, the Jack audio server needs some tweaking to make it work with realtime priorities in Karmic.

1: Make sure you have this line:

```
@audio - rtprio 99
```

in /etc/security/limits.conf

You can edit the file with:

```
sudo gedit /etc/security/limits.conf
```

2: Make sure you are a member of the audio system group:

```
sudo users-admin
```

Select your user account > Properties > User privileges > Use audio devices

Both steps will probably not be necessary if you install the ubuntustudio-audio metapackage:

```
sudo apt-get install ubuntustudio-audio
```

...however this will install a plethora of audio applications and you probably don't need all of them.

Further tweaking of your audio configuration can be done with ubuntustudio-controls:

```
sudo apt-get install ubuntustudio-controls

sudo ubuntustudio-controls

```

---

