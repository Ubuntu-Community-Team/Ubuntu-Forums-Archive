---
title: "Edgy hangs when booting from generic kernel"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by eyelessfade on 2007-01-28
I tried to install edgy on my new computer with no luck. Dapper worked fine, but when I upgradet to edgy it startet to hang at bootup. I found out that the 2.6.17-386 kernel worked fine, while the generic just crash. Any thoughts?

My specs on the computer is:
MB: Abit AB9 Pro /w newest bios
CPU: E6600
Ram: 2 x Corsair Dominator 6400
video: PoV nvidia 8800GTS
sound: Soundblaster Live 1024.

Some output
[boot.txt]("http://www.fribyte.uib.no/~svein/abit/boot.txt")
[dmesg.txt]("http://www.fribyte.uib.no/~svein/abit/dmesg.txt")
[lspci.txt]("http://www.fribyte.uib.no/~svein/abit/lspci.txt")
[lsmod.txt]("http://www.fribyte.uib.no/~svein/abit/lsmod.txt")

---

### Post by eyelessfade on 2007-01-30
Anyone?

---

### Post by eyelessfade on 2007-01-31
Well now I have compiled my own kernel, using the ubuntu 2.6.17-386 config as a basis on a 2..6.20-rc6, put on SMP support, changed the arch from 386 to core2duo and removed some stuff I didn't need and made some modules of new stuff (nice to have)

And what do you know. It plays very nice (using it now) even along with my nvidia 9746 module.
Still I would hope I could go back to the -generic soon, or maybe I just switch back to gentoo ;)

---

