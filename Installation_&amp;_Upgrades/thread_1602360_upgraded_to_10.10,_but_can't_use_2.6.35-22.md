---
title: "upgraded to 10.10, but can't use 2.6.35-22"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by karenk on 2010-10-21
I upgraded a week ago to ubuntu 10.10 (amd64).  I was unable to boot in 2.6.35-22 so I have been using 2.6.32-25.  I tried again last night after installing updates to 2.6.35-22.  Still no luck.   I really don't know what the error messages mean so I'm hoping someone can give me an idea of what to do next.

[LIST=1]
[*] 2.6.35-22 2 tries:
[LIST=1]
[*]appeared stalled so pressed power button--photo 15
[*]kernel panic, stalled--photo 19
[/LIST][*] 2.6.35-22 (Recovery) 3 tries:
[LIST=1]
[*]kernel panic, auto reboot--photo 21
[*]auto reboot--photo 22
[*]appeared stalled so I pressed power button
[/LIST]
[*]back with 2.6.32-25. update manager:  removed fglrx stuff
[*]2.6.35-22 3 times:  
[LIST=1]
[*]get to "ubuntu ...." screen, then blank, power save for a while, ctrl-alt-del, "ubuntu ...." shutdown screen
[*]kernel panic--photo 39
[*]stalled--photo 42
[/LIST]
[*]2.6.35-22 (Recovery):  stalled--photo 44
[*]Even 2.6.32-25 goes blank, power save after "ubuntu..." screen so I go into its recovery mode and reinstall fglrx stuff
[*]2.6.35-22 with 2 more tries:
[LIST=1]
[*]very texty startup screen with messages showing through, dots keep running, but eventually ctrl-alt-del--photo 45
[*]kernel panic again--photo 46
[/LIST]
[/LIST]

I gave up since this was much like what happened a week ago and I couldn't find any solutions then.  (I ran memtest then.)

Thanks for any help!


(Shuttle SH55J2, i7-870, ATI 4550)

---

### Post by P4man on 2010-10-21
Have a good look at picture 21. It clearly says "this is not a software problem, machine check: processor context corrupt". That sounds BAD.

Causes and more info here:
[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

---

### Post by P4man on 2010-10-21
BTW, if I had to guess what hardware component is causing it, it would be the PSU (since you already checked RAM?). Your case only has a 300W powersupply, thats already not much for what you have in it, and Ive found shuttle PSU's to be notoriously bad.

---

### Post by karenk on 2010-10-28
Well, today I updated the BIOS and upgraded to 2.6.35-23.  
And everything just worked beautifully!

---

