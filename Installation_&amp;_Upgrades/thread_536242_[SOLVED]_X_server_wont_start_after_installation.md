---
title: "[SOLVED] X server wont start after installation"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by comacozi on 2007-08-27
i just installed feisty fawn. i restarted the computer after installation, and it all seems normal until a screen pops up saying that x server cannot start.  I have an ati mobility radeon x1400, im guessing its a problem with my video driver, but how can i upgrade it when i cant even boot.

---

### Post by Pumalite on 2007-08-27
Get IN the System first; at the command line: sudo dpkg-reconfigure xserver-xorg. Say yes to most defaults, choose 'vesa' as your driver; then: startx
Worry later about appropriate driver for your card.

---

### Post by comacozi on 2007-08-27
just did that, got the same error

---

### Post by Pumalite on 2007-08-27
Could you be more detailed in what you did and what Error you got?

---

### Post by comacozi on 2007-08-27
it just says xserver wont start, im not sure what all the lines of text mean when it asks if i want more information..  im very new at ubuntu, i feel like an idiot.  im duel booting ubuntu and vista, but i jsut cant get ubuntu to start, should i reinstall it?

---

### Post by Pumalite on 2007-08-27
If you are using Vista, I hope you used the Vista partitioner; otherwise Vista will not let you run anything on that machine. What I don't get is if you got the GUI to configure your xorg or not?? If you followed my instructions, you should have a working system now. If not something is definitely wrong.

---

### Post by comacozi on 2007-08-27
yes i got the gui and i followed the but  still no xserver.  i think i should reinstall.  and vista is letting me have unbuntu on the machine.

---

### Post by Pumalite on 2007-08-27
[http://ubuntuforums.org/showthread.php?t=493273&highlight=ATI+x1400](http://ubuntuforums.org/showthread.php?t=493273&highlight=ATI+x1400)

---

### Post by comacozi on 2007-08-28
ok ive been reading forums all day and night, i only need one thing, how do i change the sources, becasue when i try to install the aglrx drivers, it looks in the cd drive.   im so close, please help

---

### Post by Marat Galiev on 2007-08-28
maybe **fglrx** drivers?
install it with sudo dpkg - fglrx-xxx.deb

---

### Post by comacozi on 2007-08-28
but it looked on the cd drive, how do i change that when all i have is a command prompt.

---

### Post by merlinus on 2007-08-28
```

sudo nano /etc/apt/sources.list

```

Delete all lines referring to cd's.

-merlin

---

