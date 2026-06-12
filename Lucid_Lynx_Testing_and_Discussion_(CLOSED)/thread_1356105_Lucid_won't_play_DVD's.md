---
title: "Lucid won't play DVD's"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by meeples on 2009-12-15
Totem and VLC close as soon as they open when i try to play a dvd.

is it just me?

---

### Post by mc4man on 2009-12-15
One of the main causes of immediately closing is an issue with the video output (though in an alpha could be others

For vlc try changing the default output (Xv) to x11 in tools -> preferences -> video. (in the output dropdown

Or for a quick test and some debugging (only if on the default drive - sr0

```
vlc -vv --vout x11 dvd://
```

or a variation ( doesn't use the qt interface 

```
cvlc -vv --vout x11 dvd://
```

vlc should also be using the pulseeaudio output

---

### Post by ranch hand on 2009-12-15
VLC works fine for me.

---

### Post by cariboo on 2009-12-15
I just tried playing a DVD and it worked as it should. Make sure you have libdvdcss2 installed, either by running the script in /usr/share/doc/libdvdread4, or installing it from the Medibuntu repositories.

---

### Post by VMC on 2009-12-15
> **meeples said:**
> Totem and VLC close as soon as they open when i try to play a dvd.

is it just me?

I couldn't play DVD's either. I don't have VLC installed, but I followed these [instructions]("http://ubuntuforums.org/showpost.php?p=4790346&postcount=1") and now I can.

---

