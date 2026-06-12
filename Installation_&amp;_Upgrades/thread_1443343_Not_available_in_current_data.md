---
title: "Not available in current data?"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by TurtleJuice on 2010-03-30
this is the message i keep getting when trying to install ubuntu software.  I am reading all sorts of walkthroughs trying to get such things as java and am unable to do anything they keep failing at some point or another.  any help pls

---

### Post by uRock on 2010-03-31
If you could get the message again and take a screenshot using Applications> Accessories> Take Screenshot. This way we can see the problem first hand and give you the best advice. To attach a file use the paper clip right beside the font color picker.

---

### Post by skotu on 2010-05-01
I created a USB Startup disk using the 9.10 live cd. After booting up the USB stick, all software I wanted to install showed up as "Not available in current data". Nothing would install via the command line, synaptic package manager, or the software center.

I ran ```
sudo apt-get update
``` (which on other threads has fixed the problem for many people) but that didn't fix the problem for me.

I went to **System > Administration > Software Sources **and the Community-maintained Open Source Software (universe) repository was not selected. I selected this along with the rest of them and changed the server to somewhere closer to my location.

That fixed it!

---

