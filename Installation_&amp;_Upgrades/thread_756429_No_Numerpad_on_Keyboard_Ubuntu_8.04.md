---
title: "No Numerpad on Keyboard Ubuntu 8.04?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by mep on 2008-04-15
Hello,

I have a standard keyboard and worked fine in Ubuntu 7.10  Today decided to try beat 8.04 and along with other things that I am trying to work out suddenly now my number pad on my keyboard will not work?  Yes num lock is on.  Worked fine in 7.10

help

-mike

---

### Post by mep on 2008-04-16
I want to bump up this post as I have no clue why my Number Pad on Keyboard does not work in 8.04.  Seconds before upgrading it worked fine in 7.10 ??  Number Lock is working.  Light is On but no input to screen from Number ( Numeric ) Pad

??  Standard 101 Keyboard with USA settings

Help would be appreciated

-mike

---

### Post by mep on 2008-04-16
ISSUE SOLVED

Found this post:

[https://bugs.launchpad.net/ubuntu/+bug/190579](https://bugs.launchpad.net/ubuntu/+bug/190579)

Solved by disabiling mouse control in keypad under Mouse Tabs in Keyboard Prefs..  I should have search a wee bit harder.. :)

Thanks for support

-mike

---

### Post by LingLing on 2008-06-22
I had the same problem
Thanks, Mike for posting the link.
Here's the solution in short:

   1. Go into the Keyboard Preferences (System >Preferences > Keyboard)
   2. Switch to the Mouse Keys tab
   3. Uncheck the box for Allow to control the pointer using the keyboard

---

