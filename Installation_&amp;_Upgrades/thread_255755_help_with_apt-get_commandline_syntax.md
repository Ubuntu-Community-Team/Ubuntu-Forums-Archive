---
title: "help with apt-get commandline syntax"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by stanwebber on 2006-09-11
i am trying to incorporate this command into a bash script run by root:  apt-get install gnomebaker

when run from a normal terminal window the apt-get command prompts for a y/n do you want to proceed.  how do i get this to work non-interactively in a script?  i have looked at the man page & tried the following with no success:

apt-get -y install gnomebaker
apt-get install gnomebaker -y

what is the correct syntax?

---

### Post by randell6564 on 2006-09-12
Just curious...

Why would you need to do this?  After 'gnomebaker' is installed, you don't have to repeat the process.

---

### Post by stanwebber on 2006-09-12
gnomebaker is just a random example

---

### Post by randell6564 on 2006-09-12
> **stanwebber said:**
> gnomebaker is just a random example
Yeah, but the same goes for ANY Application!

Anyway.,this forum really SUCKS! If you are experiencing the same load times that alot of users of this forum are experiencing, then let me suggest that you post your question over at [www.linuxquestions.org](www.linuxquestions.org)

I really do not feel like trying to communicate through this forum.

---

### Post by stanwebber on 2006-09-14
i'll agree it SUCKS this is the only response i get

---

### Post by moore.bryan on 2006-09-14
[I]```
sudo apt-get install -y gnomebaker
``` will assume "yes" for all questions.
[/I]

---

### Post by stanwebber on 2006-09-14
ok, i investigated this further.  it appears apt-get is failing to run in a script executed from nautilus regardless of syntax.  i have the following commands at the end of my script (run under root):

apt-get update
apt-get -y install package

BOTH fail to execute successfully--all other commands perform flawlessly.  if i open up a terminal & manually type in the apt-get commands there's no problem.  what is preventing apt-get from running in my script?

---

### Post by moore.bryan on 2006-09-14
*are you sure the script is chmod'd?  that weird.  what, exactly, are the error messages?*

---

### Post by stanwebber on 2006-09-15
ok, here's the problem.  i'm running the script off a usb stick mounted at /media/usbstick.  if i copy the script to the desktop & execute it either by nautilus or in a terminal window it works.  i have a dozen other frequently used bash scripts (comprising a wide range of root level commands) on the usb stick which execute flawlessly.  for some reason apt-get is different (perhaps the fat filesystem?).  can anyone think of a way to get apt-get to cooperate when executed from the usb stick?

---

