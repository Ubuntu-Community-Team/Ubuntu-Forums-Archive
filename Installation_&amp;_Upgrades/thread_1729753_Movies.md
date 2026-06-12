---
title: "Movies"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by OmeRavoch on 2011-04-15
hello everyone, i'm new on ubuntu and i hope that you can help me.
i have many movies and all of them are in HD.
please tell me what the best media player that can play all HD movies whit no problems.

i have a 3D movie to, but its in iso file, what can i do to open a iso file on the computer and see a 3D movie.
in window i use cyberlink but i didn't find it for linux.
please tell me what the best way to play 3D movie and how to open iso files.

note: i'm new on linux so please take your time when you explane.

---

### Post by sanderd17 on 2011-04-15
VLC is the best FOSS video player (in my opinion), it's in the software center.

And to play from an iso, you need some iso-mounting software. Just search  in the software center and check what you can do. Something like "gmountiso" should do the trick.

---

### Post by SeijiSensei on 2011-04-15
VLC gets a lot of recommendations, but I prefer [**smplayer**]("http://smplayer.sourceforge.net/").  It's a nice graphical front-end to the best free player, [**mplayer**]("http://www.mplayerhq.hu/").

What matters most is how powerful a CPU you have and whether you have a video card that supports hardware decoding of H.264 streams.  I have an NVIDIA 9500GT and can use their VDPAU technology to offload the decoding.  If you have a machine with a reasonably fast CPU, you can just let it handle the task.

If you select smplayer in your software installer, it will install mplayer and anything else it needs automatically.  Alternatively, you can open a Terminal and type:

```
sudo apt-get install smplayer
```

then enter your password,  It will all happen for you.

If you have an NVIDIA card, you should run the "Additional Drivers" application (in the Ubuntu menus) and let Ubuntu install the proprietary driver for the card.  The VDPAU libraries will be installed automatically.  You can tell smplayer to use VDPAU by clicking Options > Preferences > General and selecting the Video tab.  Choose VDPAU in the drop-down box at the top of the dialog.

I have no idea about 3D, but I can open an ISO by right-clicking the file, selecting Open With, and choosing smplayer.

---

