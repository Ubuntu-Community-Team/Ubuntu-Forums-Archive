---
title: "Pulse(*) groups"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-02-13
when i open groups (system --> admin --> users & groups) and look at pulse, pulse-access & pulse-rt: "root" is missing.

As i know, it should be there with my user name. How are yours ?
Can't see the way to add "root" with these groups.

---

### Post by zika on 2010-02-13
> **dino99 said:**
> when i open groups (system --> admin --> users & groups) and look at pulse, pulse-access & pulse-rt: "root" is missing.

As i know, it should be there with my user name. How are yours ?
Can't see the way to add "root" with these groups."Root" is not in **pulse** and **pulse-access** in my system. Just "me". I do not have **pulse-rt** group...

---

### Post by dino99 on 2010-02-13
seems now that kernel deal with pulse, but mine does not run by itself, it require admin level.

---

### Post by zika on 2010-02-13
```
# useradd -G pulse root
```
```
sudo pulse...
```
At my Lucid pulse is user-oriented and do not require root...
What's different on Your machine that caused that?

---

### Post by dino99 on 2010-02-14
thanks for your answer, well i'm thinking about a wrong setting somewhere on my end, just can't find it :o

If Lucid does not include 'root' as user's group, i suppose that we don't have to add it. (like in your config)

---

### Post by psyke83 on 2010-02-14
PulseAudio doesn't run as a system-wide daemon on Ubuntu (and generally it's [not recommended]("http://pulseaudio.org/wiki/SystemWideInstance")), so you don't need to do anything.

---

### Post by dino99 on 2010-02-14
> **psyke83 said:**
> PulseAudio doesn't run as a system-wide daemon on Ubuntu (and generally it's [not recommended]("http://pulseaudio.org/wiki/SystemWideInstance")), so you don't need to do anything.

agree with you, but after booting, pulseaudio is flooding logs and i have to start it into console. Then fooding stop and i can use audacious or else.
So i have to find where i have wrong settings or rights.

i already remove ./pulse or reconfigure pulseaudio, but no succeed. :confused:

---

### Post by psyke83 on 2010-02-14
> **dino99 said:**
> agree with you, but after booting, pulseaudio is flooding logs and i have to start it into console. Then fooding stop and i can use audacious or else.
So i have to find where i have wrong settings or rights.

i already remove ./pulse or reconfigure pulseaudio, but no succeed. :confused:

Flooding logs with what?

---

