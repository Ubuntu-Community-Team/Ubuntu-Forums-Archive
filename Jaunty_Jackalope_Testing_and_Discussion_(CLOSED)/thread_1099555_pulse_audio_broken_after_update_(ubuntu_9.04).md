---
title: "pulse audio broken after update (ubuntu 9.04)"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by powerplayground on 2009-03-18
I installed new updates and now pulse audio does not work. I was going to use ALSA, but how do I switch from the system using ulse audio to alsa in fluxbox?

---

### Post by powerplayground on 2009-03-18
Here is what happens when I try to start pulse audio:
> michael@michael-laptop:/etc/init.d$ pulseaudio start
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.


I'm running pulse audio version 0.9.14ubuntu13

---

### Post by bapoumba on 2009-03-18
Moved to Jaunty.

---

### Post by powerplayground on 2009-03-19
Alright... how would I go about installing an older version of pulse audio? Make never works so the source code archives from the pulse audio are out of the question. Is there any .debs of older versions or can I use my ubuntu install disk to install an older version? I tried to enable my cd as a software source but it doesn't appear under software sources >.<

Edit: Also another thing I've noticed is that whenever sound starts to play it mutes.

---

### Post by crimsun on 2009-03-19
> **powerplayground said:**
> I installed new updates and now pulse audio does not work. I was going to use ALSA, but how do I switch from the system using ulse audio to alsa in fluxbox?

Can you be a bit more precise than "does not work"?

If you just want to use ALSA, you can disable autospawn. See /etc/pulse/client.conf.

---

