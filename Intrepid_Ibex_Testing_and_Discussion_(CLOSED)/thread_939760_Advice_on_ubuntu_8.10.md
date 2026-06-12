---
title: "Advice on ubuntu 8.10"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phoenix_snake on 2008-10-06
Hi, I am a new user and recently wanted to just try out linux.

I am happy with Vista on my Inspiron 1525 and just wanted to try something different, I tried 8.04 first but it didn't detect some stuff like wireless so I decided to try the 8.10 beta cause its not too far from release.

Anyway everything works perfectly except my conexant modem, can some one help with its drivers.

Oh yeah and I will also try kubuntu but I read some other posts of people saying that they have problems with kde 4 and media keys and stuff on laptops, does this still occur?

---

### Post by forumache on 2008-10-06
May I ask why do you want to try something different when you are happy with what you have?

Regarding Kubuntu: you can always download a LiveCD, boot it and see for yourself, no need to install. I have Ubuntu, otherwise I would have given you an answer, although it might work on my computer and not on yours...

Above all, have fun!

---

### Post by GSMX on 2008-10-06
> **forumache said:**
> May I ask why do you want to try something different when you are happy with what you have?


"Exploring is the only true way to knowledge" no idea whose quote it is, but it's so true. I personally was happy with win xp, changed to Ubuntu 7.04 and got even happier!

TS:
Could you give some more info about the modem? Or else maybe this could give some help: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by forumache on 2008-10-06
I was just asking 'cause I try to understand other people way of thinking.

For example, I discovered that is useless to tell a friend who is happy with his/her computer about Linux. On the other hand, people who are unhappy with their computer are more likely to search for alternatives.

People like you and phoenix_snake are rare (or at least I haven't found many of them)

---

### Post by phoenix_snake on 2008-10-06
thanks for the reply, I am just interested in trying something new, I already have OS X and Windows and I have heard a few people talking about it and just want to see what its like :)

---

### Post by gcday on 2008-10-06
be aware if you are using a laptop that 3g support ranges from poor to "forget about it".

---

### Post by phoenix_snake on 2008-10-06
> **gcday said:**
> be aware if you are using a laptop that 3g support ranges from poor to "forget about it".
my wireless works on 8.10 :)

---

### Post by Sef on 2008-10-06
> I was just asking 'cause I try to understand other people way of thinking.

For example, I discovered that is useless to tell a friend who is happy with his/her computer about Linux. On the other hand, people who are unhappy with their computer are more likely to search for alternatives.

People like you and phoenix_snake are rare (or at least I haven't found many of them)

Or it could be a combination of both.

---

### Post by ronacc on 2008-10-06
my last (and only) experience with a conexant (win)modem ended with me going and buying a real (external) modem :lolflag:

---

### Post by phoenix_snake on 2008-10-06
> **ronacc said:**
> my last (and only) experience with a conexant (win)modem ended with me going and buying a real (external) modem :lolflag:
no u see this is a laptop so it has to be this modem :( 

I did some research and I heard there was a linux version of the inspiron 1525, this one has Vista so since its the same model, I will assume same hardware so there must be a linux driver right?

---

### Post by psyke83 on 2008-10-06
> **phoenix_snake said:**
> no u see this is a laptop so it has to be this modem :( 

I did some research and I heard there was a linux version of the inspiron 1525, this one has Vista so since its the same model, I will assume same hardware so there must be a linux driver right?

Not necessarily. Dell has a habit of shipping identical models (desktop and laptops) with completely different components between the same model line (with the same feature parity, unless you opt for upgrades). It's possible that the Linux version of the laptop may have a different modem than the Windows version.

Find out the exact type of modem you own:
```
$ lspci -vv
```

---

