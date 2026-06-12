---
title: "DPKG error need help please"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by Porridge on 2008-11-27
Hello I was searching the forums on this and found a couple of stuff but none really solved my problem.

I Just installed Ubuntu within XP since I am a first time linux user and have figured out almost enough to replace xp :)

but now i can't update or add new programs

I get the same error message when trying to do both.

"[COLOR="Red"] E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR] "

the other dpkg error i found on this forum was due to boot drive being filled up but mine still has 5GB left so i dont think that is the problem

Can anyone help?

[-o<

---

### Post by zibi on 2008-11-27
Open a terminal and type:

sudo dpkg --configure -a

Byebye

---

### Post by cariboo on 2008-11-27
Open a Applications-->Accessories-->Terminal and type:

```
sudo dpkg --configure -a
```

Just like it says in the error message.

Jim

---

### Post by Porridge on 2008-11-27
Oops i forgot to put that half of the error up.:lolflag:

after doing that it comes up 
"[COLOR="Red"]dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted[/COLOR]
"
and my fail train continues...

---

### Post by shoshanna on 2008-11-28
I"m having the same problem and did as directed, but received "no command found" Help!

---

