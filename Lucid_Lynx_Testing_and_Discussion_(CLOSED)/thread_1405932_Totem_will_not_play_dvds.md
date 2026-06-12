---
title: "Totem will not play dvds"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jenkins1 on 2010-02-13
I am writing the totem section for the ubuntu-manual project but can't get a DVD to play in Totem. I can't use the menus, therefore can't start the DVD.

When I install Ubuntu 10.04 I install vlc, ubuntu-restricted-extras,
libdvdread4, and ran
```
sudo /usr/share/doc/libdvdread4/install-css.sh
``` 
The same DVD plays in vlc and xine. 

I have google searched and most posts say install vlc or mplayer.

I really need to for totem to work as I need to know what specific packages people need to install. I think this may be a bug as doing the same thing in karmic means dvds run fine.

Can anyone else play DVD's?

---

### Post by mc4man on 2010-02-13
I would say technically all totem needs to have dvd playback enabled is 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

followed by the css.sh you've noted.

Atm on my lucid installs (2), it isn't playing any comm. dvd's - freezes on the menu, and barely plays non menu dvd's (movie only burns

On it's best day totem's (gstreamer) dvd playback is remedial at best - poor to no support for picking alt. audio/sub streams, poor navigation, ect.

(somewhat surprising considering other players like vlc and totem-xine have had dvd nav and stream selection for a long time and both work quite well in lucid.

---

### Post by Jenkins1 on 2010-02-13
> **mc4man said:**
> I would say technically all totem needs to have dvd playback enabled is 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

followed by the css.sh you've noted.

Atm on my lucid installs (2), it isn't playing any comm. dvd's - freezes on the menu, and barely plays non menu dvd's (movie only burns

On it's best day totem's (gstreamer) dvd playback is remedial at best - poor to no support for picking alt. audio/sub streams, poor navigation, ect.

(somewhat surprising considering other players like vlc and totem-xine have had dvd nav and stream selection for a long time and both work quite well in lucid.


Cool thanks for that. After a chat on irc there is now a bug filled [https://bugs.launchpad.net/bugs/521482](https://bugs.launchpad.net/bugs/521482) here for this error.

---

### Post by mc4man on 2010-02-13
> there is now a bug filled....

That is pretty much what I see here - added an affects me too, ect.

---

### Post by ranch hand on 2010-02-13
I believe that it will play if you;
```
[FONT=monospace]
[/FONT]sudo apt-get install libdvdcss2

```

---

### Post by Yellow Pasque on 2010-02-13
^I'm assuming the OP already installed that with the css.sh script

> ..other players like vlc and totem-xine..
totem-xine development is dead, and installing the package in Karmic or Lucid just gets the gstreamer version.

> On it's best day totem's (gstreamer) dvd playback is remedial at best
It's been improving. On Karmic with the latest gstreamer packages (from PPA), it's finally handling some of my DVD's with menus properly.

---

### Post by ranch hand on 2010-02-13
I have had occasional problems with that script for some reason.  It does install but it is not "seen" by totem.

---

### Post by mc4man on 2010-02-13
> .. installing the package in Karmic or Lucid just gets the gstreamer version.

True

> totem-xine development is dead,
While dev is finished it still is a very good player for local and streaming media. (far superior to totem-gstreamer in that regard.

Very easy to set up as a standalone media app in karmic and lucid

[http://ubuntuforums.org/showthread.php?t=1388367](http://ubuntuforums.org/showthread.php?t=1388367)

---

