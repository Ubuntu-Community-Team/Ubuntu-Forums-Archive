---
title: "cleaning aptitude."
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by Toehead on 2006-08-31
I have been having some problems with a bad package in aptitude, and a few other annoyances. What is the command to completely remove all previously  downloaded junk, sources, ect. from aptitude, and starte with a clean slate. 
Thanks!
Brendan



Also, the regular updater in breezy won't let me upgrade to dapper. It starts, then says it cannot verify, and there may be a problem with the server or network. What is that about?

---

### Post by aysiu on 2006-09-01
Can you post the output of this command? ```
sudo aptitude update
```

---

### Post by randell6564 on 2006-09-01
> **aysiu said:**
> Can you post the output of this command? ```
sudo aptitude update
```

Hi aysiu!  Please tell me.,What is the difference between 'sudo aptitude update' and 'sudo apt-get update'?

Now, regarding the OP.  Should we not want to also see the results of 'sudo gedit (or nano) /etc/apt/sources.list?

Since the OP mentioned "sources", maybe there is a bad entry there.

Maybe that will answer the question of why the update notification from 'update manager' would not inform you of an updated version of Ubuntu!

---

### Post by aysiu on 2006-09-01
If there's a bad entry, *sudo aptitude update* should catch it.

By itself, there's not a lot of difference between *sudo aptitude update* and *sudo apt-get update*, but coupled with an *install* command, there's a big difference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Incidentally, if you want to see the sources.list, you can just do ```
cat /etc/apt/sources.list
``` No need to open it with Nano or Gedit.

---

### Post by randell6564 on 2006-09-01
> **aysiu said:**
> If there's a bad entry, *sudo aptitude update* should catch it.

By itself, there's not a lot of difference between *sudo aptitude update* and *sudo apt-get update*, but coupled with an *install* command, there's a big difference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Incidentally, if you want to see the sources.list, you can just do ```
cat /etc/apt/sources.list
``` No need to open it with Nano or Gedit.

That makes sense! So, there is a difference between 'sudo aptitude install...,
and 'sudo apt-get install...?

BTW, that 'cat /etc/apt/sources.list' was NICE!

---

### Post by aysiu on 2006-09-01
> **randell6564 said:**
> That makes sense! So, there is a difference between 'sudo aptitude install...,
and 'sudo apt-get install...?
Yes, it's big:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by randell6564 on 2006-09-01
Yeah, I read the link (still reading as a matter of fact!)  

I DID notice that using 'cat /etc/apt/sources.list' does not allow you to edit.  But, it's still pretty cool for a quick inquiry!

---

