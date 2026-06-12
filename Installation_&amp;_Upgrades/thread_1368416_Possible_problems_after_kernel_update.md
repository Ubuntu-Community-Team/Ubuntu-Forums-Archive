---
title: "Possible problems after kernel update?"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by alegallo on 2009-12-30
I installed Karmic 64bit on my Athlon II X4 pc, and I constantly (weekly) update the OS.

Now I have kernel 2.6.31-16, and I deleted the old -14, which was quite annoying to see in the boot screen, and which also gave me problems about not having ECC ram. 

Following to this modifications I saw 3 different problems, which I can't really understand:
- grub does not start Ubuntu after 10 seconds, it keeps waiting forever until I press enter;
- powernowd is not started with the OS, I must start from terminal;
- the shmmax modification made by cinelerra has disappeared, so I had to do edit /etc/sysctl.conf to restore it;
- cupsd is not started at startup, just like powernowd.

Small things, I must admit, but annoying ones.

Moreover, I can't be sure that the problems have ended here, I just did not discover any more weird behaviour yet, but who knows? 

I thought that maybe uninstalling the old -14 kernel may have lead to some configuration problem, but I'm too noob to figure out what went wrong, and how to restore it all the way it has to be.

Thanks to everyone who can help ;)

---

### Post by ajgreeny on 2009-12-30
Try reinstalling the 2.6.31-14 kernel but still booting to the 16 (you should still do so by default, I think) and see if any difference shows.  Otherwise I can't imagine what else to suggest.

As a general rule, it is always worth leaving one older working kernel in case problems such as this occur.

---

### Post by alegallo on 2009-12-30
Thank you, ajgreeny
Actually I kept the 2.6.31-15 kernel as a "spare", but I really thought it was now safe to erase the -14.
I'll try, although it makes little sense to me ... ;)

---

### Post by bluesscream on 2009-12-30
I also had some minor troubles with 2.6.31-16. For me they are fixed in -17. You'll get it by activating "proposed" in your sorces software update list. After downloading this kernel and maybe the fitting headers you can deactivate this options if  you want to be on the safe side an not beeing bothered by up-to-the-minute and sometimes still experimental updates. 
I always hold 2 or 3 obsolete kernels present from which I know they really suit my needs.
I also have a amd64x2, power managemant and frequency scaling works fine and there is no more powernowd on this machine (still available in the repos). Cpu frequency scaling has preceded, so that powernowd might be not necessary any longer. But I'm no expert...
Isn't a little tweaking part of our fun with linux? ;)
Wish you a Happy New Year

---

### Post by alegallo on 2010-01-01
Thank you, bluesscream, I will try the new kernel
An you're right, it's really (one of) the fun part(s) of it ;)

In the meantime I tried ajgreeny's idea, but with no solution at all :(

Maybe 2.6.31-16 kernel changed some settings in my system, but reverting to -15 or -14 doesn't help.

The other thing I could figure out is that I installed (and uninstalled after some days) openshot video editor, but I don't think that it may change the settings for cupsd or powernowd ...

---

### Post by alegallo on 2010-01-02
I also tried updating the kernel, no way :(
Actually the 2.6.31-17 added some extra problems in my system, so it came and went right away :D

Any other idea is welcome :)

---

### Post by MarioA on 2010-05-02
If you are running 9.10, look into this. It worked for me.
 [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

