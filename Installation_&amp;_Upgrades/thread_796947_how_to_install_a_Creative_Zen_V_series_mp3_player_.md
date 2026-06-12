---
title: "how to install a Creative Zen V series mp3 player in 7.10"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by kami_iwinaru on 2008-05-16
I wanna be able to see the mount on the desktop when I plug in my mp3 player, and of course be able to open it, etc.. When I plug it in, it opens up Music Player, but it says I have 0 songs in it, which I don't.

I did lsusb first and here is the output:
```

Bus 001 Device 005: ID 041e:4152 Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000

```

Much appreciated in advance to anyone who can help.

---

### Post by qamelian on 2008-05-16
In Rhythmbox, go to Edit > Plugins and put a check mark in the box beside Portable Players - MTP. I'm not sure it the version of Rhythmbox in 7.10 actually has this plugin or not. It is present in 8.04 though.

---

### Post by kami_iwinaru on 2008-05-16
Actually, I got it
I knew about gnomad, but I didn't realize it's called gnomad2.
So its all set now, works fine.

---

### Post by drewcoon on 2008-05-16
I'm not familiar with the V series, but I know that my Zen Vision M isn't mounted to view the music, it needs a music manager (such as gnomad2).

Have you tried using gnomad yet? I'm pretty sure that it works with the V series. It's only a manager (it doesn't play the music), but it's great for adding and organizing music in Creative players :)

EDIT oops too slow :p

---

### Post by clstal on 2008-09-13
Another question - my creative vision m is found in gnomad2 and I can transfer music.  However, I'd like to be able to access it on the desktop similar to a thumb drive.  

Is that possible and if so, how might I go about it?  

Thanks so much!
Crystal

---

