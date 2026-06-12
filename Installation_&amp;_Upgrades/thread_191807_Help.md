---
title: "Help"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by curiosa863 on 2006-06-08
I've been trying for a couple hours to start the install process... i finally got it to boot the cd, and i checked my disc for errors, then launched the desktop. from their i've been trying the 'install' link on the desktop. in the application bar at the bottom it says 'starting administrative  (?)' that dissapears after about 20 seconds. then i am left with the desktop again. 

What i would like to be doing is formatting my hard drive, and putting ubuntu on fresh. thanks in advance for your advice, this is a great community.

---

### Post by curiosa863 on 2006-06-08
sorry, this is probably a really simple noob problem. If i could even just get help on formatting my XP hard drive, that would be great.

---

### Post by aysiu on 2006-06-08
How much RAM do you have?

And can you try typing this command in the terminal and posting the output? ```
gksudo ubiquity
```

---

### Post by curiosa863 on 2006-06-08
I'm pretty sure it has 512 of ram, it may be as little as 256. Definetly no less than that. The terminal was unresponsive to that command. or so it appeared... now after waiting several minutes an install window has popped up on my desktop... but i can't get it to accept input.

---

### Post by aysiu on 2006-06-08
That's really weird. I'm not sure what to tell you. If you had 128 MB of RAM or less, this behavior would make sense. Otherwise, I don't know what the problem is.

---

### Post by curiosa863 on 2006-06-08
it really seems to be a problem with ram. i got to the second install screen now... is there anyway short of upgrading ram to get this to work?

---

### Post by aysiu on 2006-06-08
[QUOTE=curiosa863]it really seems to be a problem with ram. i got to the second install screen now... is there anyway short of upgrading ram to get this to work?[/QUOTE]
Yes. Use the Alternate Install CD instead of the Desktop CD.

The Desktop CD is trying to run a fully-functional live desktop session *while* installing itself--too many processes for minimal RAM.

The Alternate Install CD runs enough in RAM just for the installation process.

---

### Post by curiosa863 on 2006-06-08
ok, thanks. you wouldn't happen to know if i can format my harddrive during the install. or if you could point me in the direction of how to do it. i can boot into dos... or a program in xp? thanks again.

---

### Post by aysiu on 2006-06-08
[QUOTE=curiosa863]ok, thanks. you wouldn't happen to know if i can format my harddrive during the install. or if you could point me in the direction of how to do it. i can boot into dos... or a program in xp? thanks again.[/QUOTE] You do not need to preformat the drive. The installation process will overwrite whatever partition you choose to format.

You can also choose to erase the entire hard drive.

---

### Post by curiosa863 on 2006-06-08
sounds great. the download for the alternate install is just about done.

---

