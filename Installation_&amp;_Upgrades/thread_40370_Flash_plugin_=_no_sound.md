---
title: "Flash plugin = no sound"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by Snipersnest on 2005-06-08
I'm hoping somebody can help me out with this problem...but I don't have any sound from flash movies that I load.  Did I do something wrong?

[http://snipersnest.jophis.com/index.php?module=PostWrap&page=mp3player](http://snipersnest.jophis.com/index.php?module=PostWrap&page=mp3player)

Thats my website MP3 player...it loads up all funny. I'm guessing since something is wrong with the sound support for Flash on my Hoary system.

Any ideas?

2.6.10-5
SB Live! CT4760
Latest Flash Plugin
Latest FireFox
Athlon 2600+
1GB PC2700

---

### Post by makisupa123 on 2005-06-08
Don't know if this will help or not....but I had the same problem until I followed the directions here:

[HOWTO: Hear multiple sounds](http://ubuntuforums.org/showthread.php?t=32063) 

BTW -- checked out your page...works fine for me.

Mak.

---

### Post by Snipersnest on 2005-06-09
Well now I hear the music...but I can't see the text.  Were you able to see the text? Maybe I have to put my Windows fonts on Ubuntu?  Is that possible? 

Hmmm...works like a champ on the sound for the Flash though thanks for that link! I wonder if that will fix my problems in Counter-Strike with my mic not working.

---

### Post by makisupa123 on 2005-06-09
The text in the playlist or the text of what's playing?

I can see the later but the playlist only has blanks and the current track that is playing.  Never noticed any other flash problems.  Not sure about the font problem....

mak.

---

### Post by Snipersnest on 2005-06-09
Ya I can't see anything in the box at all...All I know is the sound is playing.  Normally on Windows, you can see the track title, the time in the track, and you see all the titles on the playlist.

lol just like xmms is acctually. I guess I gotta figure out what font it is. Do you know anything about putting Windows fonts on so Linux can use them?

---

### Post by makisupa123 on 2005-06-10
Well, its working for me.  All i did was install some things on the "unofficial addon CD" and the new installation script.  Check out:

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts) 

Basically for your purposes:

```
sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
```

Hopefully, that'll do the trick for you.

mak.

---

### Post by Snipersnest on 2005-06-11
[QUOTE=makisupa123]Well, its working for me. All i did was install some things on the "unofficial addon CD" and the new installation script. Check out:

[http://ubuntuguide.org/#extrafonts]("http://ubuntuguide.org/#extrafonts") 

Basically for your purposes:

```
sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
```

Hopefully, that'll do the trick for you.

mak.[/QUOTE]
 hmm I got them to go in but now I can see the current song...lol it doesn't let me see the playlist, only the song its on. Does your show all of them?

---

### Post by makisupa123 on 2005-06-12
No..the playlist just shows the song that is playing.

mak.

---

