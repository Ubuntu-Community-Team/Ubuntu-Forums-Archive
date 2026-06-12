---
title: "IBM 600X Boot"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by Frihet on 2005-03-20
I put 5.04 in an IBM 600X laptop.  In the end, everything seems to work just fine.  However during boot and shutdown, the process runs through 6 to 10 (did not count) beeps with messages to the screen that go by too quickly to read.  Perhaps PCMCIA, invalid card type, not sure.

The NIC is a Xircom cardbus unit.  It works fine.

Any thoughts on where to look for this?

Thanks!!

George

---

### Post by plauniai on 2005-03-21
I just installed Array 7 on IBM 600E and have the same symptoms.

The beeps come from multiple repetitions of the following lines:

Invalid card number
Usage: amixer <options> command

... followed by the --help entry for amixer

As a result, there is no working audio by default (at least "Play" in Sound preferences panel does not function).  

Haven't yet looked into it in detail, as this machine is kind of a "scratchpad" installation maturity test device only.  But this implies that there are tons of potential (although admittedly old) IBM 600 series laptops that do not work 100% with the Hoary release. 

Warty seemed to handle the IBM audio just fine.

Another minor glitch I get on the IBM (and also on EPIA M board - these are the two I've tested so far) is the following complaint at the beginning of the installation:

Trying to enable the framebuffer...

sed: unsupported command I 

(that is capital I as in India...)

---

### Post by Frihet on 2005-03-21
I tried again tonight.  Same deal.

Yes, Warty worked fine.

I'll wait until the final HHH release and see if this is fixed.

The 600X is old, but very nice with Linux.  Small, well made.

---

### Post by uglysmurf on 2005-04-11
Just wanted to chip in that I'm having the same problem on my 600E...no idea how to stop it, even if I didn't want sound...

ubuntu 5.04 will be my first stab at linux full time...and my first post on a linux forum...greetings to anyone that comes across this!

---

