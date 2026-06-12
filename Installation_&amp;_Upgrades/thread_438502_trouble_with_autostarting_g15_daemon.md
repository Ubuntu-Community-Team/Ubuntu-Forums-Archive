---
title: "trouble with autostarting g15 daemon"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Memory.Dump on 2007-05-09
I found a thread earlier that states how to properly install the g15 drivers and it works great I'm really happy....only problem I am currently having is I can't have it automaitcly startup

I have the session set to sudo g15daemon  (name of the daemon file)
and I typed:

sudo visudo

and I added the text in blue

# User privilege specification
root    ALL=(ALL) ALL
[COLOR="Blue"]user    ALL=NOPASSWD: /usr/sbin/g15daemon[/COLOR]

however I still have to manually run the Daemon and when I type g15daemon in the terminal without the sudo it gives me an error I assume thats not correct either...could anybody help me

---

