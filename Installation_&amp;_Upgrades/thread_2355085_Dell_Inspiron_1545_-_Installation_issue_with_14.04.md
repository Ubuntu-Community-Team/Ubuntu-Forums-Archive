---
title: "Dell Inspiron 1545 - Installation issue with 14.04 LTS"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by upbabu on 2017-03-09
Hi,

I'm stuck with Ubuntu installation on my Dell Inspiron 1545 laptop since about a week.
*Version in question: **14.04***
The **live CD works **just perfect.
However, post installation, there is no mouse, no ethernet & no wireless. 
(Even the USB keyboard doesn't work but that's not really a blocker as the laptop keyboard works just fine)

Gone through several iterations of installing the same version, different minor versions (tried 16.04, 14.04.2 and currently on 14.04.4).
Behavior is the same across all attempts.

There are some solutions discussed in this & other forums for specific problems - say mouse not detected.
But with no internet & no mouse, I've really moved nowhere.

Any help would be much appreciated. 
Thanks a lot.

---

### Post by upbabu on 2017-03-10
Since the keyboard is functional, I'm able to launch a few programs & use the terminal.
Can someone please guide to set this right?

---

### Post by Bucky Ball on 2017-03-10
A) Plug in an ethernet cable if you can and you haven't already. That will help your cause and make fixing this MUCH easier.

B) [14.04.4 is EOL (end of life) and no longer supported]("https://wiki.ubuntu.com/Releases"). Suggest you use 14.04.5 or 16.04.2.

C) What are the specs of the machine? How much RAM and what video card specifically.

D) I've never owned a Dell but have been around here for longer than I care to remember. From what I've seen here, you need to jump through hoops to install on some of them, but as you are installed okay, you may need to add an option to the boot line specifically for the Dell model you are running. This option I wouldn't have a clue about.

Hopefully someone familiar with Dell laptops and their anomalies in regards to Ubuntu will jump in soon, but hope that's of some help. ;)

---

### Post by fyfe54 on 2017-03-10
I had a 1545.  The only issue I had was with the Realtek wifi card, which I solved with a (cheap, used) intel.

---

