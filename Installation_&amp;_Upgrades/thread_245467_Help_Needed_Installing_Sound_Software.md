---
title: "Help Needed Installing Sound Software"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Unoone on 2006-08-27
I installed Lmms this seems to work ok. I have ardour installed but Jack won't startup. I installed Jack from the repositories. How do I install Jack so that it actually starts up and works with the sound editing apps? Thanks for your help. 

Once I get Jack and Ardour, etc. setup then I can start messing around making music in Ubuntu.:)

---

### Post by hw-tph on 2006-08-28
Read jackd(1) (type **man 1 jackd**).

Stop or kill your sound server (if you're running one like esound or arts), the simply type **jackd -R -d alsa** to start jackd. For more information read the manpage (see above).

You will probably want to use the realtime-lsm security module to allow users to run jackd and Ardour with elevated privileges to limit latency.

Håkan

---

### Post by Unoone on 2006-08-29
Thanks that info helped a lot. Now I have to find out how to set it up so that alsa turns off when jack starts and turns it back on when jack stops. It seems that jack lauches automactically when an app using it runs.

---

