---
title: "No media files can be played."
date: 2009-05-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flipmatthew on 2009-05-08
For some reason I cannot play any MEDIA files. That includes ogg's, which I thought were natively supported. I've installed so many codes and I still  cant get it to work. However, I do have sound and I can listen and watch videos on youtube. I've also tried to install different media players, restricted extras etc. Im running Kernel 2.6.30 rc4. please help.

---

### Post by Nullack on 2009-05-08
Perhaps a good place to start would be the debugging section of the ubuntu wiki.

---

### Post by taavikko on 2009-05-09
I'll get the feeling that you've done too much and that's b0rked your settings.
After initial install, when you try to play multimedia content, gnome-app-install
will kick in and asks you to install missing codecs.

Somethings like w{32,64}codecs are obsolete, since mplayer is only one that knows to play them natively. totem needs gst-pitfdll package to do so, which doesn't get installed by default only by accident ;)

Now for the debugging,
Add new user and test if things work with that account
```
sudo adduser test
```
follow the prompts and then logout and back in with that new user.

Try using like mplayer from CLI to get good output.

---

### Post by lonniehenry on 2009-05-10
I too am having the same problems with Karmic and media files.  I get 3 seconds in and then a halt.  I have tried to bring things back to new install as mplayer worked ok.  Tried new user and it worked with youtube( no sound however, but it played) 
Not sure how to proceed from here

---

### Post by taavikko on 2009-05-11
> **lonniehenry said:**
> Tried new user and it worked with youtube( no sound however, but it played) 
Not sure how to proceed from here

Ok, so try moving settings from default users homefolder aside.
```
cd; mkdir .backups ; mv .gnome2/ .gconf/ .config/ -t .backups/
```
that'll create folder called .backups and moves those settings folders there.

Better to do that without X running, so they wont be recreated with same settings.

I usually destroy almost all settings from ~/ before doing release-upgrade.

---

