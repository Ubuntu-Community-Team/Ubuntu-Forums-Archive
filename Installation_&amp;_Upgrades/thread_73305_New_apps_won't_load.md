---
title: "New apps won't load"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by eraos on 2005-10-08
I installed RealPlayer and Acrobat Reader... both which seemed to install fine... both show up in the Gnome Applications Menu.

But neither load when I select them.

Why might this be?

Thanks for any help.

---

### Post by madjo on 2005-10-08
hmmm I can say I seem to experience the same issue, but only with Realplayer.
It does get started but nothing shows in X, and according to ps -A in the console you get something like this:
```
<snip>
11433 pts/1    00:00:00 realplay
11438 pts/1    00:00:00 realplay.bin
11440 pts/1    00:00:00 realplay.bin
11441 pts/1    00:00:00 realplay.bin
<snip>
``` 

Eraos, do you have the same issue? (If not, then I will place this in a new thread)

---

### Post by manicka on 2005-10-08
Do you have another sound app like amarok or ryhthmbox, running at the same time. Quit those first then in a  terminal run 

killall realplay

then try Realplayer again

---

### Post by eraos on 2005-10-08
madjo: 
No, I don't have that same problem.  Nothing even happens when I click the realplayer icon.


manika: 
As far as I know, nothing else is running.

```
realplay: no process killed
```

---

### Post by eraos on 2005-10-08
Okay, I reinstalled acrobat reader (using apt-get instead of synaptic) and now it works fine.

I'll see if I can reinstall realplayer.

---

### Post by madjo on 2005-10-09
@eraos: indeed, nothing appeared for me either... what you saw in my post was a result of typing in the text "ps -A" in a console window. :) 
I hope reinstalling realplayer works for you. :) (my apologies for bursting into this thread)

@Manicka, you are right, it was Amarok causing the problem for me. thanks.. :)

---

