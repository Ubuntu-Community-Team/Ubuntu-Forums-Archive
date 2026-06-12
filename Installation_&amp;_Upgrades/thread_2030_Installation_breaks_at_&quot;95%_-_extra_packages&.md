---
title: "Installation breaks at &quot;95% - extra packages&quot;"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by Fabian on 2004-10-25
Hello,

four weeks ago i installed ubuntu, it worked great! Used the system till yet, wonderful! Now i wanted to install the final:

> linux vga=771 hw-detect/start_pcmcia=false bootkbd=de 

This is my install command (VGA=771 because it's a Notebook, PCMCIA=false because it's always breaking when the system tries to start the PCMCIA).

At "Installing the Ubuntu base system", the setup is breaking... Caps Lock doesnt work anymore etc.

Any hints?

Thanks, greetings from Germany,

Fabian

---

### Post by Fabian on 2004-10-25
OK, I tried it now the 5th time, it's always breaking at this point. Now im getting sick of it...

---

### Post by rolf on 2004-10-25
Just for clarification, have you tried the Warty release without the custom line?  Mine installed on laptop with pcmcia wireless without issues.

---

### Post by Fabian on 2004-10-25
Yes I did... But PCMCIA did never work with any distribution I used. (Even Progeny ;-))

---

### Post by rolf on 2004-10-25
Post your PCMCIA details, maybe we'll get lucky and find something that works :)  I'll run your config against Progeny Debian and see what happens (just for fun).

---

### Post by Fabian on 2004-10-25
Which details you need?

---

### Post by rolf on 2004-10-25
[QUOTE=Fabian]Which details you need?[/QUOTE]

Whatever you've got.  Make and model of your pcmcia cards, pcmcia chipset if known (if not, make and model of mobo, assuming integrated pcmcia).  And lots of patience, I'll be in and out of the office this week :)

PS - this gets us off topic and onto a specific problem (ie, pcmcia).  Not sure resolving pcmcia will impact your overall experience with ubuntu or even fix the overall issue.  I'll still give it a whack.

---

### Post by Fabian on 2004-10-26
[QUOTE=rolf]Whatever you've got.  Make and model of your pcmcia cards, pcmcia chipset if known (if not, make and model of mobo, assuming integrated pcmcia).  And lots of patience, I'll be in and out of the office this week :)

PS - this gets us off topic and onto a specific problem (ie, pcmcia).  Not sure resolving pcmcia will impact your overall experience with ubuntu or even fix the overall issue.  I'll still give it a whack.[/QUOTE]
 Hey,

I will give you details as soon as possible. But my install is still breaking...

---

### Post by Fabian on 2004-10-26
Seems like I did it... Just worked with the expert install...
First boot just posts an error in hw_random (couldn't load) - PCMCIA worked with this IBM "exclude range 0x00 - 0xff" trick (or something like this)...

---

