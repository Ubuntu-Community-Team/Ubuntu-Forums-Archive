---
title: "My VGA card doesn't seem to be working."
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by abantu_IV on 2008-06-15
Been following this as I think i have the same problem, my laptop (Samsung; Intel DuoCore T2250 1.73GHz RAM 1.75GB) also keeps hanging at the same spot after the scripts (if I want to use live cd):
starting deffered execution scheduler ard OK
starting periodic command scheduler crono OK
checking abttery state OK
running local boot scripts (/etc/rc.local) OK

Then it stays there however long i wait, (last time I took a shower :) and it was still just blinking there

And then i thought maybe i install it. This is what i get after I click on install Ubuntu and a fter a few minutes(its 8.04):
ubuntu@ubuntu:~$

What does that mean and what can I do? I mean what is it expecting from me? All the manuals dont have any of this, how do i move to a more graphic interface where am asked and i reply and i move on?
I would really like to have Ubuntu, I installed Open SUSE 11 but somehow i cant do anything on it at all, though the install was problem free.
Thanks in advance.

---

### Post by PmDematagoda on 2008-06-15
What is the VGA you use abantu_IV?

---

### Post by abantu_IV on 2008-06-16
> **PmDematagoda said:**
> What is the VGA you use abantu_IV?
Am sorry Pm, i must confess that am not very computer knowledgeable. How do I find that out what VGA i use? Thanks.

---

### Post by abantu_IV on 2008-06-18
> **abantu_IV said:**
> Am sorry Pm, i must confess that am not very computer knowledgeable. How do I find that out what VGA i use? Thanks.
Hello people. 
Brian, did you get the installation working fine? If so please get back to me and tell me how you did it. Am still hoping that mine will work.
And for anyone with an idea, this was my post, am still waiting for reply:
Been following this as I think i have the same problem, my laptop (Samsung; Intel DuoCore T2250 1.73GHz RAM 1.75GB) also keeps hanging at the same spot after the scripts (if I want to use live cd):
starting deffered execution scheduler ard OK
starting periodic command scheduler crono OK
checking abttery state OK
running local boot scripts (/etc/rc.local) OK

Then it stays there however long i wait, (last time I took a shower and it was still just blinking there

And then i thought maybe i install it. This is what i get after I click on install Ubuntu and a fter a few minutes(its 8.04):
ubuntu@ubuntu:~$

What does that mean and what can I do? I mean what is it expecting from me? All the manuals dont have any of this, how do i move to a more graphic interface where am asked and i reply and i move on?
I would really like to have Ubuntu, I installed Open SUSE 11 but somehow i cant do anything on it at all, though the install was problem free.
Thanks in advance.

Pm asked about my VGA. Could it be ATI Radeon Xpress 1250? I dont know people, but am really interested in trying Ubuntu- 
I dont have internet conection all the time so i wont be able to give immediate feedback, but anyone with an idea, please just give the whole list of things i should try. Thanks again

---

### Post by PmDematagoda on 2008-06-19
abantu_IV, post the output of:-
```
lshw -C video
```

Also I am forking this thread to maintain some order otherwise everything will be confusing.

---

