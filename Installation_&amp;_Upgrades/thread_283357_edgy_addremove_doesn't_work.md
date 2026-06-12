---
title: "edgy add/remove doesn't work"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by helmeteye on 2006-10-24
First question may seem stupid, so what.  I think I've upgraded to 6.10 but I am not really sure.  How do I find out?  That is the first question.

     I am new to ubuntu, maybe 2 weeks or so and a complete noob as far as using shells.  It took me 3 or 4 tries to get anything in the 6.10 upgrade to work and I believe I have upgraded because everything just looks better than the previous install of 6.06.  

     Main question is: how do I get add/remove to work?  Right now it only goes halfway and then shuts down.

     So far, I really like the way the new Edgy looks, if I am actually running 6,10:)  I haven't tried out many things though.  I hope everything works as good as it looks and runs as good as it seems to be running now that I have it up and running.  Seems to be faster.

---

### Post by Kateikyoushi on 2006-10-24
This should tell you which release are you using.

```
lsb_release -a
```

Did you try to install the program with aptitude ?

```
sudo aptitude search proragname
sudo aptitude install packagename
```

If you get an error then post it.

---

### Post by Circus-Killer on 2006-10-24
another way to tell if you are really running 6.10 is to go to your gnome menu bar, click on system, then "about gnome". when that "about gnome" window pops-up you will see the gnome version number in the bottom-left hand corner. 6.10 uses gnome 2.16 whilst ubuntu 6.06 uses gnome 2.14. so by looking at the gnome version you can generally see what version of ubuntu you are using.

as for the add/remove not working, well, i haven't used that in edgy. to be honest, i prefer just using apt-get from the command-line. find it more quicker, easier and cleaner to use. you should try familiarize yourself with apt-get. its easy and will prevent buggy front-ends from holding you back.

Hope that helps, oh yeah, and welcome to ubuntu. give yourself time to learn your way around, after a couple of months you will be loving it.

---

### Post by Kateikyoushi on 2006-10-24
Then you could click about ubuntu instead of about gnome to know your version.

---

### Post by helmeteye on 2006-10-24
Thanks circus and youshi.  Killer, apt-get is what I have been using, that was the only way to get any updates for a while.  Add remove have been broken for some time.  I have never used remove to actually remove something but am also wonder what is the best way to remove something.  What is command line for remove?  I am just a little obsessive.  If it doesn't work it drives me crazy and it's hard to move on when I see something that doesn't work.

     Oh yea, did the release code deal and as suspected.  6.10.  Sure looks much better and seems to be way faster so far.  Still haven't been able to get add/remove going though.

---

