---
title: "&quot;Failure to start the X server&quot; - not the normal problem"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by phoenix96 on 2007-08-30
I have an Inspiron 6400, with a X1400 graphics card and an Intel Pentium Dual Core processor.

Whenever I tried to boot my Live CD (Hardy Heron), I got the message:

"Failed to start the X server. It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem"

I then did as most of these thread say to do, and entered the code into the terminal and chose the ati driver. Everything else I skipped. 

Eventually I found my rampant tapping of the enter and space key brought me to an empty black screen. Now every time I try to install I end up with the same empty black screen. 

How do I get back to the terminal and what do I do?

---

### Post by Pumalite on 2007-08-30
Accept most defaults, but choose 'vesa' as your driver.

---

### Post by phoenix96 on 2007-08-30
my problem is that I can no longer get to the terminal - how do I get to the terminal from the live cd?

---

### Post by Pumalite on 2007-08-30
Applications>Accessories>Terminal
If your questions is because you end up with a blank screen; then: Ctrl+Alt+F1

---

### Post by phoenix96 on 2007-08-30
> **Pumalite said:**
> Applications>Accessories>Terminal
If your questions is because you end up with a blank screen; then: Ctrl+Alt+F1

No, I'm talking about on the Live CD, from the menu.

---

### Post by Pumalite on 2007-08-30
???

---

### Post by Pumalite on 2007-08-30
Your first post said you had ended with a command line, that you had ran sudo dpkg-reconfigure xserver-xorg, that you had chosen ATI as driver and you continue to have a problem. I told you to do the same, but this time choose 'vesa' as the driver. What happened?.

---

### Post by phoenix96 on 2007-09-01
> **Pumalite said:**
> Your first post said you had ended with a command line, that you had ran sudo dpkg-reconfigure xserver-xorg, that you had chosen ATI as driver and you continue to have a problem. I told you to do the same, but this time choose 'vesa' as the driver. What happened?.

I've been put back a step, I now do not get the error message but just a blank screen - so I can't get to the terminal anymore. After I click 'start or install ubuntu', it gives me the loading splash screen and then just stays black.

So the only way I can sort this out, I'm guessing, is to fiind a way to the terminal from the LiveCD main-menu or reformat.

Thank you for the help, btw :)

---

### Post by merlinus on 2007-09-01
Can you boot into Recovery Mode?

If so, that should get to a CLI where you can reconfigure the x-server.

-merlin

---

### Post by phoenix96 on 2007-09-01
> **merlinus said:**
> Can you boot into Recovery Mode?

If so, that should get to a CLI where you can reconfigure the x-server.

-merlin

is that in special graphical interface mode or something like that - the second option down - because then it says the same thing.

---

### Post by phoenix96 on 2007-09-01
Okay, I'm a bit stupid - the  F1 thing worked. 

I put it on vesa and pressed 'esc' for every other screen - it spat me out at a terminal and now when I restart it still gives me the blank screen treatment.

By the way, when I got to the settings, 'vesa' was selected.

I should probably note that vista is already installed on a separate partition - but i dont think that does actually make a difference.

---

### Post by phoenix96 on 2007-09-01
anyone?

---

