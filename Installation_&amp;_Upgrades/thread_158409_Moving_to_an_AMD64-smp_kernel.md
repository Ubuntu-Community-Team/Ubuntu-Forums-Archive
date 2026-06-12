---
title: "Moving to an AMD64-smp kernel?"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by Yanagi on 2006-04-11
Hi there. I searched the forums for a bit and didn't find anything quite relevant to my problem, so please excuse my new thread. ](*,) 

I'm a SuSE convert to Ubuntu - amid all the things I'm getting used to (no RPMs, etc.), I set up Seti@Home to run on my newly converted Ubuntu box. I was dinking around in the System Monitor when I noticed that the BOINC (the managing program) was only running one seti process. Previously, it ran one for each of the cores in my AMD64 X2.

So I uname -r and lo and behold, I'm running "2.6.12-10-amd64-generic"
Last time I was running linux (SuSE, with a brief stop off in FC5 land before I decided to try Ubuntu) I was running  2.6.13-15.8-smp.

I've heard of recompiling the kernel and all sorts of scary sounding things like that (I'm a fast learner, but I've only been using linux for 6 months or so...) - but isn't there some way to do it with a config file or downloading a patch or something? :-? 

If there is no other way but to recompile the kernel, would some one please outline the process in a step-by-step fashion.

I could really use some help here, guys. Thanks a ton. ^_^

- Yanagi

---

### Post by bonzodog on 2006-04-11
The smp kernel is available from the repo's.
just type this into a terminal:
```
$sudo apt-get install linux-amd64-k8-smp
```

That will install you the latest smp kernel image.

---

### Post by Yanagi on 2006-04-11
You're so beautiful I could kiss you.

I was trying that apt-get stuff (on the recommendation of my friend), but I couldn't figure out the package name. The closest I could get was "2.6.12-10-amd64-k8-smp"

Thank thank you.


*blink*

*kiss*

^_^

---

