---
title: "CTRL-ALT-[F1-F6] not working"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lachild on 2009-03-23
Hey everyone,

After reading a thread where someone else was having problems with CTRL-ALT-[F1-F6], I thought I'd try this myself and noticed that this key combo is not producing the terminal window even hiting the combo twice doesn't work, however CTRL-ALT-F7 does bring me back to X like it's suppose to.

I looked through the first 5 pages in this forum and don't see any other posts, but I was wondering if anyone else is seeing this problem?

---

### Post by nystire on 2009-03-23
Sorry to say this, but it works for me. My system is upgraded from Hardy though, so that could be the reason. Is your system by any chance a clean install?

---

### Post by danwood76 on 2009-03-23
This used to happen with the fglrx ati driver.
What graphics drivers are you using?

I'm using the open source ATI radeon driver and ctrl alt F1 - F6 work fine.

---

### Post by ktp on 2009-03-23
I had seen the same issue with fglrx...but never with opens source ati drivers.

---

### Post by rburkartjo on 2009-03-23
working fine on my end too no problems

---

### Post by Bakon Jarser on 2009-03-23
I just tried this and had the opposite problem.  CTRL+ALT+F1 brought up a virtual terminal just fine but CTRL+ALT+F7 didn't work.  It tried to restart x.  I got a black screen, a mouse that wouldn't move, and amarok started playing again but that's it.  I tried ctrl+alt+bksp and then angrily remembered that that was not an option anymore.

---

### Post by llamakc on 2009-03-23
> **Bakon Jarser said:**
> I just tried this and had the opposite problem.  CTRL+ALT+F1 brought up a virtual terminal just fine but CTRL+ALT+F7 didn't work.  It tried to restart x.  I got a black screen, a mouse that wouldn't move, and amarok started playing again but that's it.  I tried ctrl+alt+bksp and then angrily remembered that that was not an option anymore.

Enabling ctrl-alt-backspace is easy; however, if it is not enabled the key combo of "alt-sysreq-k" will also work for you.

---

### Post by scaine on 2009-03-23
Don't get angry, get even.  Did you try ALTGR-SYSRQ-K (which is the same as CTRL-ALT-BS)?  If you don't have a SYSRQ key, just use PrintScreen.

I have no issues with my virtual terminals, except that UXA does seem to want me to "confirm" my choice by giving me a quick glimpse of my terminal, then dumping me back at CTRL-ALT-F7.  When it does so, a second attempt at CTRL-ALT-F1 has so far always gotten me to a terminal.

---

### Post by lachild on 2009-03-24
Thanks everyone.  

Last nights kernel update seemed to fix the problem.  I now have no issues getting back and forth from the terminal.


LaChild

---

