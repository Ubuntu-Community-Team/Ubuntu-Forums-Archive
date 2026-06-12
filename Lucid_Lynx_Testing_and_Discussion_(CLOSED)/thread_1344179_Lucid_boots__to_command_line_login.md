---
title: "Lucid boots  to command line login"
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Gina on 2009-12-02
I'm sure I've seen this mentioned before but I can't find it.

I have installed Lucid on my AMD64 desktop for testing. When I boot(normal boot - not recovery mode), it gives a command line login rather than the usual graphical start up.  If I log in and run **startx** it boots as usual.  Or if I leave it for a while it boots after 40 or 50 seconds.

Anyone else getting this?

---

### Post by ronacc on 2009-12-02
I am getting that here on my amd64 install but in my case the cmd line login only lasts 3>4 seconds then the splash screen comes up . I'm nvidia here with the repo 185 driver . try removing splash and quiet from the boot line to see what is happening .

---

### Post by seeker5528 on 2009-12-02
Is this happening with the 2.6.32-5 and/or 2.6.32-6 packages of the kernel and if so does it also happen if you boot with 2.6.32-4?

Later, Seeker

---

### Post by Gina on 2009-12-02
> **ronacc said:**
> I am getting that here on my amd64 install but in my case the cmd line login only lasts 3>4 seconds then the splash screen comes up . I'm nvidia here with the repo 185 driver . try removing splash and quiet from the boot line to see what is happening .Yes, I'll do that.  Good thinking :):)  nvidia here too but using the default driver OOTB.

---

### Post by jfernyhough on 2009-12-03
I get something similar. First boot drops me to the low graphics prompt, at which point I exit to CLI and reboot. Next time it comes up fine. I'm wondering if it has anything to do with enabling concurrent startup option, though it might just be an xsplash/usplash thing.

(.32-6 with nvidia 195 beta)

---

### Post by Gina on 2009-12-03
Just tried removing quiet and splash.  It now shows the startup text but still goes to a command line prompt as before - and this times out in about three quarters of a minute :(

All looked reasonable as the text flashed past though it spent quite a long time setting up CUPS.  It goes straight from setting things up to the command prompt.

---

### Post by kansasnoob on 2009-12-03
Remember this:

[http://ubuntuforums.org/showthread.php?t=1337082](http://ubuntuforums.org/showthread.php?t=1337082)

> Anyone else lose their graphical login?

I just go straight to a tty, then I can login and startx.

I also notice that I can't "unlock" the gdm gui.

Been that way since then.

Right now I'm focused more on punishing Karmic!

Trying to make it lockup after some updates from xorg crack pushers. So far the most stable I've seen Karmic :guitar:

---

### Post by Gina on 2009-12-03
Ah yes - thank you - that was it :)  I knew I'd seen it mentioned before!  I hadn't imagined it.

---

### Post by Kevbert on 2009-12-04
No problems here on AMD64X2, Nvidia default driver and kernels -4,5,6.

---

### Post by zika on 2009-12-04
> **Gina said:**
> I'm sure I've seen this mentioned before but I can't find it.

I have installed Lucid on my AMD64 desktop for testing. When I boot(normal boot - not recovery mode), it gives a command line login rather than the usual graphical start up.  If I log in and run **startx** it boots as usual.  Or if I leave it for a while it boots after 40 or 50 seconds.

Anyone else getting this?Did You try ```
sudo service gdm restart
```in tty?

---

### Post by Gina on 2009-12-04
> **zika said:**
> Did You try ```
sudo service gdm restart
```in tty?Not yet - I'll try that.  I have a hardware problem with the AMD64 ATM which I've got to sort out first.  It won't start up.

---

### Post by Gina on 2009-12-05
Just tried it - no fix :(

---

### Post by wnelson on 2009-12-05
The problem I think has to do with /etc/init/gdm.conf.

---

### Post by xebian on 2009-12-05
I think you need to increase the timeout to some 500?

IIRC this is because readahead is too fast others can't catch up.  ;)

---

### Post by Gina on 2009-12-05
> **xebian said:**
> I think you need to increase the timeout to some 500?

IIRC this is because readahead is too fast others can't catch up.  ;)Which timeout?  500 secs is over 8 mins.:o

---

### Post by autocrosser on 2009-12-05
Interesting---I was also having this problem & the new -7 kernel "fixed" it--no usplash or xsplash --just black screen until GDM, but it logs in good for me.....

---

### Post by Gina on 2009-12-05
Strange, but glad it fixed yours - it didn't fix mine.  I have quiet and splash turned off too.

---

### Post by Gina on 2009-12-05
> **wnelson said:**
> The problem I think has to do with /etc/init/gdm.conf.Well, I've had a look at it but can't see anything wrong.

---

