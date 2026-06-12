---
title: "Opening session problem"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by phaphane on 2007-04-21
Hello all,

I have a big problem, when I open my session I can see the desktop but 1 second later I've a black screen and I return to the login session.

I've got a PII 350Mhz with 256Mo de SDRAM, a 3dfx Voodoo 2000, no sound card and a ethernet card 3com.
The motherboard is a micronics with a 440BX chipset I think.

Thank's for your help!!!!

---

### Post by pepsi_max2k on 2007-04-21
did you enable desktop effects (compiz / beryl) ?

---

### Post by phaphane on 2007-04-21
No idea I've use the alternate install because I've got the same problem with the live CD.
How can I check this in command line ?

---

### Post by pepsi_max2k on 2007-04-21
never mind, that'll be a no if you haven't even got in to the desktop. If the live CD don't work either, that ain't good... likely there's a problem with whatever graphics drivers your card uses. you could try reconfiguring the x-server but i'm not sure how you'd do that... :(

**EDIT:** sudo dpkg-reconfigure xserver-xorg

might work...

---

### Post by baras_k9 on 2007-04-21
Hi, 

I do have tried the window effects but  It didn't make any change at all in the desktop.

After that, I tried to use compiz and begin to have the problem.

Any suggestion?

Thanks in advance

---

### Post by pepsi_max2k on 2007-04-21
turn compiz off? and xgl.... 

try this on a command line "gnome-xgl-switch --disable-xgl"

---

