---
title: "a /usr/bin/ and /usr/local/bin problem"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by Ponhovo on 2008-07-26
i installed jack 109 but i can't find the 'alsa module' for it
but it installed over /usr/local/bin/jackd
when i run /usr/bin/jackd, it does everything ok, which is the 103.0 ubuntu repository one
but i can't install the same 'jackd' of the /usr/bin on my /usr/local/bin to make it workable [since i got no permition to run /usr/bin entirely working]
even when i installed 103.0 again, i cudn't run alsa module

even reinstalling everything with synaptics, it doesnt work! 
plz, I need help :/

i was being posting in here many times, and ppl simply doesnt help me
i know im already being annoying, but i NEED help about that... and nobody helps me
pleaaase

---

### Post by pytheas22 on 2008-07-26
I'm not sure exactly what's wrong, but if the problem is that you want jackd to be inside /usr/local/bin and not /usr/bin, then this should solve the problem:

```
sudo mv /usr/bin/jackd /usr/local/bin/jackd
```

You should have permissions to do that as long as the account that you're using is allowed to use sudo (by default, the first user account installed on the system has sudo permissions; they can be added to other accounts using the utility at System>Administration>Users and Groups).

If I'm misunderstanding your question, please try describing again what the problem is.

---

### Post by Ponhovo on 2008-07-26
i think you got the problem...
but it wudn't still work coz if i move the executable itself, it wud still miss of libraries, which i don't know which and where those are, just as the /usr/local/bin/jackd miss of alsa libraries
got it?

---

### Post by pytheas22 on 2008-07-27
Alright, in that case, maybe:
```

sudo cp /usr/bin/jackd /usr/local/bin/jackd
sudo ln /usr/bin/jackd /usr/local/bin/jackd
```

Otherwise, which libraries does it say it's missing...in other words, what is the output in the terminal when you type:
```

/usr/bin/jackd
```

If it thinks libraries are missing, there's probably a problem with the installation.  How did you install it?

---

