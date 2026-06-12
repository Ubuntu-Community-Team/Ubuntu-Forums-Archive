---
title: "connecting on boot"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by kroiz on 2008-03-30
In order to connect to the internet I need to run a script as sudo.
```
sudo cable-start
```
how can I make it automatic upon boot?
I tired adding it to system->preferences->session with and without the sudo but it does not work.
I tried also to put an absolute path and with and without sh. something like:
```
sh /home/kroiz/cable/scripts/cable-start
```
did not help.
is there a log I can view to know what happened?
is this the right way to add a script to start up?

---

### Post by Shazaam on 2008-03-30
System>Administration>Network. Is your connection set up there and is it configured?

---

### Post by kroiz on 2008-03-30
actually I never configured anything there.
I just follow a howto that produced a script.
when I run the script from the terminal like that:
sudo cable-start
It gets me connected to the internet and all is well.
but I don't want to run the script every time I log in.
I want it to be automatic.

BTW it is a computer that I installed for my father in law and he is not good with English or computers. I switched him to ubuntu and I want to make the transition as easy as possible.

---

