---
title: "Keyboard Unresponsive upon Boot to Install disc"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by Nicholas_Campbell on 2014-11-16
Hey everybody,
I preface this by letting you know I have very little experience with Linux, so if I'm doing something stupid, please let me down softly.
I recently came into possession of a Dell Poweredge 1750. Hoping to use it for a Minecraft server, I upgraded the RAM to 4GB and, not having the money to get Win Server (which I have much more experience in), made a Ubuntu Server disc.
It booted to the disc fine, exactly as expected, but the first screen the Ubuntu Server install prompts me with is for the language. Here's where I run into my issue: Pressing enter on the (USB) keyboard does nothing. Restarting the server does nothing. It is either stalled or awaiting input from a keyboard that it does not read. I can't tell which it is.
Any ideas would be greatly appreciated.

---

### Post by Bashing-om on 2014-11-16
Nicholas_Campbell; Hey;

My thought, no driver is available in the operating system.
What one can try:
a) change the usb settings in bios (legacy, plug and play)
b) plug in an old ps/2 keyboard, see then if the keyboard is recognized.

'Bout all I know to do in this situation.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Nicholas_Campbell on 2014-11-16
Bashing-om,
Thank you! That fixed it.

---

### Post by Bashing-om on 2014-11-16
Nicholas_Campbell; Great !

But which ? or both ?
Did you only need to reset bios ? -> for the need to know for others seeking.

[INDENT][INDENT]confirmation
[INDENT][INDENT][INDENT]a nice thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

