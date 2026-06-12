---
title: "LiveCD setup freezing at 95% (pc card)"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by helsby on 2005-08-03
On a standard installation to my (old) toshiba 2065CDS setup, the machine hangs at 95% of the installation with the phrase Starting PC card services... on the screen.
It stays there for at least 10-15 minutes before I switched the machine off.
boot_debug=1 and DEBUG_CONF=5 in the boot parameter does not make any visible difference that I can tell on finding out where/what is causing the problem in more detail. (how do I access the logs?)
If I remove the Netgear MA401 PCMCIA card then the laptop continues to boot but so far its taken another 30 minutes and i've still not got to a logon screen!
What would I do to start the detection of the card once the boot up has completed after plugging the card in (or get the startup working with the card)

---

### Post by hypnos on 2005-08-04
Try to boot this way:

live hw-detect/start_pcmcia=false

---

### Post by helsby on 2005-08-05
[QUOTE=hypnos]Try to boot this way:

live hw-detect/start_pcmcia=false[/QUOTE]
That gets me further.....
The installation now goes all the way up to the cups installation and then shortly after that the screen goes black. A couple of seconds later the laptop beeps and nothing seems to happen....
5 minutes later  the laptop just shuts down
I have to remove the battery and the mains to reset the laptop before I can turn it back on again.
How do I get to a console view so I can see whats going on. Other installations used things like alt-f2 etc.

---

### Post by helsby on 2005-08-06
by using the startup options 
   live hw-detect/start_pcmcia=false vesa

it looks like I'm getting somewhere. 
ctrl-alt-f3 gives me a console with logs, as does ctrl-alt-f4.ctrl-alt-f7 switches back to the xwindows interface.

However it is incredibly incredibly slow.
I started the boot 48 minutes ago and I've still not got a gui login shell - just the orange ubuntu graphic.

---

